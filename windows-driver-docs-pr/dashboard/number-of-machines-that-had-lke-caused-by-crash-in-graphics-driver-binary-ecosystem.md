---
title: 显卡驱动程序二进制文件中的崩溃导致发生了 LKE 的计算机数
description: 该度量将来自 7 天滑动窗口的遥测数据聚合为大量不同计算机，这些计算机由于显卡驱动程序二进制文件中的崩溃而发生了 LKE
ms.topic: article
ms.date: 05/20/2019
ms.author: paslote
author: parkeratmicrosoft
ms.localizationpriority: medium
ms.openlocfilehash: c3efaf22884fc51afa78e5886d07b0c25a972705
ms.sourcegitcommit: 04da1962e34908adeca54fcf5bbfbaa456efca5f
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/03/2019
ms.locfileid: "70223995"
---
# <a name="number-of-machines-that-had-an-lke-caused-by-a-crash-in-the-graphics-driver-binary"></a>显卡驱动程序二进制文件中的崩溃导致发生了 LKE 的计算机数

## <a name="description"></a>描述

在用户会话期间，驱动程序二进制文件中的崩溃将导致实时内核事件 (LKE)，该事件可能会重启计算机，并且可能会中断用户的工作流。 该度量评估使用给定版本驱动程序的计算机中因显卡二进制文件中的崩溃而导致 LKE 的计算机数（相对于总体）。

## <a name="measure-attributes"></a>度量属性

|属性|值|
|----|----|
|受众 |生态系统|
|时间段 |7 天滑动窗口|
|度量标准 |计算机的聚合|
|最小总体数量 |120,000 台计算机|
|通过标准 |<= 130/10,000 台计算机遇到 LKE 事件|
|度量 ID |17361846|

## <a name="calculation"></a>计算

1. 该度量将来自 7 天滑动窗口的遥测数据聚合为大量不同计算机，这些计算机由于显卡驱动程序二进制文件中的崩溃而发生了 LKE（相对于总体）   。
2. 发生 LKE 的计算机数 = 计数（使用给定版本驱动程序且出现 LKE 的计算机数） 
3. 计算机总数 = 计数（使用给定版本驱动程序的计算机数） 
4. 发生 LKE 的计算机的比率 = 发生 LKE 的计算机数/计算机总数 

### <a name="final-calculation"></a>最终计算

5. 相对于总体的 LKE 计算机命中数 = 发生 LKE 的计算机的比率 * 10,000 
6. 结果规范化为 10,000 台计算机，最终计算为：

   i. [相对于总体的 LKE 计算机命中数] 10,000 台计算机中由于显卡驱动程序二进制文件中的崩溃而发生 LKE 的不同计算机数