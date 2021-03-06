---
title: Bug 检查 0xD5 DRIVER_PAGE_FAULT_IN_FREED_SPECIAL_POOL
description: DRIVER_PAGE_FAULT_IN_FREED_SPECIAL_POOL bug 检查的值为0x000000D5。 这表明驱动程序已引用先前释放的内存。
ms.assetid: b86e55d2-122f-40ac-adb3-092511d3274e
keywords:
- Bug 检查 0xD5 DRIVER_PAGE_FAULT_IN_FREED_SPECIAL_POOL
- DRIVER_PAGE_FAULT_IN_FREED_SPECIAL_POOL
ms.date: 05/23/2017
topic_type:
- apiref
api_name:
- DRIVER_PAGE_FAULT_IN_FREED_SPECIAL_POOL
api_type:
- NA
ms.localizationpriority: medium
ms.openlocfilehash: d65d5fa367a6c562eaf83a3a8088d22a58a2dbd4
ms.sourcegitcommit: dadc9ced1670d667e31eb0cb58d6a622f0f09c46
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84534554"
---
# <a name="bug-check-0xd5-driver_page_fault_in_freed_special_pool"></a>Bug 检查0xD5：已 \_ \_ \_ \_ 释放的 \_ 特殊 \_ 池中的驱动程序页错误


\_ \_ \_ \_ \_ \_ 已释放的特殊池 bug 检查中的驱动程序页错误的值为0x000000D5。 这表明驱动程序已引用先前释放的内存。

> [!IMPORTANT]
> 本主题适用于程序员。 如果你是在使用计算机时收到蓝屏错误代码的客户，请参阅[排查蓝屏错误](https://www.windows.com/stopcode)。


## <a name="driver_page_fault_in_freed_special_pool-parameters"></a>\_ \_ \_ \_ 释放 \_ 特殊 \_ 池参数时出现驱动程序页错误


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">参数</th>
<th align="left">说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>1</p></td>
<td align="left"><p>引用的内存地址</p></td>
</tr>
<tr class="even">
<td align="left"><p>2</p></td>
<td align="left"><p><strong>0：</strong>读取</p>
<p><strong>1：</strong>写入</p></td>
</tr>
<tr class="odd">
<td align="left"><p>3</p></td>
<td align="left"><p>确定所引用内存的地址（如果已知）</p></td>
</tr>
<tr class="even">
<td align="left"><p>4</p></td>
<td align="left"><p>保留</p></td>
</tr>
</tbody>
</table>

 
[**！分析**](-analyze.md)调试扩展显示有关 bug 检查的信息，可帮助确定根本原因。
如果可以识别负责错误的驱动程序，则会在蓝色屏幕上打印其名称，并将其存储在内存中的位置（PUNICODE \_ 字符串） **KiBugCheckDriver**。

<a name="cause"></a>原因
-----

"驱动程序验证程序**特殊池**" 选项已发现驱动程序访问先前释放的内存。

有关特殊池的信息，请参阅 Windows 驱动程序工具包的驱动程序验证程序部分。

<a name="remarks"></a>注解
-------

这不能通过**try-except**处理程序来保护--它只能通过探测进行保护。

 

 




