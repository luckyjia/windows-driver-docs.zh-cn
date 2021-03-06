---
title: WIA 项标志
description: WIA 项标志
ms.assetid: 2b96bc23-705b-47f0-811c-1cb4a8be8b34
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: c1cd223387112c94ef6e661e640969fce2cb0499
ms.sourcegitcommit: fb7d95c7a5d47860918cd3602efdd33b69dcf2da
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/25/2019
ms.locfileid: "67383068"
---
# <a name="wia-item-flags"></a>WIA 项标志





本主题适用于 Windows Vista 和更高版本。

WIA 项标志用于帮助对内容进行分类，或支持特定的 WIA 选项的行为。 WIA 项标志划分为两个基本组：

<a href="" id="item-status-flags"></a>项状态标志  
报告 WIA 项的当前状态的标志。

例如：**WiaItemTypeDisconnected**， **WiaItemTypeDeleted**，等等。

<a href="" id="item-data-representation-usage-flags"></a>项的数据表示形式/使用情况标记  
报告 WIA 项表示，或如果传输可能会产生的数据的标志。

例如：**WiaItemTypeImage**是数据表示形式标志，用于指示与当前的 WIA 项关联的数据的应用程序是图像数据，因此应具有图像数据属性。 **WiaItemTypeProgrammableDataSource**是告诉应用程序将 WIA 项是可配置，遵循一组预定义的配置规则根据项用法标志[ **WIA\_IPA\_项\_类别**](https://docs.microsoft.com/windows-hardware/drivers/image/wia-ipa-item-category)，并配置可能是可以为每次数据传输更改的结果。 请参阅[WIA 项类别](wia-item-categories.md)类别定义有关详细信息。

WIA 项标志及其定义的完整列表请参阅[ **WIA\_IPA\_项\_标志**](https://docs.microsoft.com/windows-hardware/drivers/image/wia-ipa-item-flags)。

 

 




