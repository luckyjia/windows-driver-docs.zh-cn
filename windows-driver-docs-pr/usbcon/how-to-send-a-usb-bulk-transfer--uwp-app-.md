---
Description: 了解有关 USB 大容量传输以及如何启动 UWP 应用中所使用的 USB 设备进行通信的传输请求。
title: 如何将发送 USB 大容量传输请求（UWP 应用）
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: 88c294772aa685d17a97cfdd09d2e43b290d001f
ms.sourcegitcommit: fb7d95c7a5d47860918cd3602efdd33b69dcf2da
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/25/2019
ms.locfileid: "67363891"
---
# <a name="how-to-send-a-usb-bulk-transfer-request-uwp-app"></a>如何将发送 USB 大容量传输请求（UWP 应用）

在本主题中，您将了解 USB 大容量传输，以及如何启动 UWP 应用中所使用的 USB 设备进行通信的传输请求。

USB 全速、 高速度、 和 SuperSpeed 设备可以支持大容量终结点。 这些终结点用于传输传输大量的数据，如传输或 USB 闪存驱动器中的数据。 大容量传输不可靠，因为它们允许错误检测，且涉及数量有限的重试次数，以确保由主机或设备接收的数据。 大容量传输用于不是时间关键的数据。 仅当有时未使用的带宽可用总线上传输数据。 因此，当在总线正忙于处理其他传输，大容量数据可以无限期等待。

是单向的大容量终结点和数据可以是中一次传输，传输 IN 或 OUT 方向。 若要支持读取和写入的大容量数据，设备必须支持大容量 IN 和 OUT 终结点的大容量。 大容量 IN 终结点用于读取数据从设备复制到的主机和输出终结点的大容量用于将数据从主机到设备发送。

若要启动的大容量传输请求，您的应用程序必须具有对引用*管道*表示终结点。 管道已打开的设备驱动程序时配置该设备的通信通道。 对于应用程序中，管道是一个终结点的逻辑表示形式。 若要从终结点读取数据，应用程序，请从关联的大容量在管道中获取数据。 将数据写入到该终结点，应用将数据发送到管道出大容量。 大容量的读取和写入管道，请使用[ **UsbBulkInPipe** ](https://docs.microsoft.com/uwp/api/Windows.Devices.Usb.UsbBulkInPipe)并[ **UsbBulkOutPipe** ](https://docs.microsoft.com/uwp/api/Windows.Devices.Usb.UsbBulkOutPipe)类。

您的应用程序还可以通过设置某些策略标志来修改管道的行为。 例如对于读取请求，可以设置一个标志，在管道上的停止条件，会自动清除。 有关这些标志的信息，请参阅[ **UsbReadOptions** ](https://docs.microsoft.com/uwp/api/Windows.Devices.Usb.UsbReadOptions)并[ **UsbWriteOptions**](https://docs.microsoft.com/uwp/api/Windows.Devices.Usb.UsbWriteOptions)。

## <a name="before-you-start"></a>开始之前

* 则必须打开设备并获得[ **UsbDevice** ](https://docs.microsoft.com/uwp/api/Windows.Devices.Usb.UsbDevice)对象。 读取[如何连接到 USB 设备 （UWP 应用）](how-to-connect-to-a-usb-device--uwp-app-.md)。
* 您所见本主题中所示的完整代码[CustomUsbDeviceAccess 示例](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/CustomUsbDeviceAccess)，Scenario4\_BulkPipes 文件。

## <a name="step-1-get-the-bulk-pipe-object"></a>第 1 步：获取大容量的管道对象

若要启动传输请求，必须获取对大容量的管道对象的引用 ([**UsbBulkOutPipe** ](https://docs.microsoft.com/uwp/api/Windows.Devices.Usb.UsbBulkOutPipe)或[ **UsbBulkInPipe**](https://docs.microsoft.com/uwp/api/Windows.Devices.Usb.UsbBulkInPipe))。 通过枚举的所有接口的所有设置，可以获取管道。 但是，对于数据传输必须仅使用管道的活动设置。 如果管道对象为 null，如果关联的终结点不在活动的设置。

<table>
  <thead>
    <tr>
      <th>如果想要...</th>
      <th>使用此属性的值</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <tr>
      <td rowspan="5">将数据发送到大容量管道、 获取对的引用<a href="https://docs.microsoft.com/uwp/api/Windows.Devices.Usb.UsbBulkOutPipe"> <strong>UsbBulkOutPipe</strong></a>。</td>
      </tr>
      <tr>
      <td><a href="https://docs.microsoft.com/uwp/api/Windows.Devices.Usb.UsbInterface#Windows_Devices_Usb_UsbInterface_BulkOutPipes"><strong>UsbDevice.DefaultInterface.BulkOutPipes[n]</strong> </a>如果设备配置公开一个 USB 接口。</td>
      </tr>
      <tr>
      <td><a href="https://docs.microsoft.com/uwp/api/Windows.Devices.Usb.UsbInterface#Windows_Devices_Usb_UsbInterface_BulkOutPipes"><strong>UsbDevice.Configuration.UsbInterfaces[m]。[N] BulkOutPipes</strong></a>) 用于枚举出通过管道传入设备支持的多个接口的大容量。</td>
      </tr>
       <td><a href="https://docs.microsoft.com/uwp/api/Windows.Devices.Usb.UsbInterruptOutEndpointDescriptor#Windows_Devices_Usb_UsbInterruptOutEndpointDescriptor_Pipe"><strong>UsbInterface.InterfaceSettings\[m\]。BulkOutEndpoints [n]。管道</strong></a>用于枚举出管道由在接口中的设置定义大容量。</td>
      </tr>
      <tr>
      <td><a href="https://docs.microsoft.com/uwp/api/Windows.Devices.Usb.UsbInterruptOutEndpointDescriptor#Windows_Devices_Usb_UsbInterruptOutEndpointDescriptor_Pipe"><strong>UsbEndpointDescriptor.AsBulkOutEndpointDescriptor.Pipe</strong> </a>的输出终结点在大容量的终结点描述符，从中获取管道对象。
      </td>
      </tr>
    </tr>
    <tr>
      <tr>
        <td rowspan="5">从大容量管道接收数据，可以获取<a href="https://docs.microsoft.com/uwp/api/Windows.Devices.Usb.UsbBulkInPipe"> <strong>UsbBulkInPipe</strong> </a>对象</td>
      </tr>
       <tr>
        <td><a href="https://docs.microsoft.com/uwp/api/Windows.Devices.Usb.UsbInterface#Windows_Devices_Usb_UsbInterface_BulkInPipes"><strong>UsbDevice.DefaultInterface.BulkInPipes[n]</strong> </a>如果设备配置公开一个 USB 接口。</td>
       </tr>
       <tr>
       <td><a href="https://docs.microsoft.com/uwp/api/Windows.Devices.Usb.UsbInterface#Windows_Devices_Usb_UsbInterface_BulkInPipes"><strong>UsbDevice.Configuration.UsbInterfaces[m]。[N] BulkInPipes</strong> </a>用于枚举大容量中通过管道传入设备支持的多个接口。</td>
       </tr>
       <tr>
       <td><a href="https://docs.microsoft.com/uwp/api/Windows.Devices.Usb.UsbBulkInEndpointDescriptor#Windows_Devices_Usb_UsbBulkInEndpointDescriptor_Pipe"><strong>UsbInterface.InterfaceSettings[m]。BulkInEndpoints [n]。管道</strong></a>用于枚举大容量在管道定义的接口中的设置。</td>
       </tr>
       <tr>
        <td><a href="https://docs.microsoft.com/uwp/api/Windows.Devices.Usb.UsbBulkInEndpointDescriptor#Windows_Devices_Usb_UsbBulkInEndpointDescriptor_Pipe"><strong>UsbEndpointDescriptor.AsBulkInEndpointDescriptor.Pipe</strong> </a>的大容量 IN 终结点的终结点描述符，从中获取管道对象。</td>
      </tr>
    </tr>
  </tbody>
</table>

注意： 应为活动设置中，或需要 null 检查。

## <a name="step-2-configure-the-bulk-pipe-optional"></a>步骤 2：配置大容量管道 （可选）

可以修改行为的读取或写入操作，通过检索到的大容量管道上设置某些标志。

对于从设备读取，设置[ **UsbBulkInPipe.ReadOptions** ](https://docs.microsoft.com/uwp/api/Windows.Devices.Usb.UsbBulkInPipe#Windows_Devices_Usb_UsbBulkInPipe_ReadOptions)属性中定义的值之一[ **UsbReadOptions**](https://docs.microsoft.com/uwp/api/Windows.Devices.Usb.UsbReadOptions)。 在撰写时的情况下设置[ **UsbBulkOutPipe.WriteOptions** ](https://docs.microsoft.com/uwp/api/Windows.Devices.Usb.UsbBulkOutPipe#Windows_Devices_Usb_UsbBulkOutPipe_WriteOptions)属性中定义的值之一**UsbWriteOptions**。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>如果想要...</th>
<th>设置此标志</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>自动清除终结点上的任何错误条件而无需停止数据流</p></td>
<td><strong>AutoClearStall</strong>
<p>有关详细信息，请参阅<a href="#clearing-stall-conditions">清除停滞条件</a>。 此标志适用于读取和写入传输。</p></td>
</tr>
<tr class="even">
<td><p>将多个读取的请求发送的最大效率。 通过绕过错误检查来提高性能。</p></td>
<td><strong>OverrideAutomaticBufferManagement</strong>
<p>数据请求可以分为一个或多个传输，其中每次传输都包含一定数量的调用的字节数<em>最大传输大小</em>。 对于多个传输模式，由于驱动程序执行错误检查队列的两个传输中可能会有延迟。 此标志会跳过该错误检查。 若要获得最大传输大小，请使用<a href="https://docs.microsoft.com/uwp/api/Windows.Devices.Usb.UsbBulkInPipe#Windows_Devices_Usb_UsbBulkInPipe_MaxTransferSizeBytes" data-raw-source="[&lt;strong&gt;UsbBulkInPipe.MaxTransferSizeBytes&lt;/strong&gt;](https://docs.microsoft.com/uwp/api/Windows.Devices.Usb.UsbBulkInPipe#Windows_Devices_Usb_UsbBulkInPipe_MaxTransferSizeBytes)"> <strong>UsbBulkInPipe.MaxTransferSizeBytes</strong> </a>属性。 如果你请求的大小<strong>UsbBulkInPipe.MaxTransferSizeBytes</strong>，必须设置此标志。 注意：</p>
<p></p>
<div class="alert">
<strong>重要须知</strong><br/><p>如果设置此标志，则必须请求中的管道的最大数据包大小倍数的数据。 该信息存储在终结点描述符。 大小取决于设备的总线速度。 有关完整的速度、 高速度、 和 SuperSpeed;最大数据包大小分别为 64，512 和 1024 个字节。 若要获取该值，请使用<a href="https://docs.microsoft.com/uwp/api/Windows.Devices.Usb.UsbBulkInEndpointDescriptor#Windows_Devices_Usb_UsbBulkInEndpointDescriptor_MaxPacketSize" data-raw-source="[&lt;strong&gt;UsbBulkInPipe.EndpointDescriptor.MaxPacketSize&lt;/strong&gt;](https://docs.microsoft.com/uwp/api/Windows.Devices.Usb.UsbBulkInEndpointDescriptor#Windows_Devices_Usb_UsbBulkInEndpointDescriptor_MaxPacketSize)"> <strong>UsbBulkInPipe.EndpointDescriptor.MaxPacketSize</strong> </a>属性。</p>
</div>
<div>

</div>
此标志仅适用于读取传输。</td>
</tr>
<tr class="odd">
<td><p>终止一个长度为零的数据包的写入请求</p></td>
<td><strong>ShortPacketTerminate</strong>
<p>发送一个零长度包以指示外传输的结尾。此标志仅适用于编写传输。</p></td>
</tr>
<tr class="even">
<td><p>禁用读取短数据包 （小于最大数据包大小支持的终结点）</p></td>
<td><strong>IgnoreShortPacket</strong>
<p>默认情况下，如果设备发送的字节数小于最大数据包大小，该应用程序接收它们。 如果您不想要接收简短的数据包，设置此标志。</p>
<p>此标志仅适用于读取传输。</p></td>
</tr>
</tbody>
</table>

## <a name="step-3-set-up-the-data-stream"></a>步骤 3:设置数据流

由设备发送大容量数据，如大容量管道上的输入流中所示收到数据。 下面是获取输入的流的步骤：

1. 获取通过获取对输入流的引用[ **UsbBulkInPipe.InputStream** ](https://docs.microsoft.com/uwp/api/Windows.Devices.Usb.UsbBulkInPipe#Windows_Devices_Usb_UsbBulkInPipe_InputStream)属性。
2. 创建[ **DataReader** ](https://docs.microsoft.com/uwp/api/Windows.Storage.Streams.DataReader)对象指定输入的流中[ **DataReader 构造函数**](https://docs.microsoft.com/uwp/api/Windows.Storage.Streams.DataReader#Windows_Storage_Streams_DataReader__ctor_Windows_Storage_Streams_IInputStream_)。

若要将数据写入到设备，应用必须在大容量管道上写入到输出流。 以下是准备的输出流的步骤：

1. 通过获取获取到输出流的引用[ **UsbBulkOutPipe.OutputStream** ](https://docs.microsoft.com/uwp/api/Windows.Devices.Usb.UsbBulkOutPipe#Windows_Devices_Usb_UsbBulkOutPipe_OutputStream)属性。
2. 创建[ **DataWriter** ](https://docs.microsoft.com/uwp/api/Windows.Storage.Streams.DataWriter)对象指定输出流中的[ **DataWriter** ](https://docs.microsoft.com/uwp/api/Windows.Storage.Streams.DataWriter#Windows_Storage_Streams_DataWriter__ctor_Windows_Storage_Streams_IOutputStream_)构造函数。
3. 填充与输出流关联的数据缓冲区。
4. 具体取决于数据类型，传输将数据写入到输出流通过调用[ **DataWriter 方法**](https://docs.microsoft.com/uwp/api/Windows.Storage.Streams.DataWriter#Windows_Storage_Streams_DataWriter__ctor_Windows_Storage_Streams_IOutputStream_)，如[ **WriteBytes**](https://docs.microsoft.com/uwp/api/Windows.Storage.Streams.DataWriter#Windows_Storage_Streams_DataWriter_WriteBytes_System_Byte___)。

## <a name="step-4-start-an-asynchronous-transfer-operation"></a>步骤 4：启动异步传输操作

大容量传输都是通过异步操作启动。

若要读取大容量数据，开始一个异步读的操作通过调用[ **DataReader.LoadAsync**](https://docs.microsoft.com/uwp/api/Windows.Storage.Streams.DataReader#Windows_Storage_Streams_DataReader_LoadAsync_System_UInt32_)。

若要编写大容量数据，开始异步写操作，通过调用[ **DataWriter.StoreAsync**](https://docs.microsoft.com/uwp/api/Windows.Storage.Streams.DataWriter#Windows_Storage_Streams_DataWriter_StoreAsync)。

## <a name="step-5-get-results-of-the-read-transfer-operation"></a>步骤 5：获取读取的传输操作的结果

异步数据操作完成后，可以获取读取或写入从任务对象的字节数。 对于读取操作，调用[ **DataReader 方法**](https://docs.microsoft.com/uwp/api/Windows.Storage.Streams.DataReader)，如[ **ReadBytes**](https://docs.microsoft.com/uwp/api/Windows.Storage.Streams.DataReader#Windows_Storage_Streams_DataReader_ReadBytes_System_Byte___)，以从输入流读取数据。

## <a name="clearing-stall-conditions"></a>清除停滞条件

有时，应用程序可能会遇到失败的数据传输。 故障的转移可能导致在终结点上的停止条件。 只要终结点已停止，不能写入或读取数据。 若要继续与数据传输，应用必须清除关联管道上的停止条件。

您的应用程序可以配置要自动清除停滞情况发生时的管道。 若要执行此操作，设置[ **UsbBulkInPipe.ReadOptions** ](https://docs.microsoft.com/uwp/api/Windows.Devices.Usb.UsbBulkInPipe#Windows_Devices_Usb_UsbBulkInPipe_ReadOptions)属性设置为**UsbReadOptions.AutoClearStall**或者[ **UsbBulkOutPipe.WriteOptions** ](https://docs.microsoft.com/uwp/api/Windows.Devices.Usb.UsbBulkOutPipe#Windows_Devices_Usb_UsbBulkOutPipe_WriteOptions)属性设置为**UsbWriteOptions.AutoClearStall**。 使用该自动配置时，应用程序不会遇到失败的传输和数据传输体验是无缝。

若要手动清除停滞条件，请调用[ **UsbBulkInPipe.ClearStallAsync** ](https://docs.microsoft.com/uwp/api/Windows.Devices.Usb.UsbInterruptInPipe#Windows_Devices_Usb_UsbInterruptInPipe_ClearStallAsync)为大容量中通过管道传递; 调用[ **UsbBulkOutPipe.ClearStallAsync** ](https://docs.microsoft.com/uwp/api/Windows.Devices.Usb.UsbBulkOutPipe#Windows_Devices_Usb_UsbBulkOutPipe_ClearStallAsync)对于管道出大容量。

**请注意**停滞条件并不表示空的终结点。 如果终结点中没有数据，在传输完成，但长度为零字节。

对于读取操作，可能需要在开始新的转移请求之前清除挂起的管道中的数据。 若要执行此操作，调用[ **UsbBulkInPipe.FlushBuffer** ](https://docs.microsoft.com/previous-versions/windows/hardware/network/ff551975(v=vs.85))方法。

## <a name="usb-bulk-transfer-code-example"></a>USB 大容量传输的代码示例

此代码示例演示如何向管道写入的大容量。 该示例将数据发送到 OUT 上的默认接口的管道的第一个大容量。 它会配置管道以将长度为零的数据包传输结束时发送。 传输完成后，显示的字节数。

```CSharp
    private async void BulkWrite()
    {
        String dataBuffer = "Hello World!";
        UInt32 bytesWritten = 0;

        UsbBulkOutPipe writePipe = usbDevice.DefaultInterface.BulkOutPipes[0];
        writePipe.WriteOptions |= UsbWriteOptions.ShortPacketTerminate;

        var stream = writePipe.OutputStream;

        DataWriter writer = new DataWriter(stream);

        writer.WriteString(dataBuffer);

        try
        {
            bytesWritten = await writer.StoreAsync();
        }
        catch (Exception exception)
        {
            ShowStatus(exception.Message.ToString());
        }
        finally
        {
            ShowStatus("Data written: " + bytesWritten + " bytes.");
        }
    }
```

此代码示例演示如何从管道读取的大容量。 该示例从第一个大容量在管道上的默认接口检索数据。 它配置为最大限度提高到管道，并接收的最大数据包大小的区块中的数据。 传输完成后，显示的字节数。

```CSharp
    private async void BulkRead()
    {
        UInt32 bytesRead = 0;

        UsbBulkInPipe readPipe = usbDevice.DefaultInterface.BulkInPipes[0];
        readPipe.ReadOptions |= UsbReadOptions.IgnoreShortPacket;

        var stream = readPipe.InputStream;
        DataReader reader = new DataReader(stream);

        try
        {
            bytesRead = await reader.LoadAsync(readPipe.EndpointDescriptor.MaxPacketSize);
        }
        catch (Exception exception)
        {
            ShowStatus(exception.Message.ToString());
        }
        finally
        {
            ShowStatus("Number of bytes: " + bytesRead);

            IBuffer buffer = reader.ReadBuffer(bytesRead);

            ShowData (buffer.ToString());

        }
    }
```
