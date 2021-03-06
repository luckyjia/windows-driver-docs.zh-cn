---
title: IWiaMiniDrv COM 接口
ms.assetid: a4bd0dee-fb40-42d4-a235-9dab3bc84017
description: 本主题提供有关使用 IWiaMiniDrv COM 接口的详细指导
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: ffb62890d59f1650b51a7be457cb4083bfd0b218
ms.sourcegitcommit: 4b7a6ac7c68e6ad6f27da5d1dc4deabd5d34b748
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2019
ms.locfileid: "72840797"
---
# <a name="iwiaminidrv-com-interface"></a>IWiaMiniDrv COM 接口

图像处理应用程序向 WIA 服务发出请求，该服务又通过微型驱动程序编写器实现的[IWiaMiniDrv 接口](https://docs.microsoft.com/windows-hardware/drivers/ddi/wiamindr_lh/nn-wiamindr_lh-iwiaminidrv)与设备微型驱动程序通信。 应用程序通常会发出以下请求：

- [创建和初始化项](#creating-and-initializing-items)
- [删除项](#deleting-items)
- [枚举设备功能](#enumerating-device-capabilities)
- [枚举图像格式](#enumerating-image-formats)
- [发出设备命令](#issuing-device-commands)
- [锁定和解锁设备](#locking-and-unlocking-a-device)
- [向设备通知事件](#notifying-a-device-of-an-event)
- [获取设备错误字符串](#obtaining-device-error-strings)
- [读取和存储项属性](#reading-and-storing-item-properties)
- [传输数据](#transferring-data)

应用程序通过 WIA 应用程序编程接口（API）向 WIA 服务发出请求。 有关此接口的详细信息，请参阅 Microsoft Windows SDK 文档。

**IWiaMiniDrv**接口提供了下表中显示的用于控制设备的 WIA 服务的入口点。 WIA 微型驱动程序必须实现每个**IWiaMiniDrv**方法。 这些入口点是通过以下**IWiaMiniDrv**方法定义的。

## <a name="creating-and-initializing-items"></a>创建和初始化项

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>方法</th>
<th>描述</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="https://docs.microsoft.com/windows-hardware/drivers/ddi/wiamindr_lh/nf-wiamindr_lh-iwiaminidrv-drvanalyzeitem" data-raw-source="[&lt;strong&gt;IWiaMiniDrv::drvAnalyzeItem&lt;/strong&gt;](https://docs.microsoft.com/windows-hardware/drivers/ddi/wiamindr_lh/nf-wiamindr_lh-iwiaminidrv-drvanalyzeitem)"><strong>IWiaMiniDrv：:d rvAnalyzeItem</strong></a></p></td>
<td><p>检查项，并根据需要创建子项。</p></td>
</tr>
<tr class="even">
<td><p><a href="https://docs.microsoft.com/windows-hardware/drivers/ddi/wiamindr_lh/nf-wiamindr_lh-iwiaminidrv-drvinitializewia" data-raw-source="[&lt;strong&gt;IWiaMiniDrv::drvInitializeWia&lt;/strong&gt;](https://docs.microsoft.com/windows-hardware/drivers/ddi/wiamindr_lh/nf-wiamindr_lh-iwiaminidrv-drvinitializewia)"><strong>IWiaMiniDrv：:d rvInitializeWia</strong></a></p></td>
<td><p>初始化 WIA 微型驱动程序。</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://docs.microsoft.com/windows-hardware/drivers/ddi/wiamindr_lh/nf-wiamindr_lh-iwiaminidrv-drvinititemproperties" data-raw-source="[&lt;strong&gt;IWiaMiniDrv::drvInitItemProperties&lt;/strong&gt;](https://docs.microsoft.com/windows-hardware/drivers/ddi/wiamindr_lh/nf-wiamindr_lh-iwiaminidrv-drvinititemproperties)"><strong>IWiaMiniDrv：:d rvInitItemProperties</strong></a></p></td>
<td><p>为应用程序项树中的每个项初始化驱动程序项属性。</p></td>
</tr>
</tbody>
</table>

## <a name="deleting-items"></a>删除项

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>方法</th>
<th>描述</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="https://docs.microsoft.com/windows-hardware/drivers/ddi/wiamindr_lh/nf-wiamindr_lh-iwiaminidrv-drvdeleteitem" data-raw-source="[&lt;strong&gt;IWiaMiniDrv::drvDeleteItem&lt;/strong&gt;](https://docs.microsoft.com/windows-hardware/drivers/ddi/wiamindr_lh/nf-wiamindr_lh-iwiaminidrv-drvdeleteitem)"><strong>IWiaMiniDrv：:d rvDeleteItem</strong></a></p></td>
<td><p>删除驱动程序项。</p></td>
</tr>
<tr class="even">
<td><p><a href="https://docs.microsoft.com/windows-hardware/drivers/ddi/wiamindr_lh/nf-wiamindr_lh-iwiaminidrv-drvfreedrvitemcontext" data-raw-source="[&lt;strong&gt;IWiaMiniDrv::drvFreeDrvItemContext&lt;/strong&gt;](https://docs.microsoft.com/windows-hardware/drivers/ddi/wiamindr_lh/nf-wiamindr_lh-iwiaminidrv-drvfreedrvitemcontext)"><strong>IWiaMiniDrv：:d rvFreeDrvItemContext</strong></a></p></td>
<td><p>释放设备特定的上下文。</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://docs.microsoft.com/windows-hardware/drivers/ddi/wiamindr_lh/nf-wiamindr_lh-iwiaminidrv-drvuninitializewia" data-raw-source="[&lt;strong&gt;IWiaMiniDrv::drvUnInitializeWia&lt;/strong&gt;](https://docs.microsoft.com/windows-hardware/drivers/ddi/wiamindr_lh/nf-wiamindr_lh-iwiaminidrv-drvuninitializewia)"><strong>IWiaMiniDrv：:d rvUnInitializeWia</strong></a></p></td>
<td><p>释放与应用程序项树关联的设备资源。</p></td>
</tr>
</tbody>
</table>

## <a name="enumerating-device-capabilities"></a>枚举设备功能

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>方法</th>
<th>描述</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="https://docs.microsoft.com/windows-hardware/drivers/ddi/wiamindr_lh/nf-wiamindr_lh-iwiaminidrv-drvgetcapabilities" data-raw-source="[&lt;strong&gt;IWiaMiniDrv::drvGetCapabilities&lt;/strong&gt;](https://docs.microsoft.com/windows-hardware/drivers/ddi/wiamindr_lh/nf-wiamindr_lh-iwiaminidrv-drvgetcapabilities)"><strong>IWiaMiniDrv：:d rvGetCapabilities</strong></a></p></td>
<td><p>报告 WIA 微型驱动程序支持的事件和命令。</p></td>
</tr>
</tbody>
</table>

## <a name="enumerating-image-formats"></a>枚举图像格式

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>方法</th>
<th>描述</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="https://docs.microsoft.com/windows-hardware/drivers/ddi/wiamindr_lh/nf-wiamindr_lh-iwiaminidrv-drvgetwiaformatinfo" data-raw-source="[&lt;strong&gt;IWiaMiniDrv::drvGetWiaFormatInfo&lt;/strong&gt;](https://docs.microsoft.com/windows-hardware/drivers/ddi/wiamindr_lh/nf-wiamindr_lh-iwiaminidrv-drvgetwiaformatinfo)"><strong>IWiaMiniDrv：:d rvGetWiaFormatInfo</strong></a></p></td>
<td><p>获取支持的设备格式和媒体类型。</p></td>
</tr>
</tbody>
</table>

## <a name="issuing-device-commands"></a>发出设备命令

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>方法</th>
<th>描述</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="https://docs.microsoft.com/windows-hardware/drivers/ddi/wiamindr_lh/nf-wiamindr_lh-iwiaminidrv-drvdevicecommand" data-raw-source="[&lt;strong&gt;IWiaMiniDrv::drvDeviceCommand&lt;/strong&gt;](https://docs.microsoft.com/windows-hardware/drivers/ddi/wiamindr_lh/nf-wiamindr_lh-iwiaminidrv-drvdevicecommand)"><strong>IWiaMiniDrv：:d rvDeviceCommand</strong></a></p></td>
<td><p>向图像设备发出命令。</p></td>
</tr>
</tbody>
</table>

## <a name="locking-and-unlocking-a-device"></a>锁定和解锁设备

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>方法</th>
<th>描述</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="https://docs.microsoft.com/windows-hardware/drivers/ddi/wiamindr_lh/nf-wiamindr_lh-iwiaminidrv-drvlockwiadevice" data-raw-source="[&lt;strong&gt;IWiaMiniDrv::drvLockWiaDevice&lt;/strong&gt;](https://docs.microsoft.com/windows-hardware/drivers/ddi/wiamindr_lh/nf-wiamindr_lh-iwiaminidrv-drvlockwiadevice)"><strong>IWiaMiniDrv：:d rvLockWiaDevice</strong></a></p></td>
<td><p>锁定对图像处理设备的访问。</p></td>
</tr>
<tr class="even">
<td><p><a href="https://docs.microsoft.com/windows-hardware/drivers/ddi/wiamindr_lh/nf-wiamindr_lh-iwiaminidrv-drvunlockwiadevice" data-raw-source="[&lt;strong&gt;IWiaMiniDrv::drvUnLockWiaDevice&lt;/strong&gt;](https://docs.microsoft.com/windows-hardware/drivers/ddi/wiamindr_lh/nf-wiamindr_lh-iwiaminidrv-drvunlockwiadevice)"><strong>IWiaMiniDrv：:d rvUnLockWiaDevice</strong></a></p></td>
<td><p>取消锁定对图像设备的访问。</p></td>
</tr>
</tbody>
</table>

## <a name="notifying-a-device-of-an-event"></a>向设备通知事件

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>方法</th>
<th>描述</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="https://docs.microsoft.com/windows-hardware/drivers/ddi/wiamindr_lh/nf-wiamindr_lh-iwiaminidrv-drvnotifypnpevent" data-raw-source="[&lt;strong&gt;IWiaMiniDrv::drvNotifyPnPEvent&lt;/strong&gt;](https://docs.microsoft.com/windows-hardware/drivers/ddi/wiamindr_lh/nf-wiamindr_lh-iwiaminidrv-drvnotifypnpevent)"><strong>IWiaMiniDrv：:d rvNotifyPnPEvent</strong></a></p></td>
<td><p>指示 WIA 微型驱动程序对即插即用事件的响应。</p></td>
</tr>
</tbody>
</table>

## <a name="obtaining-device-error-strings"></a>获取设备错误字符串

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>方法</th>
<th>描述</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="https://docs.microsoft.com/windows-hardware/drivers/ddi/wiamindr_lh/nf-wiamindr_lh-iwiaminidrv-drvgetdeviceerrorstr" data-raw-source="[&lt;strong&gt;IWiaMiniDrv::drvGetDeviceErrorStr&lt;/strong&gt;](https://docs.microsoft.com/windows-hardware/drivers/ddi/wiamindr_lh/nf-wiamindr_lh-iwiaminidrv-drvgetdeviceerrorstr)"><strong>IWiaMiniDrv：:d rvGetDeviceErrorStr</strong></a></p></td>
<td><p>将设备错误值映射到字符串。</p></td>
</tr>
</tbody>
</table>

## <a name="reading-and-storing-item-properties"></a>读取和存储项属性

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>方法</th>
<th>描述</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="https://docs.microsoft.com/windows-hardware/drivers/ddi/wiamindr_lh/nf-wiamindr_lh-iwiaminidrv-drvreaditemproperties" data-raw-source="[&lt;strong&gt;IWiaMiniDrv::drvReadItemProperties&lt;/strong&gt;](https://docs.microsoft.com/windows-hardware/drivers/ddi/wiamindr_lh/nf-wiamindr_lh-iwiaminidrv-drvreaditemproperties)"><strong>IWiaMiniDrv：:d rvReadItemProperties</strong></a></p></td>
<td><p>读取驱动程序项属性。</p></td>
</tr>
<tr class="even">
<td><p><a href="https://docs.microsoft.com/windows-hardware/drivers/ddi/wiamindr_lh/nf-wiamindr_lh-iwiaminidrv-drvvalidateitemproperties" data-raw-source="[&lt;strong&gt;IWiaMiniDrv::drvValidateItemProperties&lt;/strong&gt;](https://docs.microsoft.com/windows-hardware/drivers/ddi/wiamindr_lh/nf-wiamindr_lh-iwiaminidrv-drvvalidateitemproperties)"><strong>IWiaMiniDrv：:d rvValidateItemProperties</strong></a></p></td>
<td><p>验证驱动程序项属性。</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://docs.microsoft.com/windows-hardware/drivers/ddi/wiamindr_lh/nf-wiamindr_lh-iwiaminidrv-drvwriteitemproperties" data-raw-source="[&lt;strong&gt;IWiaMiniDrv::drvWriteItemProperties&lt;/strong&gt;](https://docs.microsoft.com/windows-hardware/drivers/ddi/wiamindr_lh/nf-wiamindr_lh-iwiaminidrv-drvwriteitemproperties)"><strong>IWiaMiniDrv：:d rvWriteItemProperties</strong></a></p></td>
<td><p>将驱动程序项属性写入设备（如果需要）。</p></td>
</tr>
</tbody>
</table>

## <a name="transferring-data"></a>传输数据

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>方法</th>
<th>描述</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="https://docs.microsoft.com/windows-hardware/drivers/ddi/wiamindr_lh/nf-wiamindr_lh-iwiaminidrv-drvacquireitemdata" data-raw-source="[&lt;strong&gt;IWiaMiniDrv::drvAcquireItemData&lt;/strong&gt;](https://docs.microsoft.com/windows-hardware/drivers/ddi/wiamindr_lh/nf-wiamindr_lh-iwiaminidrv-drvacquireitemdata)"><strong>IWiaMiniDrv：:d rvAcquireItemData</strong></a></p></td>
<td><p>将数据从驱动程序项传输到 WIA 服务。</p></td>
</tr>
</tbody>
</table>
