---
title: 禁用 OpenGL 互操作性
description: 禁用 OpenGL 互操作性
ms.assetid: 2b684cda-2137-4395-b2ee-beee8614e4c1
keywords:
- INF 文件 WDK 显示、 互操作性
- 互操作性 WDK 显示
- OpenGL WDK 显示
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: df93c9bd39b6f7d8ee413b9528ae7453ed4510c5
ms.sourcegitcommit: 0cc5051945559a242d941a6f2799d161d8eba2a7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "63393044"
---
# <a name="disabling-interoperability-with-opengl"></a>禁用 OpenGL 互操作性


若要确保没有 Microsoft Direct3D 显示器驱动程序将面临 OpenGL 可安装的客户端驱动程序 (ICDs) 的互操作性问题，必须 INF 添加注册表部分中设置以下条目：

```inf
[Xxx_SoftwareDeviceSettings]
...
HKR,, CapabilityOverride,    %REG_DWORD%, 0x8
```

 

 





