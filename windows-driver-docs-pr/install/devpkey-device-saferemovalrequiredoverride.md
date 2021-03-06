---
title: DEVPKEY_Device_SafeRemovalRequiredOverride
description: DEVPKEY_Device_SafeRemovalRequiredOverride
ms.assetid: 8289effe-3849-41bf-b870-69e3d8cb8850
keywords:
- DEVPKEY_Device_SafeRemovalRequiredOverride 设备和驱动程序安装
topic_type:
- apiref
api_name:
- DEVPKEY_Device_SafeRemovalRequiredOverride
api_location:
- Devpkey.h
api_type:
- HeaderDef
ms.localizationpriority: medium
ms.date: 10/17/2018
ms.openlocfilehash: debf67c3e3b03604448ab9e8ced10e0fdbdeb969
ms.sourcegitcommit: e180a0670b0b78c30541755e6e030df249979f1e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/16/2020
ms.locfileid: "86418418"
---
# <a name="devpkey_device_saferemovalrequiredoverride"></a>DEVPKEY_Device_SafeRemovalRequiredOverride


DEVPKEY_Device_SafeRemovalRequiredOverride 设备属性表示设备实例的安全删除重写。

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
<td align="left"><p>DEVPKEY_Device_SafeRemovalRequiredOverride</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>属性数据类型标识符</strong></p></td>
<td align="left"><p><a href="devprop-type-boolean.md" data-raw-source="[&lt;strong&gt;DEVPROP_TYPE_BOOLEAN&lt;/strong&gt;](devprop-type-boolean.md)"><strong>DEVPROP_TYPE_BOOLEAN</strong></a></p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>和</strong></p></td>
<td align="left"><p>安装应用程序和安装程序的读取和写入访问权限</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>各种?</strong></p></td>
<td align="left"><p>否</p></td>
</tr>
</tbody>
</table>

 

<a name="remarks"></a>备注
-------

此设备属性可用于重写 Windows 即插即用（PnP）用于计算[**DEVPKEY_Device_SafeRemovalRequired**](devpkey-device-saferemovalrequired.md)设备属性值的启发式结果。 执行此替代的方式如下：

-   如果 DEVPKEY_Device_SafeRemovalRequiredOverride 设备属性设置为 "DEVPROP_TRUE 并且设备实例可移动或具有可移动上级，则 PnP 会将 DEVPKEY_Device_SafeRemovalRequired 设备属性设置为 DEVPROP_TRUE，并且不使用试探法。

    **注意**   如果设置了其可移动设备功能，则会将设备实例视为可移动设备。 有关详细信息，请参阅[可移动设备功能的概述](https://docs.microsoft.com/windows-hardware/drivers/install/overview-of-the-removable-device-capability)。

     

-   如果 DEVPKEY_Device_SafeRemovalRequiredOverride 设备属性设置为 DEVPROP_TRUE 并且设备实例（或祖先）不可删除，则 PnP 会将 DEVPKEY_Device_SafeRemovalRequired 设置为 DEVPROP_FALSE，并且不使用试探法。

-   如果 DEVPKEY_Device_SafeRemovalRequiredOverride 设备属性未设置或设置为 DEVPROP_FALSE，则 PnP 会将 DEVPKEY_Device_SafeRemovalRequired 设备属性设置为使用试探法确定的值。

可以通过调用[**SetupDiGetDeviceProperty**](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdigetdevicepropertyw)来检索 DEVPKEY_Device_SafeRemovalRequiredOverride 的值。 还可以通过调用[**SetupDiSetDeviceProperty**](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdisetdevicepropertyw)来设置此值。

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
<td align="left"><p>在 windows 7 和更高版本的 Windows 中可用。</p></td>
</tr>
<tr class="even">
<td align="left"><p>标头</p></td>
<td align="left">Devpkey （包括 Devpkey）</td>
</tr>
</tbody>
</table>

## <a name="see-also"></a>请参阅


[**SetupDiGetDeviceProperty**](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdigetdevicepropertyw)

[**SetupDiSetDeviceProperty**](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdisetdevicepropertyw)

 

 






