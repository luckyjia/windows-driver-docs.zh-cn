---
title: VGA 兼容的微型端口驱动程序的 HwVidFindAdapter
description: VGA 兼容的微型端口驱动程序的 HwVidFindAdapter
ms.assetid: 4538e95f-e84d-434c-a674-e1d1d4e9e5a0
keywords:
- 视频微型端口驱动程序 WDK Windows 2000、VGA、HwVidFindAdapter
- VGA WDK 视频微型端口，HwVidFindAdapter
- HwVidFindAdapter
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: 91ea087d4bb9e30b68a5e0f7bf599a56ba7b94f1
ms.sourcegitcommit: 4b7a6ac7c68e6ad6f27da5d1dc4deabd5d34b748
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2019
ms.locfileid: "72829199"
---
# <a name="vga-compatible-miniport-drivers-hwvidfindadapter"></a>VGA 兼容的微型端口驱动程序的 HwVidFindAdapter


## <span id="ddk_vga_compatible_miniport_driver_s_hwvidfindadapter_gg"></span><span id="DDK_VGA_COMPATIBLE_MINIPORT_DRIVER_S_HWVIDFINDADAPTER_GG"></span>


与 VGA 兼容的微型端口驱动程序的[*HwVidFindAdapter*](https://docs.microsoft.com/windows-hardware/drivers/ddi/video/nc-video-pvideo_hw_find_adapter)函数（或注册表*HwVid。回呼*）必须在[**视频\_端口\_CONFIG\_信息**](https://docs.microsoft.com/windows-hardware/drivers/ddi/video/ns-video-_video_port_config_info)缓冲区中设置以下内容：

-   **NumEmulatorAccessEntries**，指示**EmulatorAccessEntries**数组中的条目数

-   **EmulatorAccessEntries**，指向包含给定数目的[**仿真器\_访问\_入口**](https://docs.microsoft.com/windows-hardware/drivers/ddi/miniport/ns-miniport-_emulator_access_entry)类型元素的静态数组，其中每个元素都描述了从 V86 模拟器挂钩的一系列 i/o 端口，并且默认情况下，转发到*SvgaHwIoPortXxx*函数

    每个条目都包含一个起始 i/o 地址、一个范围长度、要捕获的访问大小（UCHAR、USHORT 或 ULONG）、微型端口驱动程序是否支持通过 i/o 端口输入或输出字符串数据，以及微型端口驱动程序提供的*SvgaHwIoPortXxx*实际验证和传输数据的函数。 每个*SvgaHwIoPortXxx*函数处理读取（**传入**或表示**INSB/INSW/INSD**）和/或写入（**OUT**或**rep OUTSB/OUTSW/outsb**）对 UCHAR、USHORT 或 ULONG 大小的数据的传输。

-   **EmulatorAccessEntriesContext**，指向存储的指针（如微型端口驱动程序的设备扩展中的一个区域），其中微型端口驱动程序的*SvgaHwIoPortXxx*函数可以对所需的应用程序发出的指令序列进行批处理检查

-   **VdmPhysicalVideoMemoryAddress**和**VdmPhysicalVideoMemoryLength**，描述必须映射到*VDM*地址空间的视频内存范围，以支持全屏 MS-DOS 应用程序的 BIOS INT10 调用

    当这样的应用程序将视频模式更改为微型端口驱动程序的适配器可支持的模式时，微型端口驱动程序可以调用[**VideoPortInt10**](https://docs.microsoft.com/windows-hardware/drivers/ddi/video/nf-video-videoportint10)函数。

-   **HardwareStateSize**，描述存储适配器的硬件状态以响应 IOCTL\_视频所需的最小字节数\_保存\_硬件\_状态请求

    当用户将全屏 MS-DOS 应用程序切换为在窗口中运行时，微型端口驱动程序必须先保存适配器状态，然后再重新获得视频适配器的控制权。 请注意，与 VGA 兼容的微型端口驱动程序也必须支持反向 IOCTL\_视频\_RESTORE\_硬件\_状态请求，因为用户可能会将窗口应用程序切换回全屏模式。

与 VGA 兼容的微型端口驱动程序的模拟器访问条目指定适配器的访问范围数组的子集。 模拟器访问条目可以为，并且通常是映射访问范围数组中由其[*HwVidFindAdapter*](https://docs.microsoft.com/windows-hardware/drivers/ddi/video/nc-video-pvideo_hw_find_adapter)函数设置的所有 i/o 端口。 它在对[**VideoPortSetTrappedEmulatorPorts**](https://docs.microsoft.com/windows-hardware/drivers/ddi/video/nf-video-videoportsettrappedemulatorports)的调用中传递的访问范围，定义当前 IOPM 并确定可由全屏 MS-DOS 应用程序直接访问的 i/o 端口，指定微型端口驱动程序的模拟器的子集访问项。

 

 





