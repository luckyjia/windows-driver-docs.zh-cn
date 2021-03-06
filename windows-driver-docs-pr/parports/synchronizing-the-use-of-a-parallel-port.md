---
title: 同步并行端口的使用
description: 同步并行端口的使用
ms.assetid: ea3a1998-9e31-4047-9193-6b402db222c9
keywords:
- 并行端口 WDK，同步
- 同步 WDK 并行端口
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: 4ea0266896b0ce1b9acc6249173d2e99b528a33d
ms.sourcegitcommit: 4b7a6ac7c68e6ad6f27da5d1dc4deabd5d34b748
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2019
ms.locfileid: "72842317"
---
# <a name="synchronizing-the-use-of-a-parallel-port"></a>同步并行端口的使用





客户端必须先通过分配并行端口来对并行端口进行同步，然后再使用它并在使用端口完成后释放端口。

或者，客户端可以选择和取消选择 IEEE 1284.3 设备（自动分配并释放并行端口）−请参阅[选择并取消选择附加到并行端口的 ieee 1284 设备](selecting-and-deselecting-an-ieee-1284-device-attached-to-a-parallel-p.md)。

客户端使用以下设备控制请求来分配和释放并行端口：

[**IOCTL\_内部\_并行\_端口\_分配**](https://docs.microsoft.com/windows-hardware/drivers/ddi/parallel/ni-parallel-ioctl_internal_parallel_port_allocate)

[**IOCTL\_内部\_并行\_端口\_免费**](https://docs.microsoft.com/windows-hardware/drivers/ddi/parallel/ni-parallel-ioctl_internal_parallel_port_free)

内核模式客户端还可以使用系统提供的[并行端口回调例程](https://docs.microsoft.com/windows-hardware/drivers/ddi/index)，该例程是使用[**IOCTL\_内部\_获取\_并行\_端口\_信息**](https://docs.microsoft.com/windows-hardware/drivers/ddi/parallel/ni-parallel-ioctl_internal_get_parallel_port_info)请求。 此请求返回一个[**并行\_端口\_信息**](https://docs.microsoft.com/windows-hardware/drivers/ddi/parallel/ns-parallel-_parallel_port_information)结构，其中包括指向系统提供的回调的以下指针：

-   **TryAllocatePort**成员是指向[*PPARALLEL\_尝试\_分配\_例程*](https://docs.microsoft.com/previous-versions/windows/hardware/drivers/ff544550(v=vs.85))回调的指针，该例程尝试分配并行端口。

-   **QueryNumWaiters**成员是指向[*PPARALLEL\_查询的指针\_等待进程\_例程*](https://docs.microsoft.com/windows-hardware/drivers/ddi/parallel/nc-parallel-pparallel_query_waiters_routine)回调，该回调返回在并行端口的工作队列中排队的端口分配和设备选择请求数。

-   **FreePort**成员是指向[*PPARALLEL\_免费\_例程*](https://docs.microsoft.com/windows-hardware/drivers/ddi/parallel/nc-parallel-pparallel_free_routine)回调的指针，它可释放并行端口。

[**IOCTL\_内部\_并行\_端口\_分配**](https://docs.microsoft.com/windows-hardware/drivers/ddi/parallel/ni-parallel-ioctl_internal_parallel_port_allocate)请求需要客户端的最小处理，因为系统提供的并行端口的函数驱动程序会将客户端的请求排队，前提是已分配了并行端口。 函数驱动程序在将端口分配给客户端之后，完成状态为 "状态"\_"分配" 请求。 由于无法接受的超时延迟或一些其他特定于设备的情况，客户端可以随时取消挂起的分配请求。

**请注意**   [**PPARALLEL\_尝试\_分配\_例程**](https://docs.microsoft.com/previous-versions/windows/hardware/drivers/ff544550(v=vs.85))回调立即返回。 如果客户端仅使用**PPARALLEL\_尝试\_分配\_例程**回调来尝试分配其他客户端正在争用的并行端口，则并行端口函数驱动程序可能永远不会将该端口分配给客户端。 若要确保成功，客户端必须使用并行端口分配请求。 （并行端口功能驱动程序会按照收到请求的顺序，对端口分配和设备选择请求进行排队。）

 

并行端口功能驱动程序向客户端分配并行端口之后，客户端将具有对端口的独占访问权限。 客户端必须调用[**PPARALLEL\_免费\_例程**](https://docs.microsoft.com/windows-hardware/drivers/ddi/parallel/nc-parallel-pparallel_free_routine)回调以释放端口。 客户端释放端口后，并行端口函数驱动程序将从端口的工作队列中删除下一个请求（端口分配或设备选择请求）（如果有），并完成请求。

客户端应使用[**PPARALLEL\_查询\_等待进程\_例程**](https://docs.microsoft.com/windows-hardware/drivers/ddi/parallel/nc-parallel-pparallel_query_waiters_routine)回调来确定是否有其他客户端正在等待并行端口。 需要为长时间分配端口的客户端应定期调用**PPARALLEL\_查询\_等待进程\_例程**回调来确定其他客户端正在等待获取端口，如果客户端正在等待，请尽快释放端口。

 

 




