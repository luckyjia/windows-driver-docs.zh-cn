---
title: OID_GEN_DIRECTED_FRAMES_XMIT
description: 作为查询，OID_GEN_DIRECTED_FRAMES_XMIT OID 指定传输的未出现错误的定向数据包的数量。
ms.assetid: 7863c5c5-618f-4e3c-9a50-3bfdcf00034d
ms.date: 11/01/2019
keywords: -从 Windows Vista 开始 OID_GEN_DIRECTED_FRAMES_XMIT 网络驱动程序
ms.localizationpriority: medium
ms.openlocfilehash: 372c7fde80d3351bf3f612efc0a30dde1b719190
ms.sourcegitcommit: b8876f616ac625bb3f38218a32b2dc35ac7b3399
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/02/2019
ms.locfileid: "73442987"
---
# <a name="oid_gen_directed_frames_xmit"></a>OID\_代\_定向\_帧\_XMIT


作为查询，OID\_代\_定向\_帧\_XMIT OID 指定传输的未出现错误的定向数据包的数量。

**版本信息**

<a href="" id="windows-vista-and-later-versions-of-windows"></a>Windows Vista 和更高版本的 Windows  
已过时。

<a href="" id="ndis-6-0-and-later-drivers"></a>NDIS 6.0 和更高版本驱动程序  
未请求。 改用[OID\_代\_统计信息](oid-gen-statistics.md)。

<a href="" id="ndis-5-1-drivers"></a>NDIS 5.1 驱动程序  
可选。

<a href="" id="windows-xp"></a>Windows XP  
支持。

<a href="" id="ndis-5-1-drivers"></a>NDIS 5.1 驱动程序  
可选。

<a name="remarks"></a>备注
-------

计数与 RFC 2863 中所述的*ifOutUcastPkts*计数器完全相同。

有关统计信息 Oid 的一般信息，请参阅[常规统计](https://docs.microsoft.com/windows-hardware/drivers/network/ndis-general-statistics-oids)信息。

<a name="requirements"></a>要求
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>标头</p></td>
<td>Ntddndis （包括 Ndis .h）</td>
</tr>
</tbody>
</table>

## <a name="see-also"></a>另请参阅


[OID\_代\_统计信息](oid-gen-statistics.md)

 

 




