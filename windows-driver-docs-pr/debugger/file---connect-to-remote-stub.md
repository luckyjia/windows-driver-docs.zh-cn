---
title: 文件连接到远程存根 （stub）
description: 文件连接到远程存根 （stub）
ms.assetid: 7357db85-babe-4729-9a20-76ba284f5bf3
keywords:
- 文件连接到远程存根 （stub）
ms.date: 05/23/2017
ms.localizationpriority: medium
ms.openlocfilehash: 17ac4cddbd21738c868914217c85a5d422abccd7
ms.sourcegitcommit: 0cc5051945559a242d941a6f2799d161d8eba2a7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "63354909"
---
# <a name="file--connect-to-remote-stub"></a>文件 | 连接到远程存根


单击**连接到远程存根**上**文件**菜单使 WinDbg 智能客户端并连接到进程服务器或 KD 连接服务器。

此命令相当于使用用户模式或内核模式-k kdsrv 传输协议命令行选项中的-premote 命令行选项。 仅当 WinDbg 处于休眠模式时，可以使用此命令。

您不能使用此命令连接到调试服务器;为此，使用[文件 |连接到远程会话](file---connect-to-remote-session.md)相反。

### <a name="span-idconnecttoremotestubserverdialogboxspanspan-idconnecttoremotestubserverdialogboxspanconnect-to-remote-stub-server-dialog-box"></a><span id="connect_to_remote_stub_server_dialog_box"></span><span id="CONNECT_TO_REMOTE_STUB_SERVER_DIALOG_BOX"></span>连接到远程存根 （stub） 服务器对话框

当您单击**连接到远程存根**，则**连接到远程的存根 （stub） 服务器**对话框随即出现。 可以使用此对话框中，输入远程连接参数，或若要浏览的进程服务器和 KD 连接服务器的列表。

若要手动指定远程连接参数，请输入中的以下字符串之一**连接字符串**框：

```text
npipe:server=Server,pipe=PipeName[,password=Password] 

tcp:server=Server,port=Socket[,password=Password][,ipversion=6]

tcp:clicon=Server,port=Socket[,password=Password][,ipversion=6]

com:port=COMPort,baud=BaudRate,channel=COMChannel[,password=Password] 

spipe:proto=Protocol,{certuser=Cert|machuser=Cert},server=Server,pipe=PipeName[,password=Password] 

ssl:proto=Protocol,{certuser=Cert|machuser=Cert},server=Server,port=Socket[,password=Password]

ssl:proto=Protocol,{certuser=Cert|machuser=Cert},clicon=Server,port=Socket[,password=Password]
```

在前面的选项中的各种参数具有以下可能值：

<span id="Server"></span><span id="server"></span><span id="SERVER"></span>*Server*  
创建进程服务器或 KD 连接服务器的计算机的网络名称。 不要在前面加反斜杠此名称 (**\\\\**)。

<span id="PipeName"></span><span id="pipename"></span><span id="PIPENAME"></span>*PipeName*  
如果使用 NPIPE 或 SPIPE 协议*PipeName*是创建服务器时提供给管道的名称。

<span id="Socket"></span><span id="socket"></span><span id="SOCKET"></span>*Socket*  
如果使用 TCP 或 SSL 协议*套接字*是创建服务器时使用的同一套接字端口号。

<span id="COMPort"></span><span id="comport"></span><span id="COMPORT"></span>*COMPort*  
如果你使用 COM 协议*COMPort*指定要使用的 COM 端口。 "COM"前缀是可选的 （例如，"com2"和"2"正确无误）。

<span id="BaudRate"></span><span id="baudrate"></span><span id="BAUDRATE"></span>*BaudRate*  
如果你使用 COM 协议*BaudRate*应与您选择创建服务器时的波特率。

<span id="COMChannel"></span><span id="comchannel"></span><span id="COMCHANNEL"></span>*COMChannel*  
如果你使用 COM 协议*COMChannel*应匹配创建服务器时选择频道号。

<span id="Protocol"></span><span id="protocol"></span><span id="PROTOCOL"></span>*Protocol*  
(Windows 2000 及更高版本)如果使用 SSL 或 SPIPE 协议*协议*应与创建服务器时使用的安全协议。

<span id="Cert"></span><span id="cert"></span><span id="CERT"></span>*Cert*  
(Windows 2000 及更高版本)如果使用 SSL 或 SPIPE 协议，则应使用完全相同**certuser =**<em>Cert</em>或**machuser =**<em>Cert</em>已使用的参数创建服务器时。

<span id="clicon"></span><span id="CLICON"></span>**clicon**  
指定的进程服务器或 KD 连接服务器将尝试连接到客户端通过反向连接。 客户端必须使用**clicon**当且仅当服务器使用的**clicon**。 在大多数情况下，智能客户端启动服务器之前，使用反向连接时。

<span id="Password"></span><span id="password"></span><span id="PASSWORD"></span>*密码*  
如果创建服务器时使用一个密码，则必须提供*密码*创建智能客户端。 此值必须匹配的原始密码。 密码是区分大小写。 如果提供了错误的密码，则错误消息将指定"错误 0x80004005"。

<span id="ipversion_6"></span><span id="IPVERSION_6"></span>**ipversion=6**  
(调试工具的 Windows 6.6.07，之前仅)强制将 IP 版本 6 调试器而不是版本 4 使用 TCP 连接到 Internet 时。 在 Windows Vista 和更高版本中，调试器将尝试自动默认为 IP 版本 6，这使得此选项不必要。

而不是手动指定的远程连接参数，可以按**浏览**按钮**连接到远程的存根 （stub） 服务器**对话框，并使用**浏览远程服务器**对话框。

### <a name="span-idbrowseremoteserversdialogboxspanspan-idbrowseremoteserversdialogboxspanbrowse-remote-servers-dialog-box"></a><span id="browse_remote_servers_dialog_box"></span><span id="BROWSE_REMOTE_SERVERS_DIALOG_BOX"></span>远程服务器浏览对话框

在**浏览远程服务器**对话框中**机**文字框中，输入运行的进程服务器或 KD 连接服务器的计算机的名称。 (两个初始反斜杠是可选的："MyBox"和"\\\\MyBox"均正确。)然后，按**刷新**按钮。

**服务器**区域列出的所有进程服务器和该计算机运行的 KD 连接服务器。 选择任何列出的服务器，然后按 ENTER 或单击**确定**。 （您还可以双击一个列出的服务器。）现在将出现所选的进程服务器的正确的连接字符串**连接字符串**框中**连接到远程的存根 （stub） 服务器**对话框。

如果服务器是受密码保护，包括连接字符串**密码 =\\**<em>。必须将为星号 (</em>*\** *) 与实际密码。

指定服务器名和密码后，单击**确定**来打开连接。

中的服务器列表**浏览远程服务器**对话框还可以包括服务器不再存在，但未正确关闭。 如果您连接到这些不存在服务器之一，将收到一条错误消息。

服务器列表不包括调试服务器。 若要查看这些服务器，请使用[文件 |连接到远程会话](file---connect-to-remote-session.md)命令。

### <a name="span-idadditionalinformationspanspan-idadditionalinformationspanadditional-information"></a><span id="additional_information"></span><span id="ADDITIONAL_INFORMATION"></span>其他信息

有关详细信息和加入远程存根 （stub） 会话的其他方法，请参阅[**激活智能客户端**](activating-a-smart-client.md)并[**激活智能客户端 （内核模式）**](activating-a-smart-client--kernel-mode-.md).

 

 





