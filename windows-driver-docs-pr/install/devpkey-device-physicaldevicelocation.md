---
title: DEVPKEY_Device_PhysicalDeviceLocation
description: DEVPKEY_Device_PhysicalDeviceLocation
ms.assetid: DEF01D17-7E32-45BB-8846-D3B3B60506EB
keywords:
- DEVPKEY_Device_PhysicalDeviceLocation 设备和驱动程序安装
topic_type:
- apiref
api_name:
- DEVPKEY_Device_PhysicalDeviceLocation
api_location:
- Devpkey.h
api_type:
- HeaderDef
ms.localizationpriority: medium
ms.date: 10/17/2018
ms.openlocfilehash: 7be1b9dbd3bf7a1420e374fdcbb59ef69e90493d
ms.sourcegitcommit: e180a0670b0b78c30541755e6e030df249979f1e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/16/2020
ms.locfileid: "86418229"
---
# <a name="devpkey_device_physicaldevicelocation"></a>DEVPKEY_Device_PhysicalDeviceLocation


DEVPKEY_Device_PhysicalDeviceLocation 设备属性将设备固件提供的物理设备位置信息封装到 Windows 中。

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
<td align="left"><p>DEVPKEY_Device_PhysicalDeviceLocation</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>属性数据类型标识符</strong></p></td>
<td align="left"><p><a href="devprop-type-string.md" data-raw-source="[&lt;strong&gt;DEVPROP_TYPE_BINARY&lt;/strong&gt;](devprop-type-string.md)"><strong>DEVPROP_TYPE_BINARY</strong></a></p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>和</strong></p></td>
<td align="left"><p>安装应用程序和安装程序的只读访问</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>对应 SPDRP_<em>Xxx</em> </strong> <strong>标识符</strong></p></td>
<td align="left"><p>SPDRP_PHYSICAL_DEVICE_LOCATION</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>各种?</strong></p></td>
<td align="left"><p>否</p></td>
</tr>
</tbody>
</table>

 

<a name="remarks"></a>备注
-------

Windows 将 DEVPKEY_Device_PhysicalDeviceLocation 的值设置为物理设备位置信息。 信息的格式在 ACPI 4.0 a 规范中的6.1.6 部分定义。

可以调用[**SetupDiGetDeviceProperty**](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdigetdevicepropertyw)来检索 DEVPKEY_Device_PhysicalDeviceLocation 的值。

<a name="requirements"></a>要求
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="left"><p>版本</p></td>
<td align="left"><p>从 Windows 8 开始提供</p></td>
</tr>
<tr class="even">
<td align="left"><p>标头</p></td>
<td align="left">Devpkey （包括 Devpkey）</td>
</tr>
</tbody>
</table>

## <a name="see-also"></a>请参阅


[**SetupDiGetDeviceProperty**](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdigetdevicepropertyw)

 

 






