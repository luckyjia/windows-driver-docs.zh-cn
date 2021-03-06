---
title: 提供所需的电池微型类驱动程序功能
description: 提供所需的电池微型类驱动程序功能
ms.assetid: d33d3c8c-f867-40dc-901c-6b0dd5d57dac
keywords:
- 电池 miniclass 驱动程序 WDK，例程
- 例程 WDK 电池
- 电池 miniclass 驱动程序 WDK，功能
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: dfb9b8412006ea94828fc5a034a805eeeaf258a4
ms.sourcegitcommit: 4b7a6ac7c68e6ad6f27da5d1dc4deabd5d34b748
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2019
ms.locfileid: "72832217"
---
# <a name="supplying-required-battery-miniclass-driver-functionality"></a>提供所需的电池微型类驱动程序功能


## <span id="ddk_supplying_required_battery_miniclass_driver_functionality_dg"></span><span id="DDK_SUPPLYING_REQUIRED_BATTERY_MINICLASS_DRIVER_FUNCTIONALITY_DG"></span>


除了支持[即插即用](https://docs.microsoft.com/windows-hardware/drivers/kernel/implementing-plug-and-play)所需的例程以外，电池 miniclass 驱动程序必须具有以下例程：

[DriverEntry](driverentry-routine-of-a-battery-miniclass-driver.md)

[AddDevice](adddevice-routine-of-a-battery-miniclass-driver.md)

[DispatchDeviceControl](dispatchdevicecontrol-routine-of-a-battery-miniclass-driver.md)

[DispatchSystemControl](dispatchsystemcontrol-routine-of-a-battery-miniclass-driver.md)

[*BatteryMiniQueryTag*](https://docs.microsoft.com/windows/desktop/api/batclass/nc-batclass-bclass_query_tag_callback)

[*BatteryMiniQueryStatus*](https://docs.microsoft.com/windows/desktop/api/batclass/nc-batclass-bclass_query_status_callback)

[*BatteryMiniQueryInformation*](https://docs.microsoft.com/windows/desktop/api/batclass/nc-batclass-bclass_query_information_callback)

[*BatteryMiniSetInformation*](https://docs.microsoft.com/windows/desktop/api/batclass/nc-batclass-bclass_set_information_callback)

[*BatteryMiniSetStatusNotify*](https://docs.microsoft.com/windows/desktop/api/batclass/nc-batclass-bclass_set_status_notify_callback)

[*BatteryMiniDisableStatusNotify*](https://docs.microsoft.com/windows/desktop/api/batclass/nc-batclass-bclass_disable_status_notify_callback)

[](unload-routine-of-a-battery-miniclass-driver.md)

[DriverEntry](driverentry-routine-of-a-battery-miniclass-driver.md)、 [Unload](unload-routine-of-a-battery-miniclass-driver.md)、 [DispatchDeviceControl](dispatchdevicecontrol-routine-of-a-battery-miniclass-driver.md)和[AddDevice](adddevice-routine-of-a-battery-miniclass-driver.md)是标准的驱动程序例程。 需要名称 DriverEntry，以便操作系统可以在启动驱动程序时调用它。 您可以自行选择其他驱动程序例程的名称，前提是在相应的数据结构中正确加载了其地址。

[BatteryMini*Xxx* ](https://docs.microsoft.com/windows-hardware/drivers/ddi/_battery/)例程由 miniclass 驱动程序提供，由电池类驱动程序调用。 编写 miniclass 驱动程序时，可以选择不实现任何这些例程的功能;但是，仍必须提供例程的入口点，并且例程必须返回状态\_不\_支持。 这些例程的原型出现在 Batclass 中。

电池 miniclass 驱动程序必须包含以下头文件：

-   Batclass

-   Ntddk 或 Wdm

 

 




