---
title: 安装、升级和删除组件
description: 安装、升级和删除组件
ms.assetid: 7069e7a0-0c7e-4f7c-a764-a83e758df1bf
keywords:
- 通知对象 WDK 网络，删除网络组件
- 网络通知对象 WDK，删除网络组件
- 通知对象 WDK 网络、 升级网络组件
- 网络通知对象 WDK、 升级网络组件
- 通知对象 WDK 网络，安装网络组件
- 网络通知对象 WDK，安装网络组件
- 删除网络组件
- 升级网络组件 WDK，通知对象
- 安装 WDK 的网络组件，通知对象
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: 9445db497145a433edece7795ab5cbc22d2383f7
ms.sourcegitcommit: fb7d95c7a5d47860918cd3602efdd33b69dcf2da
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/25/2019
ms.locfileid: "67381217"
---
# <a name="installing-upgrading-and-removing-the-component"></a>安装、升级和删除组件





网络配置子系统安装时，升级或删除网络组件，请在子系统还调用组件的通知对象才能完成安装、 升级，并删除。 组件的通知对象可以实现执行组件可能需要进行的操作。 例如：

-   可以实现多路复用器的虚拟 LAN 的通知对象，以便通知对象时子系统安装多路复用器，将安装的多路复用器协议将绑定到的虚拟适配器。

    若要安装的虚拟适配器，通知对象将调用网络配置[ **INetCfgClassSetup::Install** ](https://docs.microsoft.com/previous-versions/windows/hardware/network/ff547711(v=vs.85))方法。 在此调用中，通知对象将传递要安装的虚拟适配器的标识符。 通知对象可以调用**INetCfgClassSetup::Install**，例如，从其[ **INetCfgComponentNotifyBinding::NotifyBindingPath** ](https://docs.microsoft.com/previous-versions/windows/hardware/network/ff547731(v=vs.85))或[**INetCfgComponentPropertyUi::ApplyProperties** ](https://docs.microsoft.com/previous-versions/windows/hardware/network/ff547741(v=vs.85))方法。

    若要完成虚拟适配器的安装，操作系统为虚拟适配器需要 INF 文件。 若要确保可以查找的此 INF 文件，它必须复制到操作系统时安装 multipexer。 有关详细信息，请参阅[复制 Inf](https://docs.microsoft.com/windows-hardware/drivers/install/copying-inf-files)。 本主题指明**CopyINF**指令或调用**SetupCopyOEMInf**共同安装程序或安装应用程序的函数可用于 INF 文件复制到目标系统的 INF 目录。 但是，如果 INF 文件进行多路复用器 (原始 INF) 使用复制**SetupCopyOEMInf**，则还必须使用复制的虚拟适配器的 INF 文件**SetupCopyOEMInf**因为的操作系统系统只处理**CopyINF**指令如果 INF 目录中尚不存在原始 INF。

-   可以实现多路复用器通知对象，以便通知对象时子系统中删除多路复用器，将删除所有虚拟适配器。 若要删除的虚拟适配器，通知对象将调用网络配置[ **INetCfgClassSetup::DeInstall** ](https://docs.microsoft.com/previous-versions/windows/hardware/network/ff547710(v=vs.85))方法。 在此调用，通知对象将传递指向**INetCfgComponent**虚拟适配器的接口。 通知对象可以调用**INetCfgClassSetup::DeInstall**，例如，从其**INetCfgComponentNotifyBinding::NotifyBindingPath**或**INetCfgComponentPropertyUi::ApplyProperties**方法。

-   可以实现组件的通知对象，以便通知对象在子系统升级该组件，将更改组件的绑定路径的顺序。 若要更改此顺序，通知对象的[ **INetCfgComponentSetup::Upgrade** ](https://docs.microsoft.com/previous-versions/windows/hardware/network/ff547783(v=vs.85))方法调用任一[ **INetCfgComponentBindings::MoveBefore**](https://docs.microsoft.com/previous-versions/windows/hardware/network/ff547722(v=vs.85))或[ **INetCfgComponentBindings::MoveAfter** ](https://docs.microsoft.com/previous-versions/windows/hardware/network/ff547721(v=vs.85))方法。

 

 





