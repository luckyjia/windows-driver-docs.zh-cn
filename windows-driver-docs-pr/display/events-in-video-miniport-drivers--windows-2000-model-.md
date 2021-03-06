---
title: 视频微型端口驱动程序中的事件（Windows 2000 模型）
description: 视频微型端口驱动程序中的事件（Windows 2000 模型）
ms.assetid: f6b5ded8-ddb4-4242-9bd3-b12dc96d8f6b
keywords:
- 视频微型端口驱动程序 WDK Windows 2000，事件
- 事件 WDK 视频微型端口
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: 52c97f8035e4987a249c082ca02212a4de255ffd
ms.sourcegitcommit: 4b7a6ac7c68e6ad6f27da5d1dc4deabd5d34b748
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2019
ms.locfileid: "72839700"
---
# <a name="events-in-video-miniport-drivers-windows-2000-model"></a>视频微型端口驱动程序中的事件（Windows 2000 模型）


## <span id="ddk_events_in_video_miniport_drivers_windows_2000_model__gg"></span><span id="DDK_EVENTS_IN_VIDEO_MINIPORT_DRIVERS_WINDOWS_2000_MODEL__GG"></span>


视频端口驱动程序提供对事件的支持，这是一种可用于同步在调度\_级别下运行的两个线程的[内核调度程序对象](https://docs.microsoft.com/windows-hardware/drivers/kernel/kernel-dispatcher-objects)。 视频微型端口驱动程序可以使用事件来同步对视频硬件的访问：

-   由视频微型端口驱动程序和显示驱动程序

-   由显示或视频微型端口驱动程序和其他组件（如 OpenGL 驱动程序或程序扩展（如 "控制面板" 中的 "显示程序"）。

下表列出了视频端口驱动程序提供的与事件相关的函数。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">函数</th>
<th align="left">描述</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><a href="https://docs.microsoft.com/windows-hardware/drivers/ddi/video/nf-video-videoportclearevent" data-raw-source="[&lt;strong&gt;VideoPortClearEvent&lt;/strong&gt;](https://docs.microsoft.com/windows-hardware/drivers/ddi/video/nf-video-videoportclearevent)"><strong>VideoPortClearEvent</strong></a></p></td>
<td align="left"><p>将给定的事件对象设置为非终止状态。</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="https://docs.microsoft.com/windows-hardware/drivers/ddi/video/nf-video-videoportcreateevent" data-raw-source="[&lt;strong&gt;VideoPortCreateEvent&lt;/strong&gt;](https://docs.microsoft.com/windows-hardware/drivers/ddi/video/nf-video-videoportcreateevent)"><strong>VideoPortCreateEvent</strong></a></p></td>
<td align="left"><p>创建事件对象。</p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="https://docs.microsoft.com/windows-hardware/drivers/ddi/video/nf-video-videoportdeleteevent" data-raw-source="[&lt;strong&gt;VideoPortDeleteEvent&lt;/strong&gt;](https://docs.microsoft.com/windows-hardware/drivers/ddi/video/nf-video-videoportdeleteevent)"><strong>VideoPortDeleteEvent</strong></a></p></td>
<td align="left"><p>删除指定的事件对象。</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="https://docs.microsoft.com/windows-hardware/drivers/ddi/video/nf-video-videoportreadstateevent" data-raw-source="[&lt;strong&gt;VideoPortReadStateEvent&lt;/strong&gt;](https://docs.microsoft.com/windows-hardware/drivers/ddi/video/nf-video-videoportreadstateevent)"><strong>VideoPortReadStateEvent</strong></a></p></td>
<td align="left"><p>返回给定事件对象的当前状态： "已终止" 或 "非终止"。</p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="https://docs.microsoft.com/windows-hardware/drivers/ddi/video/nf-video-videoportsetevent" data-raw-source="[&lt;strong&gt;VideoPortSetEvent&lt;/strong&gt;](https://docs.microsoft.com/windows-hardware/drivers/ddi/video/nf-video-videoportsetevent)"><strong>VideoPortSetEvent</strong></a></p></td>
<td align="left"><p>如果事件对象尚未处于该状态，则将其设置为 "已终止" 状态，并返回事件对象先前的状态。</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="https://docs.microsoft.com/windows-hardware/drivers/ddi/video/nf-video-videoportwaitforsingleobject" data-raw-source="[&lt;strong&gt;VideoPortWaitForSingleObject&lt;/strong&gt;](https://docs.microsoft.com/windows-hardware/drivers/ddi/video/nf-video-videoportwaitforsingleobject)"><strong>VideoPortWaitForSingleObject</strong></a></p></td>
<td align="left"><p>将当前线程置于等待状态，直到将给定调度对象设置为终止状态，或（可选），直到等待超时。</p></td>
</tr>
</tbody>
</table>

 

GDI 还为显示驱动程序的事件提供支持。 有关详细信息，请参阅[在显示驱动程序中使用事件](using-events-in-display-drivers.md)。

有关事件的更多详细情况，请参阅*内核模式驱动程序设计指南*中的[事件对象](https://docs.microsoft.com/windows-hardware/drivers/kernel/event-objects)。

 

 





