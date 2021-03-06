---
title: DEVPKEY_Device_DriverProvider
description: DEVPKEY_Device_DriverProvider
ms.assetid: cbc1582a-1f43-4239-b00a-f7c99bf2deee
keywords:
- DEVPKEY_Device_DriverProvider 设备和驱动程序安装
topic_type:
- apiref
api_name:
- DEVPKEY_Device_DriverProvider
api_location:
- Devpkey.h
api_type:
- HeaderDef
ms.localizationpriority: medium
ms.date: 10/17/2018
ms.openlocfilehash: c3bc2a83f0c671b9ab88daf223494c9863578555
ms.sourcegitcommit: e180a0670b0b78c30541755e6e030df249979f1e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/16/2020
ms.locfileid: "86418255"
---
# <a name="devpkey_device_driverprovider"></a>DEVPKEY_Device_DriverProvider


DEVPKEY_Device_DriverProvider 设备属性表示设备实例的[驱动程序包](https://docs.microsoft.com/windows-hardware/drivers/install/driver-packages)的访问接口的名称。

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
<td align="left"><p>DEVPKEY_Device_DriverProvider</p></td>
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
<td align="left"><p>REGSTR_VAL_PROVIDER_NAME</p>
<p><strong>ProviderName</strong></p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>各种?</strong></p></td>
<td align="left"><p>否</p></td>
</tr>
</tbody>
</table>

 

<a name="remarks"></a>备注
-------

DEVPKEY_Device_DriverProvider 的值由设备 INF 文件的[**INF 版本部分**](https://docs.microsoft.com/windows-hardware/drivers/install/inf-driverver-directive)中包含的**提供程序**指令提供。

可以调用[**SetupDiGetDeviceProperty**](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdigetdevicepropertyw)来检索 DEVPKEY_Device_DriverProvider 的值。

Windows Server 2003、Windows XP 和 Windows 2000 支持此属性，但不支持 DEVPKEY_Device_DriverProvider 属性键。 在这些早期版本的 Windows 上，你可以访问此属性的值，方法是在设备实例的软件密钥下访问相应的**ProviderName**注册表值。 有关如何在这些早期版本的 Windows 上访问此属性值的信息，请参阅[访问设备驱动程序属性](https://docs.microsoft.com/windows-hardware/drivers/install/accessing-device-driver-properties)。

<a name="requirements"></a>要求
------------

**版本**： windows Vista 和更高版本的 windows**头**： Devpkey （包括 Devpkey）


## <a name="see-also"></a>请参阅


[**INF Version 节**](https://docs.microsoft.com/windows-hardware/drivers/install/inf-driverver-directive)

[**SetupDiGetDeviceProperty**](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdigetdevicepropertyw)

 

 






