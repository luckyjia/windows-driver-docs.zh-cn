---
title: 对象引用跟踪
description: 对象引用跟踪
ms.assetid: b5af0ab0-954b-4da1-a074-df88d2d039f8
keywords:
- 对象引用跟踪
- 对象引用跟踪概述
- GFlags、 对象引用跟踪
ms.date: 05/23/2017
ms.localizationpriority: medium
ms.openlocfilehash: b9a5d24abbcafb770b7cee6f97ff9117c21592f8
ms.sourcegitcommit: 0cc5051945559a242d941a6f2799d161d8eba2a7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "63385041"
---
# <a name="object-reference-tracing"></a>对象引用跟踪


**对象引用跟踪**功能记录每个时间对象引用计数器即会递增或递减的顺序的堆栈跟踪。 跟踪可以帮助你检测对象引用错误，包括双取消引用、 失败，若要引用和失败，若要取消引用的对象。 仅在 Windows Vista 和更高版本的 Windows 中支持此功能。

璝惠砞对象引用跟踪中的功能**全局标志**对话框中，请参阅[配置对象引用跟踪](configuring-object-reference-tracing.md)。 有关在命令提示符下配置的对象引用跟踪功能的信息，请参阅[ **GFlags 命令**](gflags-commands.md)。 有关示例，请参阅[示例 15:使用对象引用跟踪](example-15--using-object-reference-tracing.md)。

对象引用跟踪都最为有用的如果您担心未引用特定对象或甚至是取消引用正确，通常因为池增加的使用率，则表明正在泄漏对象，或无法结束进程或会话，但其句柄计数为零。 与中供以后查看的日志记录的跟踪，不同对象引用跟踪专门设计用来在真实时间中时进程正在运行，而且该对象正在引用和取消引用。 通过在调试器中查看的对象引用跟踪[ **！ obtrace 调试器扩展**](-obtrace.md)。 由于此扩展需要一个指定的对象地址，您必须事先知道哪些对象是错误的可能的原因。

以下规则适用于对象引用跟踪：

-   可以一次运行只有一个对象引用跟踪。

-   由于内核级跟踪不可行，必须限制跟踪对对象使用指定的池标记创建的或由指定的进程 （指示的图像文件名称），或同时创建的对象。

-   可以指定只有一个图像文件，为每个跟踪。 如果指定的图像文件，跟踪仅限于创建的映像表示的进程对象。 不跟踪所引用的过程中，但由不同的过程中，创建对象的情况。

-   您可以指定最多为 16 池标记为每个跟踪。 跟踪与任何指定的池标记的对象。

-   如果指定一个图像文件和一个或多个池标记时，跟踪仅限于由过程创建和具有任何指定的池标记的对象。

-   对象引用跟踪无法跟踪已在运行时跟踪已启动的进程。 跟踪包括只跟踪开始后启动的进程的对象。

-   直到销毁对象或已禁用跟踪，跟踪已标记为要跟踪的对象。 默认情况下，对象被销毁，但您可以指定"永久性"跟踪之前，仅保留对象的跟踪 (**/p**) 跟踪保留在那里，直到禁用跟踪。

-   可以将对象引用跟踪配置存储为注册表设置或内核标志 （运行） 设置。 如果你使用注册表和内核标志设置，运行时设置优先，但关闭或重新启动计算机时都将丢失。

 

 





