---
title: GUID_DEVINTERFACE_WRITEONCEDISK
description: GUID_DEVINTERFACE_WRITEONCEDISK
ms.assetid: 8b1660e1-0868-40aa-ba47-dfcb6cf58aaf
keywords:
- GUID_DEVINTERFACE_WRITEONCEDISK 设备和驱动程序安装
topic_type:
- apiref
api_name:
- GUID_DEVINTERFACE_WRITEONCEDISK
api_location:
- Ntddstor.h
api_type:
- HeaderDef
ms.localizationpriority: medium
ms.date: 10/17/2018
ms.openlocfilehash: 262c3c24e75ace510ae0da5030392c5494c83c75
ms.sourcegitcommit: fb7d95c7a5d47860918cd3602efdd33b69dcf2da
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/25/2019
ms.locfileid: "67355159"
---
# <a name="guiddevinterfacewriteoncedisk"></a>GUID_DEVINTERFACE_WRITEONCEDISK


GUID_DEVINTERFACE_WRITEONCEDISK[设备接口类](https://docs.microsoft.com/windows-hardware/drivers/install/device-interface-classes)写为定义的一次磁盘设备。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">特性</th>
<th align="left">设置</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>标识符</p></td>
<td align="left"><p>GUID_DEVINTERFACE_WRITEONCEDISK</p></td>
</tr>
<tr class="even">
<td align="left"><p>类 GUID</p></td>
<td align="left"><p>{53F5630C-B6BF-11D0-94F2-00A0C91EFB8B}</p></td>
</tr>
</tbody>
</table>

 

<a name="remarks"></a>备注
-------

系统提供[存储设备驱动程序](https://docs.microsoft.com/windows-hardware/drivers/storage/storage-drivers)注册 GUID_DEVINTERFACE_WRITEONCEDISK 通知操作系统和应用程序的写入是否存在实例-一次磁盘，如 CD。

[**WriteOnceDiskClassGuid** ](writeoncediskclassguid.md) GUID_DEVINTERFACE_WRITEONCEDISK 设备接口类的已过时标识符。 对于此类的新实例，请改为使用 GUID_DEVINTERFACE_WRITEONCEDISK。

<a name="requirements"></a>要求
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="left"><p>Version</p></td>
<td align="left"><p>在 Microsoft Windows 2000 和更高版本的 Windows 中可用。</p></td>
</tr>
<tr class="even">
<td align="left"><p>Header</p></td>
<td align="left">Ntddstor.h （包括 Ntddstor.h）</td>
</tr>
</tbody>
</table>

## <a name="see-also"></a>请参阅


[**WriteOnceDiskClassGuid**](writeoncediskclassguid.md)

 

 






