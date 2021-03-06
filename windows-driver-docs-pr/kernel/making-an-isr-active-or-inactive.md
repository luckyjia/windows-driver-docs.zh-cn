---
title: 使 ISR 处于活动或非活动状态
description: 从 Windows 8 开始，驱动程序可以调用 IoReportInterruptActive 或 IoReportInterruptInactive 例程，使已注册的中断服务例程（ISR）处于活动状态或非活动状态。
ms.assetid: 788D9341-D1F8-4126-8C30-AA49DE27F4BB
ms.localizationpriority: medium
ms.date: 10/17/2018
ms.openlocfilehash: 98df2d6f2396a33cb175eb0d5b2ec89ecfc6ef33
ms.sourcegitcommit: 4b7a6ac7c68e6ad6f27da5d1dc4deabd5d34b748
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2019
ms.locfileid: "72838552"
---
# <a name="making-an-isr-active-or-inactive"></a>使 ISR 处于活动或非活动状态


从 Windows 8 开始，驱动程序可以调用[**IoReportInterruptActive**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/nf-wdm-ioreportinterruptactive)或[**IoReportInterruptInactive**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/nf-wdm-ioreportinterruptinactive)例程，使已注册的中断服务例程（ISR）处于活动状态或非活动状态。

若要注册 ISR，并将 ISR 连接到一个或一组中断，驱动程序将调用[**IoConnectInterruptEx**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/nf-wdm-ioconnectinterruptex)例程。 注册 ISR 后，驱动程序可以使用**IoReportInterruptActive**和**IoReportInterruptInactive**来执行轻型（或 "软"）连接和断开操作，使 ISR 的注册保持不变。 **IoReportInterruptInactive**通过软断开关联的中断或中断来禁用对 ISR 的调用。 **IoReportInterruptActive**软-连接这些中断以启用对 ISR 的调用。

例如，驱动程序可以调用**IoReportInterruptInactive** ，在设备退出 D0 电源状态之前软断开一组中断，并调用**IoReportInterruptActive**在设备重新输入 D0 后软连接这些中断。 原则上，驱动程序可以在设备退出 D0 之前调用[**IoDisconnectInterruptEx**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/nf-wdm-iodisconnectinterruptex) ，并在设备重新输入 d0 后调用**IoConnectInterruptEx** 。 但是， **IoReportInterrupt * Xxx*** 调用比**IoConnectInterruptEx**和**IoDisconnectInterruptEx**调用更快。 与**IoConnectInterruptEx**和**IoDisconnectInterruptEx**调用相比，这种情况可能因多种原因（例如，系统资源不足）而失败， **IoReportInterrupt * Xxx*** 调用很少会失败（如果情况过多）。 此外，可以在 IRQL &lt;= 调度\_级别调用**IoReportInterrupt * Xxx*** 例程，而只能在被动\_级别调用**IoConnectInterruptEx**和**IoDisconnectInterruptEx** 。

默认情况下，在**IoConnectInterruptEx**成功注册 isr 后，isr 处于活动状态（已启用对 isr 的调用）。

调用**IoReportInterruptInactive**和**IoReportInterruptActive**是可选的。 如果驱动程序永远不会调用这些例程，则已注册的 ISR 会保持活动状态，直到驱动程序调用[**IoDisconnectInterruptEx**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/nf-wdm-iodisconnectinterruptex)例程来取消注册 ISR。

驱动程序应将设备配置为仅当这些中断的 ISR 处于活动状态时才发出中断。 当 ISR 处于非活动状态时，无法阻止设备发出中断可能会导致系统不稳定。 例如，如果设备与其他设备共享级别触发的中断线路，并且设备在 ISR 处于非活动状态时发出中断请求，则线路上其他设备的 Isr 不会确认中断，中断将继续激发. 在调用**IoReportInterruptInactive**之前，驱动程序应将设备配置为停止发出中断。 调用**IoReportInterruptActive**之后，驱动程序应将设备配置为开始发出中断。

若要注销 ISR，无论 ISR 当前处于活动状态还是非活动状态，驱动程序都可以调用**IoDisconnectInterruptEx** 。

ISR 已经处于活动状态时出现的**IoReportInterruptActive**调用不起作用，但不会被视为错误。 同样，当 ISR 已经处于非活动状态时，就不**会有任何**影响，但不会被视为错误。

 

 




