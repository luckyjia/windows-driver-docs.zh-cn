---
title: 访问控制
description: 访问控制
ms.assetid: 7f87276f-4014-4b37-b051-4bf02acbf575
keywords:
- 安全 WDK 文件系统，最大限度地减少威胁
- access control WDK 文件系统
- access 验证 WDK 文件系统
- 验证安全 WDK 文件系统
- 检查安全性
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: 196c68ef022781b1e2d2e935765b2e8715e9480e
ms.sourcegitcommit: 4b7a6ac7c68e6ad6f27da5d1dc4deabd5d34b748
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2019
ms.locfileid: "72841511"
---
# <a name="access-control"></a>访问控制


## <span id="ddk_access_control_if"></span><span id="DDK_ACCESS_CONTROL_IF"></span>


为了防止对自身进行不当访问，大多数驱动程序依赖于 i/o 管理器针对其设备对象应用的默认访问控制。 驱动程序可以使用其他机制。 通常，最简单的驱动程序是在安装其驱动程序时应用显式安全描述符。 后面的部分将介绍将安全描述符应用到设备对象的示例。

实现其自己的安全策略的驱动程序可以依赖标准 Windows Api 来帮助管理安全访问。 在这种情况下，驱动程序将管理安全描述符的存储，并负责调用安全引用监视器例程来验证安全性。 其中包括多个例程，如下所示：

-   [**SeAccessCheck**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/nf-wdm-seaccesscheck)-此例程比较安全描述符和调用方的安全凭据。

-   [**SePrivilegeCheck**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntifs/nf-ntifs-seprivilegecheck)--此例程确定是否为调用方启用了给定的权限。

-   [**SeSinglePrivilegeCheck**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntddk/nf-ntddk-sesingleprivilegecheck)--此例程确定是否为调用方启用了特定权限。

-   [**SeAuditingFileOrGlobalEvents**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntifs/nf-ntifs-seauditingfileorglobalevents)--此例程指示系统是否已启用审核。

-   [**SeOpenObjectAuditAlarm**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntifs/nf-ntifs-seopenobjectauditalarm)--此例程审核打开对象事件。

此列表不完整，但它描述了许多可在驱动程序中用来执行访问验证的关键功能。

 

 




