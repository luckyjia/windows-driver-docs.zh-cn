---
title: 了解 TYMED
description: 了解 TYMED
ms.assetid: 36110923-c346-4367-8b7d-ef4d003ed88c
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: 5e9fdba50a40960fc459ae0479b275c870d7e2a1
ms.sourcegitcommit: fb7d95c7a5d47860918cd3602efdd33b69dcf2da
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/25/2019
ms.locfileid: "67358205"
---
# <a name="understanding-tymed"></a>了解 TYMED





TYMED 指定数据传输的类型。 此成员的值派生自[ **WIA\_IPA\_TYMED** ](https://docs.microsoft.com/windows-hardware/drivers/image/wia-ipa-tymed)常见项属性。 指定的数据复制可能会内存回调传输或文件传输。 请参阅有关 TYMED 的详细信息的 Microsoft Windows SDK 文档\_XXX 常量。

### <a name="file-transfer-tymed"></a>文件传输 TYMED

文件传输，使用以下值：

<a href="" id="tymed-file"></a>TYMED\_文件  
指示一个文件包含的单一映像。

<a href="" id="tymed-multipage-file"></a>TYMED\_多页\_文件  
表示一个包含多个映像，如多页 TIF 和类似格式的文件。 这主要用于文档送纸器获取。

### <a name="memory-transfer-tymed"></a>内存传输 TYMED

内存传输使用以下值：

<a href="" id="tymed-callback"></a>TYMED\_回调  
指示一个缓冲区，其中包含的单一映像或分隔的多个映像 IT\_MSG\_新建\_页消息。

<a href="" id="tymed-multipage-callback"></a>TYMED\_多页\_回调  
指示一个缓冲区，其中包含由分隔的多个映像 IT\_MSG\_新建\_页消息。 这会导致包含多个映像的单个文件。 这主要用于文档送纸器获取。

 

 




