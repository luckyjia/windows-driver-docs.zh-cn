---
title: 渲染目标要求
description: 渲染目标要求
ms.assetid: 4d16819e-f209-44df-b5af-f3ff9cae256b
keywords:
- 呈现器目标 WDK Direct3D
- 颜色 WDK Direct3D 缓冲区
- WDK Direct3D 缓冲区
- 深度缓冲区 WDK Direct3D
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: 4045f4ecba4016c0e07aeef3fcab0d9db7144e22
ms.sourcegitcommit: fb7d95c7a5d47860918cd3602efdd33b69dcf2da
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/25/2019
ms.locfileid: "67380554"
---
# <a name="render-target-requirements"></a>渲染目标要求


## <span id="ddk_render_target_requirements_gg"></span><span id="DDK_RENDER_TARGET_REQUIREMENTS_GG"></span>


颜色缓冲区和深度缓冲区的要求如下所示：

### <a name="span-idcolorbuffersspanspan-idcolorbuffersspancolor-buffers"></a><span id="color_buffers"></span><span id="COLOR_BUFFERS"></span>颜色缓冲区

如果硬件不支持也是要用作纹理的呈现器目标 （即，设备不能"呈现为纹理"），该设备时不能调用**IDirect3DDevice7::SetRenderTarget**和**IDirect3D7::CreateDevice**方法。 Direct3D SDK 文档中介绍了这些方法。 呈现器目标是要用作纹理表示由 DDSCAPS 存在这一事实\_图面上的说明中的纹理标志 (请参阅**dwCaps**的成员[ **DDSCAPS**](https://docs.microsoft.com/previous-versions/windows/hardware/drivers/ff550286(v=vs.85))结构)。

### <a name="span-iddepthbuffersspanspan-iddepthbuffersspandepth-buffers"></a><span id="depth_buffers"></span><span id="DEPTH_BUFFERS"></span>深度缓冲区

如果硬件不支持的特定组合的呈现器目标和深度缓冲区，则该设备必须故障会导致这种情况下，检测这种不匹配如到在调用时的 API 调用**IDirect3D7::CreateDevice**并**IDirectDrawSurface7::AddAttachedSurface**方法。 分别在 Direct3D 和 DirectDraw SDK 文档集中，介绍这些方法。 此类不匹配的一个示例可能是当呈现器目标和深度缓冲区属于不同的位深度。 不要以透明方式更改该呈现器目标或深度缓冲区会导致无效组合才能正常工作的格式。 相反，而不通知 DirectX 运行时分配更高精度深度缓冲区。

 

 





