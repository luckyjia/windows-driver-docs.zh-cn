---
title: KSPROPERTY\_BDA\_NODE\_类型
description: 客户端使用 KSPROPERTY\_BDA\_NODE\_类型来检索节点类型列表。
ms.assetid: 8fe72434-3635-4c2c-a72a-1fd398e488d8
keywords:
- KSPROPERTY_BDA_NODE_TYPES 流媒体设备
topic_type:
- apiref
api_name:
- KSPROPERTY_BDA_NODE_TYPES
api_location:
- Bdamedia.h
api_type:
- HeaderDef
ms.date: 11/28/2017
ms.localizationpriority: medium
ms.openlocfilehash: 1e9edfbc59d070987e4f532bdaf129f323c07fe8
ms.sourcegitcommit: 4b7a6ac7c68e6ad6f27da5d1dc4deabd5d34b748
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2019
ms.locfileid: "72844341"
---
# <a name="ksproperty_bda_node_types"></a>KSPROPERTY\_BDA\_NODE\_类型


客户端使用 KSPROPERTY\_BDA\_NODE\_类型来检索节点类型列表。

## <span id="ddk_ksproperty_bda_node_types_ks"></span><span id="DDK_KSPROPERTY_BDA_NODE_TYPES_KS"></span>


### <a name="usage-summary-table"></a>使用情况摘要表

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
<th>属性描述符类型</th>
<th>属性值类型</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>“是”</p></td>
<td><p>无</p></td>
<td><p>Filter</p></td>
<td><p>KSPROPERTY</p></td>
<td><p>KSNODE_DESCRIPTORs 列表</p></td>
</tr>
</tbody>
</table>

 

<a name="remarks"></a>备注
-------

在模板拓扑中，每个节点类型只能出现一次，但它可以在实际拓扑中出现多次。 此节点类型列表是 KSNODE\_描述符结构的数组。 通常，此数组中每个元素的索引用于标识每个特定节点类型。

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
<td>Bdamedia （包括 Bdamedia）</td>
</tr>
</tbody>
</table>

## <a name="see-also"></a>另请参阅


[**BdaPropertyNodeTypes**](https://docs.microsoft.com/windows-hardware/drivers/ddi/bdasup/nf-bdasup-bdapropertynodetypes)

[**KSNODE\_描述符**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ks/ns-ks-_ksnode_descriptor)

[**KSPROPERTY**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ks/ns-ks-ksidentifier)

 

 






