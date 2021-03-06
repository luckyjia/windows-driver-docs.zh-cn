---
title: OID_WDI_TASK_DELETE_PORT
description: OID_WDI_TASK_DELETE_PORT 请求 IHV 组件释放所有资源 （包括 MAC 和 PHY） 分配给指定的端口。
ms.assetid: c84b6cd6-a8e7-4ba7-a9d9-04b2881904c8
ms.date: 07/18/2017
keywords:
- 从 Windows Vista 开始 OID_WDI_TASK_DELETE_PORT 网络驱动程序
ms.localizationpriority: medium
ms.custom: 19H1
ms.openlocfilehash: d6c7e43f7fa897c4b9148e63c692e1d5fe318b17
ms.sourcegitcommit: fb7d95c7a5d47860918cd3602efdd33b69dcf2da
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/25/2019
ms.locfileid: "67387246"
---
# <a name="oidwditaskdeleteport"></a>OID\_WDI\_TASK\_DELETE\_PORT


OID\_WDI\_任务\_删除\_端口请求 IHV 组件释放所有资源 （包括 MAC 和 PHY） 分配给指定的端口。

| Object  | 中止支持 | 默认优先级 （主机驱动程序策略） | 正常执行时间 （秒） |
|---------|---------------|---------------------------------------|---------------------------------|
| 适配器 | 否            | 6                                     | 1                               |

 

## <a name="task-parameters"></a>任务参数


| TLV                                                                               | 允许多个 TLV 实例 | 可选 | 描述                 |
|-----------------------------------------------------------------------------------|--------------------------------|----------|-----------------------------|
| [**WDI\_TLV\_DELETE\_PORT\_PARAMETERS**](https://docs.microsoft.com/windows-hardware/drivers/network/wdi-tlv-delete-port-parameters) |                                |          | 删除端口参数。 |

 

## <a name="task-completion-indication"></a>指示任务完成


[NDIS\_状态\_WDI\_指示\_删除\_端口\_完成](ndis-status-wdi-indication-delete-port-complete.md)

<a name="requirements"></a>要求
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>最低受支持的客户端</p></td>
<td><p>Windows 10</p></td>
</tr>
<tr class="even">
<td><p>最低受支持的服务器</p></td>
<td><p>Windows Server 2016</p></td>
</tr>
<tr class="odd">
<td><p>Header</p></td>
<td>Dot11wdi.h</td>
</tr>
</tbody>
</table>

 

 




