---
title: KSEVENT\_VIDCAPTOSTI\_EXT\_触发器
description: KSEVENT\_VIDCAPTOSTI\_EXT\_触发器事件传播一项操作，例如，在视频捕获设备上按下触发器按钮时，从内核模式视频捕获微型驱动程序到 DirectShow 中的用户模式。
ms.assetid: 97f67d22-20c4-460c-9022-04e55e74f6f9
keywords:
- KSEVENT_VIDCAPTOSTI_EXT_TRIGGER 流媒体设备
topic_type:
- apiref
api_name:
- KSEVENT_VIDCAPTOSTI_EXT_TRIGGER
api_type:
- NA
ms.date: 11/28/2017
ms.localizationpriority: medium
ms.openlocfilehash: d233530c7baa845dc5929e5bd99db384a37078c0
ms.sourcegitcommit: 4b7a6ac7c68e6ad6f27da5d1dc4deabd5d34b748
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2019
ms.locfileid: "72843670"
---
# <a name="ksevent_vidcaptosti_ext_trigger"></a>KSEVENT\_VIDCAPTOSTI\_EXT\_触发器


KSEVENT\_VIDCAPTOSTI\_EXT\_触发器事件传播一项操作，例如，在视频捕获设备上按下触发器按钮时，从内核模式视频捕获微型驱动程序到 DirectShow 中的用户模式。

## <span id="ddk_ksevent_vidcaptosti_ext_trigger_ks"></span><span id="DDK_KSEVENT_VIDCAPTOSTI_EXT_TRIGGER_KS"></span>


### <a name="span-idusage_summary_tablespanspan-idusage_summary_tablespanusage-summary-table"></a><span id="usage_summary_table"></span><span id="USAGE_SUMMARY_TABLE"></span>使用情况摘要表

<table>
<colgroup>
<col width="20%" />
<col width="20%" />
<col width="20%" />
<col width="20%" />
<col width="20%" />
</colgroup>
<thead>
<tr class="header">
<th>“获取”</th>
<th>设置</th>
<th>目标</th>
<th>事件描述符类型</th>
<th>事件值类型</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>无</p></td>
<td><p>“是”</p></td>
<td><p>大头针</p></td>
<td><p><a href="https://docs.microsoft.com/windows-hardware/drivers/ddi/ks/ns-ks-kse_node" data-raw-source="[&lt;strong&gt;KSE_NODE&lt;/strong&gt;](https://docs.microsoft.com/windows-hardware/drivers/ddi/ks/ns-ks-kse_node)"><strong>KSE_NODE</strong></a></p></td>
<td><p><a href="https://docs.microsoft.com/windows-hardware/drivers/ddi/ks/ns-ks-kseventdata" data-raw-source="[&lt;strong&gt;KSEVENTDATA&lt;/strong&gt;](https://docs.microsoft.com/windows-hardware/drivers/ddi/ks/ns-ks-kseventdata)"><strong>KSEVENTDATA</strong></a></p></td>
</tr>
</tbody>
</table>

 

有关 DirectShow 筛选器和 KsProxy 的详细信息，请参阅[内核流式处理代理](https://docs.microsoft.com/windows-hardware/drivers/ddi/_stream/index)。

 

 





