---
title: DeinterlaceCloseStream 方法
description: 示例 DXVA\_DeinterlaceBobDeviceClass::DeinterlaceCloseStream 函数关闭取消隔行扫描流对象，并指示释放与该流关联的任何硬件资源的设备驱动程序。
ms.assetid: 89131951-7d79-4236-9d9f-51382d63baa9
keywords:
- DeinterlaceCloseStream 方法显示设备
- DeinterlaceCloseStream 方法显示设备，DXVA_DeinterlaceBobDeviceClass 接口
- DXVA_DeinterlaceBobDeviceClass 接口显示设备，DeinterlaceCloseStream 方法
topic_type:
- apiref
api_name:
- DXVA_DeinterlaceBobDeviceClass.DeinterlaceCloseStream
api_type:
- COM
ms.date: 12/06/2018
ms.localizationpriority: medium
ms.custom: seodec18
ms.openlocfilehash: 76360ef2452813339973d228550eeb37f7f0ffff
ms.sourcegitcommit: fb7d95c7a5d47860918cd3602efdd33b69dcf2da
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/25/2019
ms.locfileid: "67375841"
---
# <a name="dxvadeinterlacebobdeviceclassdeinterlaceclosestream-method"></a>DXVA\_DeinterlaceBobDeviceClass::DeinterlaceCloseStream 方法


该示例*DeinterlaceCloseStream*函数关闭取消隔行扫描流对象，并指示释放与该流关联的任何硬件资源的设备驱动程序。

<a name="syntax"></a>语法
------

```cpp
HRESULT DeinterlaceCloseStream();
```

<a name="parameters"></a>Parameters
----------

此方法没有任何参数。

<a name="return-value"></a>返回值
------------

将返回零 (S\_确定或 DD\_确定) 如果成功; 否则，返回错误代码。 请参阅*ddraw.h*有关错误代码的完整列表。

<a name="remarks"></a>备注
-------

*DeinterlaceCloseStream*函数直接映射到**DestroyMoComp**的成员[ **DD\_MOTIONCOMPCALLBACKS** ](https://docs.microsoft.com/windows/desktop/api/ddrawint/ns-ddrawint-dd_motioncompcallbacks)指向的驱动程序提供的结构*DdMoCompDestroy*回调。

## <a name="span-idseealsospansee-also"></a><span id="see_also"></span>另请参阅


[**DD\_MOTIONCOMPCALLBACKS**](https://docs.microsoft.com/windows/desktop/api/ddrawint/ns-ddrawint-dd_motioncompcallbacks)

[**DeinterlaceOpenStream**](dxva-deinterlacebobdeviceclass-deinterlaceopenstream.md)

 

 






