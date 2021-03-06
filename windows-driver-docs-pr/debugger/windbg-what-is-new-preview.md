---
title: WinDbg 预览版 - 新增功能
description: 本主题提供有关 WinDbg 预览调试器的新增功能的 inofmration。
ms.date: 07/02/2020
ms.topic: article
ms.prod: windows-hardware
ms.technology: windows-devices
ms.localizationpriority: medium
ms.openlocfilehash: cad1e49a7da21301b0faaa98d4d4072d22154050
ms.sourcegitcommit: f788aa204a3923f9023d8690488459a4d9bc2495
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/08/2020
ms.locfileid: "86141301"
---
# <a name="windbg-preview---whats-new"></a>WinDbg 预览版 - 新增功能

![windbg 预览版上的小徽标](images/windbgx-preview-logo.png)

本主题提供有关 WinDbg 预览调试器中的新增功能的信息。

## <a name="10200701003"></a>1.0.2007.01003

**时间线书签**

在 WinDbg 将重要的时间旅行位置做成书签，而不是手动将位置粘贴到记事本。 使用书签，可以更轻松地查看相对于其他事件的跟踪中的不同位置，并为其添加批注。 

可以为书签提供描述性名称。

![显示问候语应用中第一个 api 调用的示例名称的 "新建书签" 对话框](images/windbgx-timeline-bookmark-new.png)

通过 *> 时间线视图*中提供的 "时间线" 窗口访问书签。 当您将鼠标悬停在某个书签上方时，它将显示书签名称。

![显示在一个显示书签名称的书签上方的三个书签的时间线](images/windbgx-timeline-bookmarks.png)

您可以右键单击书签以到达该位置，重命名或删除书签。

![书签右键单击显示旅行以定位编辑和删除的弹出菜单](images/windbgx-timeline-bookmark-edit.png)

**模块窗口**

新的 windows 会显示模块及其相关信息，可以通过 "视图" 功能区获得。
其中显示：

- 包含路径位置的模块的名称
- 加载的模块的大小（以字节为单位）
- 加载模块的基址
- 文件版本

![显示了五个模块的 "模块" 视图窗口](images/windbgx-view-modules.png)


**实时调试中提供的线程名称/说明**

当执行实时用户模式调试时，从 SetThreadDescription 设置的线程名称现在可用。 线程名称可使用 "~" 命令或调试器数据模型。

```dbgconsole
0:000> ~
   0  Id: 53a0.5ffc Suspend: 1 Teb: 000000b1`db1ed000 Unfrozen "Hello world!"
   7  Id: 53a0.9114 Suspend: 1 Teb: 000000b1`db1ef000 Unfrozen
   8  Id: 53a0.2cc4 Suspend: 1 Teb: 000000b1`db1f1000 Unfrozen
   9  Id: 53a0.5c40 Suspend: 1 Teb: 000000b1`db1f3000 Unfrozen

0:000> dx @$curthread
@$curthread                 : ConsoleTestApp!ILT+25(mainCRTStartup) (00007ff7`fac7101e)  [Switch To]
    Id               : 0x5ffc
    Name             : Hello world!
    Stack
    Registers
    Environment
```

**便携 PDB 支持**

添加了便携 PDB 支持。 可移植 PDB （程序数据库）格式描述由公共语言基础结构（CLI）语言的编译器生成的调试信息的编码，并由调试器和其他工具使用。 有关详细信息，请参阅[可移植 PDB v1.0：格式规范](https://github.com/dotnet/corefx/blob/master/src/System.Reflection.Metadata/specs/PortablePdb-Metadata.md)。


**其他更改和 bug 修补程序**

- WinDbg 现在支持 AMD64 和 Linux 内核转储调试。
- 旅行记录增强功能和其他修补程序。

## <a name="10191211001"></a>1.0.1912.11001

**TTD 时间线**-我们添加了一个新窗口，该窗口显示跟踪中重要事件的可视化表示形式：异常、断点、函数调用和内存访问。 时间线将自动打开并显示异常（如果存在）和断点。 有关详细信息，请参阅[WinDbg 预览-时间线](windbg-timeline-preview.md)。

**切换到默认窗口镶边**-我们使用的自定义窗口 chrome，尽管外观会导致某些规模的用户缩放并调整其大小，因此我们已选择在此时间删除它。

"**文件" 菜单改善了键盘导航**-"文件" 菜单现在更易于只使用键盘进行导航。

**其他更改和 bug 修补程序**

* 当目标正在运行时，"堆栈" 和 "局部变量" 窗口将处于禁用状态，并且不会在没有目标时显示 "未指定的错误"。
* 向附加对话框添加了 "服务" 列，以便轻松地查找正在运行的服务。
* 修复了在使用参数启动应用程序时导致体系结构检测不起作用的 bug。
* 在加载私有符号时，"反汇编" 窗口已改进了反汇编。
* 现在会自动加载 jsprovider.dll，因此我们从脚本功能区删除了 "Load JSProvider" 按钮。

## <a name="10190830002"></a>1.0.1908.30002

**对 TTD 的改进调用对象**  - [调用查询](https://docs.microsoft.com/windows-hardware/drivers/debugger/time-travel-debugging-calls-objects)现在包括参数名称、类型和值。 当跨函数调用的跟踪进行查询时，可以获取完全类型的参数及其值，以便于按参数对结果进行筛选。

**支持 Open Enclave** -WinDbg 预览版现在可以调试打开的 ENCLAVE （OE）应用程序，你可以在[打开的 Enclave 文档](https://github.com/openenclave/openenclave/blob/master/docs/GettingStartedDocs/Windows_windbg.md)中找到如何执行此操作的说明。

**VS Code 扩展**-为了更轻松地为开放式 Enclave 进行开发，我们发布了一个基本的 VS Code 扩展，以实现更快的内部循环。 "变量"、"监视" 和 "调用堆栈" 窗口所有工作以及断点和源窗口，任何更深入的调试都需要使用控制台窗口。
 
可以在[VS Code Marketplace](https://aka.ms/CDBVSCode)中找到该扩展，并向我们的[WinDbg 反馈 GitHub](https://aka.ms/dexex)报告任何问题。 请注意，虽然扩展可能适用于其他方案，但我们只是在此时解决与 OE 方案相关的问题。

**ELF 核心转储**-作为支持的开放 Enclave 的一部分，WinDbg 可以从 DWARF 和 Linux 应用程序打开 ELF Core 转储和二进制文件（目前不支持 Enclaves 5）。 当从非 Windows 应用程序打开核心转储时，基本窗口和命令都应正常运行，但大多数扩展和 Windows 特定的命令将不起作用。 按照[此处定义的关键约定](https://github.com/dotnet/symstore/blob/master/docs/specs/SSQP_Key_Conventions.md)，将从符号服务器下载 ELF 和 DWARF 文件。 Enclaves 是唯一受支持的方案，但我们在打开其他 Linux core 转储时提供反馈。

**TTD 文件格式更改**-对于中断向前兼容性的 TTD 跟踪，我们已对文件格式进行了重大更新。 以前版本的 WinDbg Preview 将无法打开此（以及将来）版本的 WinDbg Preview 记录的跟踪，但此（和更未来）版本将能够打开新的和旧的跟踪。

**其他更改**

* TTD 现在将使用64位引擎进行索引编制，并使用相应的调试器引擎位重放来最大程度地减少在重播时索引和 SOS 问题时可能出现的内存问题。
* 在没有任何参数的情况下运行 "dx" 现在会显示根命名空间，以便更轻松 browsability。
* 现在可以通过 "设置" 菜单修改默认符号和源缓存位置。
* 改善了对录制 AVX-512 的支持（AVX-512 的记录将导致比正常的慢）。
* 已启用[脱机许可](https://docs.microsoft.com/windows/uwp/publish/organizational-licensing#allowing-disconnected-offline-licensing)。

## <a name="10190512001"></a>1.0.1905.12001

**对 SymSetDiaSession 错误缓解功能的改进**-我们的第一个月修复了此错误，以减少在某些情况下将 dbghelp.dll 注入到进程中的应用程序造成的错误。 我们已对其进行了改进，并将继续监视有关此错误的反馈。

**自定义颜色自定义**-很多情况下都需要使用 WinDbg 的几个实例，在这两个实例之间来回移动可能会造成混淆，并花一些时间来找出哪一项是 "右"。 我们添加了更改蓝色强调颜色的功能，以帮助用户直观地区分会话，并使它们之间的交换变得更容易。

只需单击 "**视图**" 功能区，然后在上一节中选择 "**强调色**" 选项。 从最近的目标启动未来的会话时，将在目标工作区中保留着色颜色。

**源词汇切分改进**-源窗口现在具有对词汇切分 Rust 源文件和 c + + SEH __try/__except/__finally/__leave 的基本支持。

**协同程序改进**-改进了对协同程序局部变量和某些优化变量的支持。

**默认符号和源缓存设置**-将选项添加到 "**调试设置**" 下的 "设置" 菜单，以更改符号的缓存位置。 **注意**-有一个已知问题，此问题会导致源加载失败。 我们将添加验证，以防止此情况在未来版本中发生。

**-pv fix** -修复了在某些情况下可能阻止的 bug （pv （非侵害性连接）。

## <a name="10190418001"></a>1.0.1904.18001

**修复 SymSetDiaSession 错误**-我们有一段时间的报告，此错误会阻止在某些情况下启动 WinDbg Preview。 在加载某个版本的 Dbghelp.dll 之前，有几个外部应用程序会尝试将该版本注入到我们的进程中。 其中一些用户使用的是具有缺少的功能的 Dbghelp.dll 版本，在我们尝试使用这些功能时会导致此错误。 我们为此添加了修复程序，如果仍出现此问题，则会进行跟踪。

**字体控件**-我们添加了用于控制字体和字体大小的设置。 有两个不同的设置，一个用于文本窗口（如 "反汇编"、"源"、"命令" 等），另一个用于工具窗口（局部变量、堆栈等）。 还有几个区域不受这些选项的影响，这些选项将在将来更新。

**突出显示改进**-"命令" 窗口中的文本持久突出显示现在也会在 "源" 和 "备注" 窗口中突出显示文本。

**源加载改进**-我们已更改加载源文件工作的方式。 以前在打开源文件时，无法运行或无法预测的引擎操作，如运行其他命令。 我们更改了加载的位置，以实现更好的并行，并更可靠地取消源打开操作。

其他更改和 bug 修复：

* 已将 "转向反汇编" 添加到源窗口的上下文菜单中。
* 在 "反汇编" 窗口中添加了 "跟踪当前指令" 的复选框。
* 修复了一个 bug，该 bug 导致命令窗口在输出大量文本时执行缓慢。
* 更改了 page up 和 page down 键，使其类似于 Visual Studio。
* 当 ASM 文件在源窗口中打开时，它现在将包含基本注释、字符串和指令突出显示


## <a name="10181212001"></a>1.0.1812.12001

此版本包含这些更新。

**调试器数据模型 c + + 标头**-有一个新的 c + + 标头 DbgModel，作为 Windows SDK 的一部分包含，用于通过 c + + 扩展调试器数据模型。 有关详细信息，请查看[调试器数据模型 c + + 概述](https://docs.microsoft.com/windows-hardware/drivers/debugger/data-model-cpp-overview)。 此版本包含一个新扩展，它向调试器数据模型添加一些更多 "API 样式" 功能，可通过 "dx" 命令、JavaScript 和新的 DbgModel 标头进行访问。 此扩展插件将数据模型扩展为包含有关通过[调试](https://docs.microsoft.com/windows-hardware/drivers/debugger/dbgmodel-namespace-code)程序中的程序集和代码执行的知识，并通过调试程序. [FileSystem 命名](https://docs.microsoft.com/windows-hardware/drivers/debugger/dbgmodel-namespace-file-system)空间和本地文件系统。

**合成类型扩展**使用这一新的 API 扩展，我们在 GitHub 存储库中提供了一个新示例 https://github.com/Microsoft/WinDbg-Samples/tree/master/SyntheticTypes 。 此 JavaScript 扩展读取基本 C 头文件，并定义标头中定义的结构和联合的综合类型信息。 然后，可以通过 dx 命令查看内存结构，就像您有一个具有这些类型的类型信息的 PDB 一样。

其他更改和 bug 修复：

- 在单步执行时，WinDbg Preview 现在将更智能地处理将源窗口或 "反汇编" 窗口引入前台。
- 重新排列 WinDbgNext 的窗口标题，以便在启动内核调试时获得更重要的信息。
- "命令" 窗口中的 "交替背景对比度" 应该稍微明显一些。

## <a name="1018102001"></a>1.0.1810.2001

此版本包含这些更新。

- 可从 "文件" 菜单或 Home 功能区访问的 "新建设置" 对话框。 
- "事件和异常设置" 对话框。 此菜单更改调试器处理事件和异常的方式，等效于 "sx" 命令或 WinDbg 的事件筛选器对话框。 选择 "主页" 功能区上的 "设置"，然后点击左侧的 "事件和异常" 来管理这些**设置**。
- 提高了 TTD 索引器的性能。 这会提高索引 TTD 跟踪文件的性能，使索引过程的速度快得多（在2倍之间），同时使索引文件更小（约50%）。 对于大小超过4GB 的跟踪，或使用具有多个 CPU 核心（8 +）的计算机，性能改进最明显。 新的索引器使调试非常大的跟踪（50GB +）变得更可行。
- 用于指定体系结构的 New *debugArch*启动标志。 WinDbg 预览版尝试将具有正确位数的调试器引擎启动到目标，以更好地支持调试托管代码。 在某些情况下，它不能确定正确的位数，或者您可能想要重写它所决定的位数。 使用-debugArch x86 | amd64 控制调试器引擎的体系结构。

其他更改和 bug 修复：

-  修复了一个 bug，该 bug 会导致在打开浮动窗口的全屏调试器上出现黑色条。
-  修复了一个 bug，该 bug 会导致无意中清除符号选项。
-  从最近的目标启动时，命令历史记录现在会被保留。
-  在 "数据模型" 窗口中，您现在可以编辑值。
-  现在，未编制索引的 TTD 跟踪将更清楚地表明它们未编入索引。
-  提高了 "局部变量" 窗口的性能
-  添加了 "功能区" 按钮，用于将命令窗口日志保存到文件。
-  。 将 SelectMany （ <projection> ）设置为默认的 LINQ 方法集。

## <a name="10180711002"></a>1.0.1807.11002

此版本包含这些更新。

**自动保存和加载断点**。 这是替换工作区的第一步。 我们将通过启用断点的保存和加载来开始路由。 从 "文件" 菜单上的 "最近" 选项卡中启动以前调试过的内容后，将从该会话加载断点。 计划是扩展此功能，以便在多个会话中保留更多信息。 当前未保存针对断点（如线程和进程特定上下文以及条件）的硬件断点（ba）和其他各种属性。
 
少量更改和 bug 修复：

- 添加了命令行选项-x、-xe、-xd、-xn 和-xi，用于控制异常和事件的处理。 这些命令行选项的行为与它们的命令计数器部分的行为一样。
- 注释窗口现在支持粗体、下划线和斜体格式。
- 修复了一些缩放和滚动问题。
- 选择命令、内存、源或反汇编窗口中的文本后，将会突出显示选定文本的其他实例。
- 修复了在中断符号加载时导致符号加载失败的 bug，导致会话的其余部分失败。
- NatVis 现在会在重新启动会话时正确地重新加载。

## <a name="10180517002"></a>1.0.1805.17002

此版本包含这些更新。

**新**的 "反汇编" 窗口-"反汇编" 窗口现在包括：
- 如果可能，向上或向下滚动会持续加载更多的反汇编。
- 为数字、代码地址和操作码突出显示语法。
- 单击代码符号会将 "反汇编" 窗口跳转到该位置。
- 将鼠标悬停在数字上将显示将该数字转换为其他基的工具提示。
- 表示函数开头的标头。

**更快的源窗口**-已更新源窗口，以提高资源效率。

少量更改和 bug 修复：

- 修复了有关符号缓存的问题
- 解决了某些情况下，当目标未损坏时，切换初始中断不可用
- 如果在 "命令" 窗口中点击 "无" 选项卡，则光标将保留在输入字段中
- 在打开 CAB 文件时，WinDbgNext 将自动检测位数

## <a name="10180418003"></a>1.0.1804.18003

此版本包含这些更新。

**符号状态和取消改进**-在这种情况下，调试器会显示*繁忙*的加载符号，并且很难确定其执行的操作以及没有启用符号干扰的原因。 我们更新了 WinDbg 预览版，使其能够在加载符号时更好地通信，以帮助解决任何问题。
除了轻松查看发生的情况外，我们还进行了一些更改，使取消符号更可靠，并且 "日志" 窗口将包含在启用了！符号干扰的情况下通常会输出的一些详细信息。 如果点击了视图 > 日志，您将获得完全干扰的符号加载输出，而无需打开它并尝试重新加载符号。

"**试验性注释" 窗口**-WinDbg Preview 现在提供了一个用于记笔记的窗口。 只需点击视图 > "说明" 即可将其打开。 如果复制/粘贴到其中，将保留 DML 链接，但仍可像命令窗口一样工作。 当窗口处于打开状态时，还可以保存和加载 "注释" 功能区中的注释文件。 

**更快**的 "源" 窗口-为了帮助改善 WinDbg 预览版的性能，我们提供了一个更高效的试验性新源窗口。 上下文菜单和语法突出显示仍有一些缺口，但我们希望为每个人提供一种在完成前将其试用的选项，以向我们提供更早的反馈。 运行 $UseFastSourceWindow 以使用该方法。 如果要返回到旧版本，请运行 $UseMonacoSourceWindow。 此设置将在多个会话中保留，你需要关闭并重新打开源窗口才能获取新版本。

**JSPROVIDER api 版本 1.2** -适用于声明支持 API 版本1.2 的 JavaScript 扩展：

- 如果任何对象的 compareTo 方法退出脚本，则该对象的自定义比较运算符（比较运算符将在 DX 计算器和其他地方工作：例如： IModelObject：： Compare）
- 如果任何对象的. equals 方法退出脚本，则该对象的自定义相等运算符（= = 和！ = 将在 DX 计算器和其他地方工作：例如： IModelObject：： IsEqualTo）
- 输入脚本的本机或数据模型对象将对其使用 compareTo 和. equals，以允许访问任何自定义比较运算符或自定义相等实现。
 
少量更改和 bug 修复：

- 。服务器现在将列出完全限定的域名，以便在出现短名称的域问题时更便于使用。
- Ctrl + G 现在可在源窗口中工作。
- 已将地址栏添加到 "反汇编" 窗口。
- WinDbg Preview 现在会按预期方式处理 _NT_SYMBOL_PATH。
- 添加了-服务器命令行选项。
- TTD 数据模型查询现在可以渐进式显示，因此，如果您中断它，仍会看到一些结果。 此功能仍是实验性的，可选。 运行 `dx @$cursession.TTD.AsyncQueryEnabled = 1` 以启用它。
- "Dps" 命令现在包含指向它引用的源文件的链接。

## <a name="11801190010"></a>1.1801.19001.0

此版本包含这些更新。

**文本突出显示**-现在可以在调试器中直接突出显示所选文本的所有实例。 若要使用此功能，只需在命令窗口中选择一些文本，然后单击 "命令" 功能区中的 "突出显示" 或按 CTRL + ALT + H。 使用其中一个已突出显示的文本将删除突出显示内容。

如果更喜欢使用命令，可以使用 "$hl" 命令：

`$hl ["someValueHere"]`-突出显示 "给文本（或突出显示，如果已突出显示）"

`$hl clearAll`-清除所有突出显示的条目

`$hl caseSensitive [1|0]`-将突出显示匹配设置为区分大小写或不区分大小写（默认情况下不区分大小写）

此版本还包括一些次要 bug 修补程序。


## <a name="11712150030"></a>1.1712.15003.0

此版本包含这些更新。

**TTD 内存查询**-现在可以查询 TTD 的内存访问，就像现在查询调用的方式一样。 这允许你查找访问特定内存范围的所有读取、写入和执行操作。

读写示例：`dx @$cursession.TTD.Memory(startAddress, endAddress, "rw")`

唯一的执行示例：`dx @$cursession.TTD.Memory(startAddress, endAddress, "ec")`

**设置更改**-WinDbg Preview 现在会自动保存会话之间的设置，包括符号路径和源路径。

**JavaScript 改进**

- 64中的位数字和数值现在包含一个取模方法，该方法允许真正的64位取模运算。
- JavaScript 中定义的对象现在可以实现自定义可比较或可相等的概念，这些概念将使用标准 c + + 运算符或 LINQ 操作在 dx 中工作。 为了利用这一点，脚本必须在 initializeScript 数组中声明，该脚本通过插入记录 "new apiVersionSupport （1，2）" 来支持新版本的宿主 API。 完成后，可以在任意 "dx" 或数据模型窗口 LINQ 查询中使用这些函数。 如果该方法实现 compareTo （其他），则可比较（比较运算符在 dx 和 LINQ 中工作）。 如果该方法返回一个负值，如 "this < 其他"。 如果该方法返回零，则 "this = = other"。 如果该方法返回正值 "this > other"。 如果该方法实现. equals （其他），则它是可相等（= = 在 dx 和 LINQ 中起作用）。 方法必须返回 true 或 false。

少量更改和 bug 修复：

- 修复了在启动调试过程中堆栈和局部变量窗口无法工作的 bug
- 已更新 LM 的输出，更准确地报告 ProductVersion 和类似字段
- 在 TTD 会话期间启用 "单步执行" 按钮
- 添加了对-lsrcpath 的支持
- 向下滚动时，"局部变量"、"监视" 和 "模型" 窗口中的标头现在不会消失
- 当 ALT + Tab 键返回到 WinDbg Preview 时，命令窗口将正确保留光标位置
- 为切换详细模式添加了 CTRL + ALT + V 快捷方式
- 你现在可以通过右键单击 "命令窗口" 选项卡并选择 "关闭自动滚动" 来禁止自动滚动命令窗口
- 现在可通过 "启动可执行文件高级" 页调试子进程。


## <a name="10140"></a>1.0.14.0

此版本包含这些更新。

**改进了进程服务器体验**-"文件" 菜单中的新通知，用于显示你连接到的进程服务器并与之交互。 在这些更改过程中，当结束调试会话时，进程服务器连接将保留，并且可以在 "文件" 菜单中断开连接。

"**视图" 功能区中的新预设布局选项**-"视图" 功能区中有一个新的 "布局" 选项。 目前有三个布局：默认值，一个集中在反汇编上，一个最小。 

**旅行调试功能区**-在调试时间旅行调试跟踪时，有一个增强的时间段功能区将显示。

**Javascript 脚本中的元数据**-javascript 扩展现在可以返回属性和其他构造的元数据。 这意味着扩展可以提供帮助字符串、指示值的显示基数等。 通过在对象上放置元数据描述符来提供元数据，方法是使用 metadataDescriptor 或 defineMetadata 的显式调用。 函数返回值、迭代值和其他值上下文可以通过 valueWithMetadata 为其值返回元数据。

**JAVASCRIPT API 更新**-对 JavaScript 提供程序中的 api 进行了一些潜在的源级别重大更改（包括新的对本机对象的方法和属性）。 现有扩展将不会看到任何可能重大的更改，而不会指明它们是否支持新版本的 JsProvider API。 对于新的 API 版本，可通过将 apiVersionSupport 记录置于由 initializeScript 返回的支持版本1.1 的数组中来指示。 可能? .. 值为时，指示对版本1.1 的支持。

API 版本1.1 中的更改包括：

- getModuleSymbol 和 getModuleType 如果无法找到符号而不是引发异常，则返回 null。
- 除外，所有本机对象的 address 属性都是 targetLocation。 如果该对象没有地址，则在访问属性时将引发异常。
- 所有本机对象均对其使用 getObjectValue 和 setObjectValue 方法来访问对象上的属性，这可能与对象上的名称 JavaScript 位置（例如： ' address '）冲突。

**其他 JavaScript 更改**

- JavaScript 扩展现在可以通过 defineProperty 和 delete 运算符在数据模型对象上添加和移除属性。 将 JavaScript 类作为父模型或类型签名添加或注册仍是处理对象模型的首选方法。
- JavaScript 扩展现在可以通过新的 setModuleSymbol API 修改调试目标中的模块内的全局变量。
- 所有位于64位库类型上的数学函数（例如：. 加法、. 减法、. 乘法、除法等）现在也存在于 JavaScript 编号上。
- JavaScript 函数和属性现在可以返回通过自定义封送处理枚举的值。 函数或属性访问器可以返回 typeSystem （value，type ...），以便调用它此类自定义封送处理。
- 脚本调试器中的 "断点" 命令现在可以在函数名称和行/列位置之外进行中断。
- JavaScript 扩展中的类型对象可以通过 containingModule 属性访问其包含模块。

少量更改和 bug 修复：

- 更正了条件功能区选项卡的格式，使其变得更容易。
- 重新运行 DML 以更严格地进行分析以提高性能。
- 与 CTRL + F 的性能和行为的各种修复。
- 在尝试使用 TTD 之前，在运行未提升的状态时添加了警告。
- 添加了替代自动目标位数检测的选项。
- 禁用了不同的 "文件" 菜单和功能区选项（在转储文件中时为 "执行"）。

已知问题：
- SOS 在 x86 跟踪上不起作用。

## <a name="10130"></a>1.0.13.0

此版本添加了时间行程跟踪。 使用行程调试，可以记录进程，然后在以后向前和向后重播。 旅行调试（TTD）可让您通过 "倒带" 调试器会话来更轻松地调试问题，而无需在发现 bug 之前重现问题。 有关详细信息，请参阅[时间行程调试 - 概述](time-travel-debugging-overview.md)。

## <a name="10120"></a>1.0.12.0

此版本是 WinDbg Preview 的第一版。 有关 WinDbg Preview 中提供的功能的一般信息，请[使用 Windbg preview 进行调试](debugging-using-windbg-preview.md)。

## <a name="see-also"></a>另请参阅

[WinDbg 预览版–安装](windbg-install-preview.md)

[WinDbg 预览–命令行启动选项](windbg-command-line-preview.md)
