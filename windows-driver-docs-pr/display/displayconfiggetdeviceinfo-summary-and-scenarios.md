---
title: DisplayConfigGetDeviceInfo 摘要和方案
description: DisplayConfigGetDeviceInfo 摘要和方案
ms.assetid: 19d9a77c-252e-4623-b4bc-f0b990ed31e2
keywords:
- 连接显示 WDK Windows 7 显示 DisplayConfigGetDeviceInfo 在 CCD Api
- 连接显示 WDK Windows Server 2008 R2 显示 DisplayConfigGetDeviceInfo 在 CCD Api
- 配置显示 WDK Windows 7 显示 DisplayConfigGetDeviceInfo 在 CCD Api
- 配置显示 WDK Windows Server 2008 R2 显示 DisplayConfigGetDeviceInfo 在 CCD Api
- CCD 概念 WDK Windows 7 显示 DisplayConfigGetDeviceInfo
- CCD 概念 WDK Windows Server 2008 R2 显示 DisplayConfigGetDeviceInfo
- DisplayConfigGetDeviceInfo WDK Windows 7 显示
- DisplayConfigGetDeviceInfo WDK Windows Server 2008 R2 display
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: 76e7ad0bd73f4d7c1948a84651c03a07315a4b63
ms.sourcegitcommit: fb7d95c7a5d47860918cd3602efdd33b69dcf2da
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/25/2019
ms.locfileid: "67365738"
---
# <a name="displayconfiggetdeviceinfo-summary-and-scenarios"></a>DisplayConfigGetDeviceInfo 摘要和方案


本部分仅适用于 Windows 7 及更高版本、 和 Windows Server 2008 R2 和更高版本的 Windows 操作系统。

以下部分汇总了如何使用调用方[ **DisplayConfigGetDeviceInfo** ](https://docs.microsoft.com/windows/desktop/api/winuser/nf-winuser-displayconfiggetdeviceinfo) CCD 函数，并提供了有关使用方案**DisplayConfigGetDeviceInfo**。

### <a name="span-iddisplayconfiggetdeviceinfosummaryspanspan-iddisplayconfiggetdeviceinfosummaryspandisplayconfiggetdeviceinfo-summary"></a><span id="displayconfiggetdeviceinfo_summary"></span><span id="DISPLAYCONFIGGETDEVICEINFO_SUMMARY"></span>DisplayConfigGetDeviceInfo Summary

可以使用调用方[ **DisplayConfigGetDeviceInfo** ](https://docs.microsoft.com/windows/desktop/api/winuser/nf-winuser-displayconfiggetdeviceinfo)以获取更多的友好名称，以便在用户界面中显示。 调用方可以获取有关适配器、 源和目标的名称。 此外可以使用调用方**DisplayConfigGetDeviceInfo**以获取连接的显示设备的本机分辨率。

### <a name="span-iddisplayconfiggetdeviceinfoscenariosspanspan-iddisplayconfiggetdeviceinfoscenariosspandisplayconfiggetdeviceinfo-scenarios"></a><span id="displayconfiggetdeviceinfo_scenarios"></span><span id="DISPLAYCONFIGGETDEVICEINFO_SCENARIOS"></span>DisplayConfigGetDeviceInfo Scenarios

[**DisplayConfigGetDeviceInfo** ](https://docs.microsoft.com/windows/desktop/api/winuser/nf-winuser-displayconfiggetdeviceinfo)在以下情况下调用：

-   显示控件面板小程序调用[ **DisplayConfigGetDeviceInfo** ](https://docs.microsoft.com/windows/desktop/api/winuser/nf-winuser-displayconfiggetdeviceinfo)以获取要显示在下拉列表菜单，其中列出了所有已连接的监视器的监视器名称。

-   显示控件面板小程序调用[ **DisplayConfigGetDeviceInfo** ](https://docs.microsoft.com/windows/desktop/api/winuser/nf-winuser-displayconfiggetdeviceinfo)获取连接到系统的适配器的名称。

-   显示控件面板小程序调用[ **DisplayConfigGetDeviceInfo** ](https://docs.microsoft.com/windows/desktop/api/winuser/nf-winuser-displayconfiggetdeviceinfo)以获取每个连接监视器的分辨率，以便可以在用户界面中突出显示分辨率。

 

 





