---
title: DEVPKEY_Device_HardwareIds
description: DEVPKEY_Device_HardwareIds
ms.assetid: 4bfd50b3-027f-4f79-8bff-d0c92c1b2386
keywords:
- DEVPKEY_Device_HardwareIds 设备和驱动程序安装
topic_type:
- apiref
api_name:
- DEVPKEY_Device_HardwareIds
api_location:
- Devpkey.h
api_type:
- HeaderDef
ms.localizationpriority: medium
ms.date: 10/17/2018
ms.openlocfilehash: 310e744d9b6505c3c8fb46a3776de79a62b1c3f2
ms.sourcegitcommit: e180a0670b0b78c30541755e6e030df249979f1e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/16/2020
ms.locfileid: "86418292"
---
# <a name="devpkey_device_hardwareids"></a>DEVPKEY_Device_HardwareIds


DEVPKEY_DEVICE_HardwareIds 设备属性表示设备实例的硬件标识符的列表。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr>
<th>属性</th>
<th>Value</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><strong>属性键</strong></p></td>
<td align="left"><p>DEVPKEY_Device_HardwareIds</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>属性数据类型标识符</strong></p></td>
<td align="left"><p><a href="devprop-type-string-list.md" data-raw-source="[&lt;strong&gt;DEVPROP_TYPE_STRING_LIST&lt;/strong&gt;](devprop-type-string-list.md)"><strong>DEVPROP_TYPE_STRING_LIST</strong></a></p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>数据格式</strong></p></td>
<td align="left">"<em>hw-id1</em>\ 0<em>hw-id</em>2 \ 0 ..."<em>hw-idn</em>\ 0 \ 0 "</td>
</tr>
<tr class="even">
<td align="left"><p><strong>和</strong></p></td>
<td align="left"><p>安装应用程序和安装程序的只读访问</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>对应 SPDRP_</strong><em>Xxx</em> <strong>标识符</strong></p></td>
<td align="left"><p>SPDRP_HARDWAREID</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>各种?</strong></p></td>
<td align="left"><p>否</p></td>
</tr>
</tbody>
</table>

 

<a name="remarks"></a>备注
-------

DEVPKEY_DEVICE_HardwareIds 的值是由安装设备的 INF 文件的 " [**Inf*模型*" 部分**](https://docs.microsoft.com/windows-hardware/drivers/install/inf-models-section)提供的设备的*hw id*输入值设置的。

可以调用[**SetupDiGetDeviceProperty**](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdigetdevicepropertyw)来检索 DEVPKEY_DEVICE_HardwareIds 的值。

Windows Server 2003、Windows XP 和 Windows 2000 支持此属性，但不支持 DEVPKEY_DEVICE_HardwareIds 属性键。 相反，你可以使用相应的 SPDRP_HARDWAREID 标识符来访问这些早期版本的 Windows 上的属性值。 有关如何在这些早期版本的 Windows 上访问此属性值的信息，请参阅[SPDRP_Xxx 属性访问设备实例](https://docs.microsoft.com/windows-hardware/drivers/install/accessing-device-instance-spdrp-xxx-properties)。

<a name="requirements"></a>要求
------------

**版本**： windows Vista 和更高版本的 windows**头**： Devpkey （包括 Devpkey）


## <a name="see-also"></a>请参阅


[**INF*型号*部分**](https://docs.microsoft.com/windows-hardware/drivers/install/inf-models-section)

[**SetupDiGetDeviceProperty**](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdigetdevicepropertyw)

 

 






