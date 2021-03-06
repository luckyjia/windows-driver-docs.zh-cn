---
title: 驱动程序签名工具
description: 驱动程序签名工具
ms.assetid: 2654388d-b39e-4009-bcba-56b318fd5119
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: d8130dc90539e05078cc175ff267bd36300c95c6
ms.sourcegitcommit: fb7d95c7a5d47860918cd3602efdd33b69dcf2da
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/25/2019
ms.locfileid: "67360918"
---
# <a name="tools-for-signing-drivers"></a>驱动程序签名工具


Microsoft Windows Driver Kit (WDK) 包括了以下工具，可用于创建代码签名证书进行签名[编录文件](https://docs.microsoft.com/windows-hardware/drivers/install/catalog-files)的[驱动程序包](https://docs.microsoft.com/windows-hardware/drivers/install/driver-packages)，并将嵌入中的签名驱动程序文件：

[**CertMgr**](certmgr.md)

[**Inf2Cat**](inf2cat.md)

[**MakeCat**](makecat.md)

[**MakeCert**](makecert.md)

[**Pvk2Pfx**](pvk2pfx.md)

[**SignTool**](signtool.md)

这些工具位于以下目录：

-   Inf2Cat 工具位于 %windowssdkdir%\\bin\\x86 目录。

-   其他工具位于用于 32 位 Windows 平台目录 (%windowssdkdir%\\bin\\x86) 和 64 位 Windows 平台 (%windowssdkdir%\\bin\\x64)。

**请注意**  Visual Studio 环境变量，%windowssdkdir%，表示 Windows 工具包 WDK 的此版本的安装的目录，例如，c: 路径\\Program Files (x86)\\Windows 工具包\\10。

 

Microsoft Windows SDK 包括有关服务、 组件和工具，您可以向应用程序添加加密安全信息。 这包括[ **CertMgr**](certmgr.md)， [ **MakeCert**](makecert.md)，并[ **SignTool** ](signtool.md)工具。

有关签名的驱动程序的详细信息和[驱动程序包](https://docs.microsoft.com/windows-hardware/drivers/install/driver-packages)，请参阅[驱动程序签名](https://docs.microsoft.com/windows-hardware/drivers/install/driver-signing)。

有关测试签名的驱动程序的信息包，请参阅[签名驱动程序开发和测试期间](https://docs.microsoft.com/windows-hardware/drivers/install/signing-drivers-during-development-and-test)。

 

 





