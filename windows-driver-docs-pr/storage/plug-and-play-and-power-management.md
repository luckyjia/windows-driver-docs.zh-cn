---
title: 即插即用和电源管理
description: 即插即用和电源管理
ms.assetid: 9e5d545d-ec24-42ac-a9e5-290502548fc0
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: 1d125b52fbc84b1ae367616c40873e220b9b2225
ms.sourcegitcommit: 0cc5051945559a242d941a6f2799d161d8eba2a7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "63389397"
---
# <a name="plug-and-play-and-power-management"></a>即插即用和电源管理


LsiU3AdapterControl 例程允许特殊适配器控制例程来实现而无需更改其 HW\_初始化\_数据结构。 它包含对将其替换为适用于通过电源管理周期的适配器的 HwFindAdapter 和 HwInitialize 例程 StopAdapter 和 ScsiRestartAdapter ControlTypes 的支持。 此外，LsiU3StartIo 例程增加了函数代码 SRB Srb 地处理\_函数\_HBA 关闭电源。

 

 




