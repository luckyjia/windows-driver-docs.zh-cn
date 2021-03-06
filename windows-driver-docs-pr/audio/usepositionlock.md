---
title: UsePositionLock
description: UsePositionLock 注册表值更改 PortCls 序列化其 i/o 的方式。
ms.assetid: AD5AF873-4129-4C82-B251-0469CF6149E9
ms.date: 11/28/2017
ms.localizationpriority: medium
ms.openlocfilehash: 986e8e26c7edf29d37314f629c0c385a0ae38749
ms.sourcegitcommit: 4b7a6ac7c68e6ad6f27da5d1dc4deabd5d34b748
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2019
ms.locfileid: "72829999"
---
# <a name="usepositionlock"></a>UsePositionLock


*UsePositionLock*注册表值更改 PortCls 序列化其 i/o 的方式。 如果你的音频驱动程序受到 portcls 用于序列化的全局设备锁定的故障影响，则启用此设置可能会很有帮助。 请注意，当启用*UsePositionLock*时，它会由音频驱动程序应用于下面列出的回调与其他属性回叫之间的任何序列化（如果需要）。 默认情况下不启用此标志。 在打开驱动程序之前，请务必查看驱动程序中是否有任何争用情况。

使用以下 INF 设置来启用此行为。

```inf
 
[MyAudioDevice.AddReg]
HKR, DispatchSettings, UsePositionLock, 3, 01, 00, 00, 00
```

此 INF 设置创建以下注册表值。 注册表项路径中使用了 {4d36e96c-e325-11ce-bfc1-08002be10318} 的媒体 GUID 和音频设备的 &lt;实例\#&gt;。

```text
\HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Class\{4d36e96c-e325-11ce-bfc1-08002be10318}\<instance#>\DispatchSettings\UsePositionLock 
```

如果此值设置为1或更高，则 portcls 将使用流位置锁来序列化下面列出的回调。 如果它不存在或设置为零，则默认行为是使用全局设备锁。 第一次添加设备时，将读取此值。

只有 WaveRT 和拓扑筛选器支持*UsePositionLock*设置。 Portcls 会在设备添加时间读取此注册表值，该设置将一直保留，直到删除功能设备对象（FDO）。

如果 portcls 检测到此标志已打开，则它不会将以下属性与全局设备锁定序列化。

-   {KSPROPSETID\_RtAudio， [**KSPROPERTY\_RtAudio\_GETREADPACKET**](ksproperty-rtaudio-getreadpacket.md)}

-   {KSPROPSETID\_RtAudio， [**KSPROPERTY\_RtAudio\_SETWRITEPACKET**](ksproperty-rtaudio-setwritepacket.md)}

-   {KSPROPSETID\_RtAudio， [**KSPROPERTY\_RtAudio\_表示\_位置**](ksproperty-rtaudio-presentation-position.md)}

-   {KSPROPSETID\_RtAudio， [**KSPROPERTY\_RtAudio\_PACKETCOUNT**](ksproperty-rtaudio-packetcount.md)}

-   {KSPROPSETID\_音频，[**KSPROPERTY\_音频\_位置**](ksproperty-audio-position.md)}

-   {KSPROPSETID\_音频， [**KSPROPERTY\_音频\_POSITIONEX**](ksproperty-audio-positionex.md)}

这意味着，以下微型端口的回调不会与其他属性请求（包括设置状态请求）进行序列化。

-   [**IMiniportWaveRTInputStream::GetReadPacket**](https://docs.microsoft.com/windows-hardware/drivers/ddi/portcls/nf-portcls-iminiportwavertinputstream-getreadpacket)

-   [**IMiniportWaveRTOutputStream::SetWritePacket**](https://docs.microsoft.com/windows-hardware/drivers/ddi/portcls/nf-portcls-iminiportwavertoutputstream-setwritepacket)

-   [**IMiniportWaveRTOutputStream::GetOutputStreamPresentationPosition**](https://docs.microsoft.com/windows-hardware/drivers/ddi/portcls/nf-portcls-iminiportwavertoutputstream-getoutputstreampresentationposition)

-   [**IMiniportWaveRTOutputStream::GetPacketCount**](https://docs.microsoft.com/windows-hardware/drivers/ddi/portcls/nf-portcls-iminiportwavertoutputstream-getpacketcount)

-   [**IMiniportWaveRTStream::GetPosition**](https://docs.microsoft.com/previous-versions/windows/hardware/drivers/ff536749(v=vs.85))

 

 





