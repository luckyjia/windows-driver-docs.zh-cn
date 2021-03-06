---
title: DEVPKEY_Device_DriverPropPageProvider
description: DEVPKEY_Device_DriverPropPageProvider
ms.assetid: 9dabdba0-e179-467b-b0ad-960033a7ab86
keywords:
- DEVPKEY_Device_DriverPropPageProvider 设备和驱动程序安装
topic_type:
- apiref
api_name:
- DEVPKEY_Device_DriverPropPageProvider
api_location:
- Devpkey.h
api_type:
- HeaderDef
ms.localizationpriority: medium
ms.date: 10/17/2018
ms.openlocfilehash: bc808e35ccda214650f64a52ba90409a1d17d34e
ms.sourcegitcommit: e180a0670b0b78c30541755e6e030df249979f1e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/16/2020
ms.locfileid: "86418263"
---
# <a name="devpkey_device_driverproppageprovider"></a>DEVPKEY_Device_DriverPropPageProvider


DEVPKEY_Device_DriverPropPageProvider 设备属性表示 DLL 的名称和 DLL 中的入口点，作为设备实例的属性页提供程序进行注册。

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
<td align="left"><p>DEVPKEY_Device_DriverPropPageProvider</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>属性数据类型标识符</strong></p></td>
<td align="left"><p><a href="devprop-type-string.md" data-raw-source="[&lt;strong&gt;DEVPROP_TYPE_STRING&lt;/strong&gt;](devprop-type-string.md)"><strong>DEVPROP_TYPE_STRING</strong></a></p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>和</strong></p></td>
<td align="left"><p>安装应用程序和安装程序的只读访问</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>对应的注册表值标识符和注册表值名称</strong></p></td>
<td align="left"><p>REGSTR_VAL_ENUMPROPPAGES_32</p>
<p><strong>EnumPropPages32</strong></p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>各种?</strong></p></td>
<td align="left"><p>否</p></td>
</tr>
</tbody>
</table>

 

<a name="remarks"></a>备注
-------

你可以使用 inf [**AddReg 指令**](https://docs.microsoft.com/windows-hardware/drivers/install/inf-addreg-directive)设置 DEVPKEY_Device_DriverPropPageProvider 的值，该指令包含用于安装设备的 inf 文件的[**inf *DDInstall*部分**](https://docs.microsoft.com/windows-hardware/drivers/install/inf-ddinstall-section)。

可以通过调用[**SetupDiGetDeviceProperty**](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdigetdevicepropertyw)来检索 DEVPKEY_Device_DriverPropPageProvider 的值。

Windows Server 2003、Windows XP 和 Windows 2000 支持此属性，但不支持 DEVPKEY_Device_DriverPropPageProvider 属性键。 在这些早期版本的 Windows 上，可以通过访问设备实例的软件密钥下的相应**EnumPropPages32**注册表值来访问此属性的值。 有关如何在这些早期版本的 Windows 上访问此属性值的信息，请参阅[访问设备驱动程序属性](https://docs.microsoft.com/windows-hardware/drivers/install/accessing-device-driver-properties)。

<a name="requirements"></a>要求
------------

**版本**： windows Vista 和更高版本的 windows**头**： Devpkey （包括 Devpkey）


## <a name="see-also"></a>请参阅


[**INF AddReg 指令**](https://docs.microsoft.com/windows-hardware/drivers/install/inf-addreg-directive)

[**INF *DDInstall*部分**](https://docs.microsoft.com/windows-hardware/drivers/install/inf-ddinstall-section)

[**SetupDiGetDeviceProperty**](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdigetdevicepropertyw)

 

 






