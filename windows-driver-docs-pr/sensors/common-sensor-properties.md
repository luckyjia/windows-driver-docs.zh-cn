---
title: 通用传感器属性
description: 本主题介绍所有传感器的常见传感器属性。
ms.assetid: 3E4DD221-BA8E-446E-BA7A-EF84DFED332F
ms.date: 01/04/2018
ms.localizationpriority: medium
ms.openlocfilehash: 654eac3d8f9e93c8d613bfd69a0304f8c3a97199
ms.sourcegitcommit: 4b7a6ac7c68e6ad6f27da5d1dc4deabd5d34b748
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2019
ms.locfileid: "72842529"
---
# <a name="common-sensor-properties"></a>通用传感器属性


本主题介绍所有传感器的常见传感器属性。

下表显示了常用属性。 有关 "类型" 列中显示的类型的详细信息，请参阅[PROPVARIANT 结构](https://go.microsoft.com/fwlink/p/?linkid=313395)。

<table>
<colgroup>
<col width="20%" />
<col width="20%" />
<col width="20%" />
<col width="20%" />
<col width="20%" />
</colgroup>
<thead>
<tr class="header">
<th>属性键</th>
<th>在任务栏的搜索框中键入</th>
<th>访问（R/O，R/W）</th>
<th>必需/可选</th>
<th>描述</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>PKEY_Sensor_Type</p></td>
<td><p>VT_CLSID</p></td>
<td><p>R/O</p></td>
<td><p>必需</p></td>
<td><p>传感器的类型。 GUID 将包含与 Windows 传感器相同的格式（例如，SENSOR_TYPE_ACCELEROMETER_3D）。 有关传感器类型的详细信息，请参阅<a href="https://docs.microsoft.com/windows-hardware/drivers/sensors/about-sensor-constants" data-raw-source="[Sensor type GUIDs](https://docs.microsoft.com/windows-hardware/drivers/sensors/about-sensor-constants)">传感器类型 guid</a>。</p></td>
</tr>
<tr class="even">
<td><p>PKEY_Sensor_State</p></td>
<td><p>VT_UI4</p></td>
<td><p>R/O</p></td>
<td><p>必需</p></td>
<td><p>传感器的状态。 有关传感器状态的详细信息，请参阅<a href="https://docs.microsoft.com/windows-hardware/drivers/ddi/sensorsdef/ne-sensorsdef-sensor_state" data-raw-source="[&lt;strong&gt;SENSOR_STATE&lt;/strong&gt;](https://docs.microsoft.com/windows-hardware/drivers/ddi/sensorsdef/ne-sensorsdef-sensor_state)"><strong>SENSOR_STATE</strong></a>。</p></td>
</tr>
<tr class="odd">
<td><p>PKEY_Sensor_MinimumDataInterval_Ms</p></td>
<td><p>VT_UI4</p></td>
<td><p>R/O</p></td>
<td><p>必需</p></td>
<td><p>硬件支持的传感器数据报表生成的最小时间间隔（毫秒）。</p></td>
</tr>
<tr class="even">
<td><p>PKEY_Sensor_MaximumDataFieldSize_Bytes</p></td>
<td><p>VT_UI4</p></td>
<td><p>R/O</p></td>
<td><p>必需</p></td>
<td><p>ReadFile 调用中返回的最大大小。 ReadFile 调用允许本机 API 分配一个缓冲区来保存任何数据字段。</p></td>
</tr>
<tr class="odd">
<td><p>PKEY_Sensor_Power_Milliwatts</p></td>
<td><p>VT_R4</p></td>
<td><p>R/O</p></td>
<td><p>可选</p></td>
<td><p>传感器功率以毫瓦表示。</p></td>
</tr>
<tr class="even">
<td><p>PKEY_SensorHistory_MaxSize_Bytes</p></td>
<td><p>VT_UI4</p></td>
<td><p>R/O</p></td>
<td><p>可选</p>
<p>但如果传感器支持历史记录，则为必需。</p></td>
<td><p>传感器历史记录数据的最大大小，以字节表示。</p></td>
</tr>
<tr class="odd">
<td><p>PKEY_SensorHistory_Interval_Ms</p></td>
<td><p>VT_UI4</p></td>
<td><p>R/O</p></td>
<td><p>可选</p>
<p>但如果传感器支持历史记录，则为必需。</p></td>
<td><p>传感器历史记录采样间隔，以毫秒为单位。</p></td>
</tr>
<tr class="even">
<td><p>PKEY_SensorHistory_MaximumRecordSize_Bytes</p></td>
<td><p>VT_UI4</p></td>
<td><p>R/O</p></td>
<td><p>可选</p>
<p>但如果传感器支持历史记录，则为必需。</p></td>
<td><p>以字节表示的最大记录大小。</p></td>
</tr>
<tr class="odd">
<td><p>PKEY_Sensor_FifoReservedSize_Samples</p></td>
<td><p>VT_UI4</p></td>
<td><p>R/O</p></td>
<td><p>可选</p>
<p>但如果传感器支持批处理，则需要。</p></td>
<td><p>此传感器在批处理的前（FIFO）缓冲区中保留的事件数。 这可保证最小数量的事件。 如果此值为零，则无法保证传感器会执行批处理。</p></td>
</tr>
<tr class="even">
<td><p>PKEY_Sensor_FifoMaxSize_Samples</p></td>
<td><p>VT_UI4</p></td>
<td><p>R/O</p></td>
<td><p>可选</p>
<p>但如果传感器支持批处理，则需要。</p></td>
<td><p>可在 FIFO 中批处理的最大事件数。 如果此值为零，则传感器不支持批处理。 实际事件数可能小于此数字，因为批处理 FIFO 可由多个传感器共享。</p></td>
</tr>
<tr class="odd">
<td><p>PKEY_Sensor_WakeCapable</p></td>
<td><p>VT_BOOL</p></td>
<td><p>R/O</p></td>
<td><p>可选</p>
<p>但如果传感器支持批处理，则需要。</p></td>
<td><p>指示传感器是否支持唤醒。</p>
<p>如果传感器支持传感器批处理，则应将其设置为 VARIANT_TRUE，如果当 FIFO 已满时，传感器可以唤醒应用程序处理器。 如果传感器无法唤醒应用程序处理器，则应将该值设置为 VARIANT_FALSE。 在这种情况下，此属性的状态指示传感器从连接待机状态中唤醒的能力。</p>
<p>如果传感器支持从 SX 唤醒系统，则此属性应设置为 VARIANT_TRUE，如果不支持从 SX 唤醒，则应将此属性设置为 VARIANT_FALSE。</p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idnotespanspan-idnotespanspan-idnotespannote"></a><span id="Note"></span><span id="note"></span><span id="NOTE"></span>纪录


支持数据批处理的传感器驱动程序必须报告以下常见传感器属性：

-   PKEY\_传感器\_FifoReservedSize\_示例

-   PKEY\_传感器\_FifoMaxSize\_示例

-   PKEY\_传感器\_WakeCapable

从 Windows 10 开始，版本1511现在可以使用 HID 传感器类驱动程序来实现数据批处理。 有关此方面的信息，请参阅[传感器批处理控件](sensor-batching-for-power-saving-.md)。

有关与数据批处理相关的回调函数的信息，请参阅[EvtSensorSetBatchLatency](https://docs.microsoft.com/windows-hardware/drivers/ddi/sensorscx/ns-sensorscx-_sensor_controller_config) 。

使用传感器的额外功能唤醒 CPU 和操作系统的 SX 状态，PKEY\_传感器\_WakeCapable 也用作枚举属性，该属性可从 PnP 驱动程序存储中查询，以确定传感器是否能够除了从连接待机唤醒系统外，还从 SX 唤醒系统。

## <a name="span-idremarksspanspan-idremarksspanspan-idremarksspanremarks"></a><span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>备注


当客户端驱动程序报告以下属性时，客户端驱动程序必须使用**CollectionsListGetMarshalledSizeWithoutSerialization**而不是**CollectionsListGetMarshalledSize**：

-   PKEY\_SensorHistory\_MaxSize\_字节数

-   PKEY\_SensorHistory\_MaximumRecordSize\_字节数

## <a name="span-idrelated_topicsspanrelated-topics"></a><span id="related_topics"></span>相关主题


[EvtSensorSetBatchLatency](https://docs.microsoft.com/windows-hardware/drivers/ddi/sensorscx/ns-sensorscx-_sensor_controller_config)

[PROPVARIANT 结构](https://go.microsoft.com/fwlink/p/?linkid=313395)

[传感器属性](sensor-properties2.md)

[**传感器\_状态**](https://docs.microsoft.com/windows-hardware/drivers/ddi/sensorsdef/ne-sensorsdef-sensor_state)

[传感器类型 Guid](https://docs.microsoft.com/windows-hardware/drivers/sensors/about-sensor-constants)

 

 






