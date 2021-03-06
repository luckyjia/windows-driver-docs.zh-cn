---
title: Bug 检查 0x15B WORKER_THREAD_RETURNED_WITH_SYSTEM_PAGE_PRIORITY_ACTIVE
description: WORKER_THREAD_RETURNED_WITH_SYSTEM_PAGE_PRIORITY_ACTIVE bug 检查具有一个值，该值指示工作线程的系统页优先级就已经泄露 0x0000015B。
ms.assetid: F618AA35-54BC-4923-99C8-311DB1D20C71
keywords:
- Bug 检查 0x15B WORKER_THREAD_RETURNED_WITH_SYSTEM_PAGE_PRIORITY_ACTIVE
- WORKER_THREAD_RETURNED_WITH_SYSTEM_PAGE_PRIORITY_ACTIVE
ms.date: 05/23/2017
topic_type:
- apiref
api_name:
- WORKER_THREAD_RETURNED_WITH_SYSTEM_PAGE_PRIORITY_ACTIVE
api_type:
- NA
ms.localizationpriority: medium
ms.openlocfilehash: e33613c3f97e82f041f0c4698129288fdfb241fa
ms.sourcegitcommit: d03b44343cd32b3653d0471afcdd3d35cb800c0d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2019
ms.locfileid: "67520020"
---
# <a name="bug-check-0x15b-workerthreadreturnedwithsystempagepriorityactive"></a>Bug 检查 0x15B：辅助角色\_线程\_返回\_WITH\_系统\_页\_优先级\_ACTIVE


辅助角色\_线程\_返回\_WITH\_系统\_页\_优先级\_活动 bug 检查的值为 0x0000015B。 这表明工作线程的系统页优先级就已经泄露由被调用的辅助角色例程。

> [!IMPORTANT]
> 本主题面向程序员。 如果你已使用计算机时收到一个蓝色的屏幕，错误代码的客户，请参阅[疑难解答蓝屏错误](https://www.windows.com/stopcode)。


## <a name="workerthreadreturnedwithsystempagepriorityactive-parameters"></a>辅助角色\_线程\_返回\_WITH\_系统\_页\_优先级\_活动的参数


| 参数 | 描述                                                                    |
|-----------|--------------------------------------------------------------------------------|
| 1         | 辅助角色 (在此地址来查找有问题的驱动程序上执行操作 ln) 例程的地址 |
| 2         | 当前系统页面优先级值                                             |
| 3         | 工作项参数                                                             |
| 4         | 工作项地址                                                               |

 

 

 




