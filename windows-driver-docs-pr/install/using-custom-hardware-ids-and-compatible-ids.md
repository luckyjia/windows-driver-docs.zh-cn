---
title: 使用自定义硬件 ID 和兼容 ID
description: 使用自定义硬件 ID 和兼容 ID
ms.assetid: 4f0ae082-b601-4322-add8-63941c2bdad3
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: 7fb25fe8bc5132877af5419a22d9fced8b579ad5
ms.sourcegitcommit: 1983d65315876b5b3783632f3a3395b287d15b86
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/23/2020
ms.locfileid: "85289473"
---
# <a name="using-custom-hardware-ids-and-compatible-ids"></a>使用自定义硬件 ID 和兼容 ID


如[设备标识字符串](device-identification-strings.md)中所述，以下是新的总线驱动程序应用于即插即用（PnP）硬件 id 和兼容 id 的通用格式。

```cpp
enumerator\enumerator-specific-device-ID 
```

其中：

-   *枚举器*标识在总线上检测和报告到 PnP 管理器的子设备的总线驱动程序。

-   *特定于枚举器的设备 ID*是特定于总线驱动程序的设备标识符。

如果与其他总线相比，总线的配置或操作明显不同，则总线的总线驱动程序应使用唯一的枚举器名称，以确保不会无意中将总线的子设备与其他总线的总线驱动程序所枚举的子设备进行不当分组。 总线驱动程序应使用以下格式向 PnP 管理器报告设备标识字符串：

```cpp
bus-type-guid\vendor-specific-id
```

其中：

-   *总线类型-guid*是标识总线的唯一 guid，并且应与用于标识总线的 guid 相同。 如[安装总线驱动程序](installing-a-new-bus-driver.md)中所述，总线驱动程序会标识设备的总线类型，以响应[**IRP_MN_QUERY_BUS_INFORMATION**](https://docs.microsoft.com/windows-hardware/drivers/kernel/irp-mn-query-bus-information)设备的请求。

-   供应商*特定 id*是供应商定义的格式，通常标识供应商、设备、子系统、修订号，以及可能的其他设备信息。 例如，格式可能采用*供应商* & *设备* & *子系统* & *修订版本*的形式，其中，与号字符（"&"）分隔子字段，每个子字段的格式是特定于供应商的。 有关实际设备标识字符串的示例，请参阅[设备标识字符串](device-identification-strings.md)。

PnP 管理器将[**IRP_MN_QUERY_ID**](https://docs.microsoft.com/windows-hardware/drivers/kernel/irp-mn-query-id)请求发送到总线驱动程序，以获取设备的设备标识字符串。 设备标识字符串包括设备 ID、设备实例 ID、硬件 Id 列表以及兼容 Id 列表。 以下虚构示例包括设备 ID、硬件 Id 列表以及兼容 Id 列表。 在这些示例中，枚举器由*总线类型 guid*子字段指定，后者是 guid "{xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx-zzzz-yyyyyyyyyyyy}"。 供应商*特定 id*字段的格式为*供应*商 & *设备* & *子系统* & *修订版*，其中*供应商*子字段为 "ven_1"，*设备*子字段为 "dev_2"，*子系统*子字段为 "subsys_3"，*修订*子字段为 "rev_4"。

设备 ID 是设备的最特定说明的硬件 ID。 在以下示例中，设备 ID 指定供应商、设备、子系统和修订版本。

```cpp
{xxxxxxxx-yyyy-zzzz-xxxx-yyyyyyyyyyyy}\ven_1&dev_2&subsys_3&rev_4 
```

硬件 ID 列表按从最特定到最不特定的顺序指定 Id。 在下面的列表中，如果设备标识字符串至少指定了供应商、设备和子系统，则会将其报告为硬件 ID。 首先列出了包含大多数信息的硬件 ID。

```cpp
{xxxxxxxx-yyyy-zzzz-xxxx-yyyyyyyyyyyy}\ven_1&dev_2&subsys_3&rev_4 
{xxxxxxxx-yyyy-zzzz-xxxx-yyyyyyyyyyyy}\ven_1&dev_2&subsys_3 
```

在下面的列表中，如果设备标识字符串至少指定了供应商和设备（位置1和2），但未指定子系统（位置3），则将其报告为兼容 ID。 首先列出了包含大多数信息的兼容 ID。

```cpp
{xxxxxxxx-yyyy-zzzz-xxxx-yyyyyyyyyyyy}\ven_1&dev_2&rev_4 
{xxxxxxxx-yyyy-zzzz-xxxx-yyyyyyyyyyyy}\ven_1&dev_2
```

如果使用硬件 ID 安装驱动程序，则它将表示匹配设备的完整功能。 如果使用兼容的 ID 安装驱动程序，则该驱动程序将至少表示用于匹配设备的基本功能。驱动程序可能使用兼容的 ID，以便通用驱动程序可在大量设备上运行。 例如，许多 Windows 系统提供的驱动程序都与兼容的 Id 匹配。 与硬件 ID 匹配的驱动程序通常针对一组小型设备，但提供完整功能。



