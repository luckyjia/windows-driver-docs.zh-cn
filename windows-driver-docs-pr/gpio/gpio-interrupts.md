---
title: GPIO 中断
description: 某些常规用途 I/O (GPIO) 控制器设备可以配置其 GPIO 引脚，使之充当中断请求输入。
ms.assetid: 0F56AD4C-E0BF-49F1-AB67-0107D08DEF9F
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: 713eb6162dde55c265aacb868c0a7e11c2c3b97a
ms.sourcegitcommit: 4b7a6ac7c68e6ad6f27da5d1dc4deabd5d34b748
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2019
ms.locfileid: "72824969"
---
# <a name="gpio-interrupts"></a>GPIO 中断


某些常规用途 I/O (GPIO) 控制器设备可以配置其 GPIO 引脚，使之充当中断请求输入。 这些中断请求输入由通过物理方式连接到 GPIO 引脚的外围设备驱动。 这些 GPIO 控制器的驱动程序可以启用、禁用、屏蔽、取消屏蔽以及清除单个 GPIO 引脚上的中断请求。

支持 GPIO 中断是可选的。 GPIO framework 扩展（GpioClx）不需要 GPIO 控制器来支持 GPIO 中断。

## <a name="in-this-section"></a>本部分内容


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>主题</th>
<th>描述</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="https://docs.microsoft.com/windows-hardware/drivers/gpio/primary-and-secondary-interrupts" data-raw-source="[Primary and Secondary Interrupts](https://docs.microsoft.com/windows-hardware/drivers/gpio/primary-and-secondary-interrupts)">主要和次要中断</a></p></td>
<td><p>GPIO 中断处理本质上是一个两阶段过程。 用于使 GPIO framework 扩展（GpioClx）中断服务例程（ISR）运行的常规用途 i/o （GPIO）控制器的中断被称为<em>主中断</em>。 此 ISR 将中断的 GPIO pin 映射到全局系统中断（GSI），并将此 GSI 传递到硬件抽象层（HAL）。 HAL 通过此 GSI 生成一个<em>辅助中断</em>，以运行通过逻辑方式连接到 GPIO pin 的第二个 ISR。 此过程显示在<a href="https://docs.microsoft.com/windows-hardware/drivers/gpio/gpio-driver-support-overview#gpio-block-diagram" data-raw-source="[GPIO Driver Support Overview](https://docs.microsoft.com/windows-hardware/drivers/gpio/gpio-driver-support-overview#gpio-block-diagram)">GPIO 驱动程序支持概述</a>的关系图中。</p></td>
</tr>
<tr class="even">
<td><p><a href="https://docs.microsoft.com/windows-hardware/drivers/gpio/gpio-based-interrupt-resources" data-raw-source="[GPIO-Based Interrupt Resources](https://docs.microsoft.com/windows-hardware/drivers/gpio/gpio-based-interrupt-resources)">基于 GPIO 的中断资源</a></p></td>
<td><p>将中断发送到常规用途 i/o （GPIO） pin 的外围设备的驱动程序会将 GPIO 中断获取为抽象的 Windows 中断资源。 <a href="https://docs.microsoft.com/windows-hardware/drivers/wdf/what-s-new-for-wdf-drivers" data-raw-source="[Kernel-mode driver framework](https://docs.microsoft.com/windows-hardware/drivers/wdf/what-s-new-for-wdf-drivers)">内核模式驱动程序框架</a>（KMDF）驱动程序通过其<a href="https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfdevice/nc-wdfdevice-evt_wdf_device_prepare_hardware" data-raw-source="[&lt;em&gt;EvtDevicePrepareHardware&lt;/em&gt;](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfdevice/nc-wdfdevice-evt_wdf_device_prepare_hardware)"><em>EvtDevicePrepareHardware</em></a>事件回调函数接收这些资源。 </p></td>
</tr>
<tr class="odd">
<td><p><a href="https://docs.microsoft.com/windows-hardware/drivers/gpio/passive-level-isrs" data-raw-source="[Passive-Level ISRs](https://docs.microsoft.com/windows-hardware/drivers/gpio/passive-level-isrs)">被动级别 Isr</a></p></td>
<td><p>从 Windows 8 开始，可以选择内核模式驱动程序框架（KMDF）和用户模式驱动程序框架（UMDF）驱动程序，将其中断服务例程（Isr）注册到被动级别运行。</p></td>
</tr>
<tr class="even">
<td><p><a href="https://docs.microsoft.com/windows-hardware/drivers/gpio/interrupt-related-callbacks" data-raw-source="[Interrupt-Related Callbacks](https://docs.microsoft.com/windows-hardware/drivers/gpio/interrupt-related-callbacks)">与中断相关的回调</a></p></td>
<td><p>作为一个选项，常规用途 i/o （GPIO）控制器的驱动程序可以为 GPIO 中断提供支持。 为了支持 GPIO 中断，GPIO 控制器驱动程序实现了一组回调函数以管理这些中断。 驱动程序在注册数据包中包含指向这些回调函数的指针，驱动程序将自身注册为 GPIO framework 扩展（GpioClx）的客户端。</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://docs.microsoft.com/windows-hardware/drivers/gpio/interrupt-synchronization-for-gpio-controller-drivers" data-raw-source="[Interrupt Synchronization for GPIO Controller Drivers](https://docs.microsoft.com/windows-hardware/drivers/gpio/interrupt-synchronization-for-gpio-controller-drivers)">GPIO 控制器驱动程序的中断同步</a></p></td>
<td><p>GPIO 控制器驱动程序可以调用<a href="https://docs.microsoft.com/windows-hardware/drivers/ddi/gpioclx/nf-gpioclx-gpio_clx_acquireinterruptlock" data-raw-source="[&lt;strong&gt;GPIO_CLX_AcquireInterruptLock&lt;/strong&gt;](https://docs.microsoft.com/windows-hardware/drivers/ddi/gpioclx/nf-gpioclx-gpio_clx_acquireinterruptlock)"><strong>GPIO_CLX_AcquireInterruptLock</strong></a>和<a href="https://docs.microsoft.com/windows-hardware/drivers/ddi/gpioclx/nf-gpioclx-gpio_clx_releaseinterruptlock" data-raw-source="[&lt;strong&gt;GPIO_CLX_ReleaseInterruptLock&lt;/strong&gt;](https://docs.microsoft.com/windows-hardware/drivers/ddi/gpioclx/nf-gpioclx-gpio_clx_releaseinterruptlock)"><strong>GPIO_CLX_ReleaseInterruptLock</strong></a>方法来获取和释放由 GPIO framework 扩展（GpioClx）在内部实现的中断锁。 以 IRQL = PASSIVE_LEVEL 运行的驱动程序代码可以调用这些方法以同步到 GpioClx 中的中断服务例程（ISR）。 GpioClx 专用在 GPIO 控制器中的每个引脚插槽之间单独中断锁定。</p></td>
</tr>
<tr class="even">
<td><p><a href="https://docs.microsoft.com/windows-hardware/drivers/gpio/enabling-and-disabling-shared-gpio-interrupts" data-raw-source="[Enabling and Disabling Shared GPIO Interrupts](https://docs.microsoft.com/windows-hardware/drivers/gpio/enabling-and-disabling-shared-gpio-interrupts)">启用和禁用共享 GPIO 中断</a></p></td>
<td><p>在某些情况下，来自两个或多个外围设备的中断请求线路可能连接到相同的物理常规用途 i/o （GPIO） pin。 通常为共享中断线路配置用于共享中断线路的 GPIO pin。</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://docs.microsoft.com/windows-hardware/drivers/gpio/gpio-interrupt-masks" data-raw-source="[GPIO Interrupt Masks](https://docs.microsoft.com/windows-hardware/drivers/gpio/gpio-interrupt-masks)">GPIO 中断掩码</a></p></td>
<td><p>配置为中断输入的常规用途 i/o （GPIO） pin 除了启用和禁用外，还可屏蔽和取消屏蔽。</p></td>
</tr>
</tbody>
</table>

 

 

 




