---
title: WIA\_IP\_XSCALING
description: WIA\_IP\_XSCALING 属性指示是否应使扫描应用沿 x 轴缩放。 WIA 微型驱动程序创建并维护此属性。
ms.assetid: 608ac942-4a37-4490-8715-a1e2ebc4dc64
keywords:
- WIA_IPS_XSCALING 成像设备
topic_type:
- apiref
api_name:
- WIA_IPS_XSCALING
api_location:
- Wiadef.h
api_type:
- HeaderDef
ms.date: 11/28/2017
ms.localizationpriority: medium
ms.openlocfilehash: 2eeb96b0fd3f4c9c429bcf216142db9da56d6cd4
ms.sourcegitcommit: 0cc5051945559a242d941a6f2799d161d8eba2a7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "63342001"
---
# <a name="wiaipsxscaling"></a>WIA\_IP\_XSCALING


WIA\_IP\_XSCALING 属性指示是否应使扫描应用沿 x 轴缩放。 WIA 微型驱动程序创建并维护此属性。

属性类型：VT\_I4

有效值：WIA\_PROP\_范围或 WIA\_PROP\_列表

访问权限：读/写或只读的

<a name="remarks"></a>备注
-------

有效值为 WIA\_IP\_XSCALING 属性介于 1 到 65535 之间。

WIA\_IP\_XSCALING 指示仅沿 x 轴缩放。 如果你想要能够统一缩放图像，则必须设置类似的值中 WIA\_IPS\_XSCALING 并在[ **WIA\_IP\_YSCALING** ](wia-ips-yscaling.md)属性。

请考虑以下示例：

-   100，无需进行扩展 (1 x 100%)。 图像不会更改。

-   050，1/2 的缩放 (1/2 x，50%)。 沿 x 轴的 50%减小映像大小 (1/2 原始大小)。

-   200，2 倍缩放 （200%)。 沿 x 轴放大图像大小是 200%(double)。

<a name="requirements"></a>要求
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Version</p></td>
<td><p>在 Windows Vista 和更高版本操作系统中可用。</p></td>
</tr>
<tr class="even">
<td><p>Header</p></td>
<td>Wiadef.h （包括 Wiadef.h）</td>
</tr>
</tbody>
</table>

## <a name="see-also"></a>请参阅


[**WIA\_IPS\_YSCALING**](wia-ips-yscaling.md)

 

 






