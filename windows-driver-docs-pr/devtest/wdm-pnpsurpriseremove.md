---
title: PnpSurpriseRemove 规则（wdm）
description: PnpSurpriseRemove 规则指定在处理 IRP \_ MN \_ 意外删除请求时，驱动程序不调用 IoDeleteDevice 或 IoDetachDevice \_ 。
ms.assetid: 58553c78-04c3-423c-bf68-69d5a8fbfa9b
ms.date: 05/21/2018
keywords:
- PnpSurpriseRemove 规则（wdm）
topic_type:
- apiref
api_name:
- PnpSurpriseRemove
api_type:
- NA
ms.localizationpriority: medium
ms.openlocfilehash: 06d84d85f5cda055ec444b45eda1bf3e2f2d663e
ms.sourcegitcommit: 82a9be3b3584f991e5121f8f46a972e04185fa52
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85917665"
---
# <a name="pnpsurpriseremove-rule-wdm"></a>PnpSurpriseRemove 规则（wdm）


**PnpSurpriseRemove**规则指定在处理[**IRP \_ MN \_ 意外 \_ 删除**](https://docs.microsoft.com/windows-hardware/drivers/kernel/irp-mn-surprise-removal)请求时，驱动程序不调用 IoDeleteDevice 或 IoDetachDevice。

PnP 管理器发送[**IRP \_ MN \_ 意外 \_ 删除**](https://docs.microsoft.com/windows-hardware/drivers/kernel/irp-mn-surprise-removal)请求，通知驱动程序设备不再可用于 i/o 操作，并且可能已从计算机上意外删除。

-   所有 PnP 驱动程序都必须处理[**IRP \_ MN \_ 意外 \_ 删除**](https://docs.microsoft.com/windows-hardware/drivers/kernel/irp-mn-surprise-removal)请求。
-   此驱动程序不能在设备对象上调用[**IoDeleteDevice**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/nf-wdm-iodeletedevice)或[**IODETACHDEVICE**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/nf-wdm-iodetachdevice) ，直到 IRP \_ MN \_ 意外 \_ 删除 irp 成功并关闭对该设备的所有打开的句柄。
-   然后，PnP 管理器将[**IRP \_ MN \_ REMOVE \_ 设备**](https://docs.microsoft.com/windows-hardware/drivers/kernel/irp-mn-remove-device)请求发送到设备堆栈。 为响应删除 IRP，驱动程序从堆栈中分离其设备对象并将其删除。

有关驱动程序应如何响应[**irp \_ MN \_ 意外 \_ 删除**](https://docs.microsoft.com/windows-hardware/drivers/kernel/irp-mn-surprise-removal)请求的详细信息，请参阅[**处理 irp \_ MN \_ 意外 \_ 删除请求**](https://docs.microsoft.com/windows-hardware/drivers/kernel/handling-an-irp-mn-surprise-removal-request)

**驱动程序模型： WDM**

<a name="how-to-test"></a>如何测试
-----------

<table>
<colgroup>
<col width="100%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">在编译时</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>运行<a href="https://docs.microsoft.com/windows-hardware/drivers/devtest/static-driver-verifier" data-raw-source="[Static Driver Verifier](https://docs.microsoft.com/windows-hardware/drivers/devtest/static-driver-verifier)">静态驱动程序验证程序</a>并指定<strong>PnpSurpriseRemove</strong>规则。</p>
使用以下步骤来运行代码分析：
<ol>
<li><a href="https://docs.microsoft.com/windows-hardware/drivers/devtest/using-static-driver-verifier-to-find-defects-in-drivers#preparing-your-source-code" data-raw-source="[Prepare your code (use role type declarations).](https://docs.microsoft.com/windows-hardware/drivers/devtest/using-static-driver-verifier-to-find-defects-in-drivers#preparing-your-source-code)">准备你的代码（使用角色类型声明）。</a></li>
<li><a href="https://docs.microsoft.com/windows-hardware/drivers/devtest/using-static-driver-verifier-to-find-defects-in-drivers#running-static-driver-verifier" data-raw-source="[Run Static Driver Verifier.](https://docs.microsoft.com/windows-hardware/drivers/devtest/using-static-driver-verifier-to-find-defects-in-drivers#running-static-driver-verifier)">运行静态驱动程序验证程序。</a></li>
<li><a href="https://docs.microsoft.com/windows-hardware/drivers/devtest/using-static-driver-verifier-to-find-defects-in-drivers#viewing-and-analyzing-the-results" data-raw-source="[View and analyze the results.](https://docs.microsoft.com/windows-hardware/drivers/devtest/using-static-driver-verifier-to-find-defects-in-drivers#viewing-and-analyzing-the-results)">查看并分析结果。</a></li>
</ol>
<p>有关详细信息，请参阅<a href="https://docs.microsoft.com/windows-hardware/drivers/devtest/using-static-driver-verifier-to-find-defects-in-drivers" data-raw-source="[Using Static Driver Verifier to Find Defects in Drivers](https://docs.microsoft.com/windows-hardware/drivers/devtest/using-static-driver-verifier-to-find-defects-in-drivers)">使用静态驱动程序验证器查找驱动程序中的缺陷</a>。</p></td>
</tr>
</tbody>
</table>

<a name="applies-to"></a>适用于
----------

[**IoDeleteDevice**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/nf-wdm-iodeletedevice) 
[**IoDetachDevice**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/nf-wdm-iodetachdevice)另请参阅
--------

[**处理 IRP \_MN \_ 意外 \_ 删除请求**](https://docs.microsoft.com/windows-hardware/drivers/kernel/handling-an-irp-mn-surprise-removal-request) 
 [使用验证和代码分析工具分析驱动程序](https://docs.microsoft.com/windows-hardware/drivers) 
 [**irp \_ MN \_ 意外 \_ 删除**](https://docs.microsoft.com/windows-hardware/drivers/kernel/irp-mn-surprise-removal) 
 [**IRP \_ MN \_ 删除 \_ 设备**](https://docs.microsoft.com/windows-hardware/drivers/kernel/irp-mn-remove-device)
 

 





