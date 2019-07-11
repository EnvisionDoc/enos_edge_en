# Data Ingestion

Note: This article is in the progress of translation. Thanks for your visit!

设备根据其支持的规约与EnOS Edge通信，Edge根据规约中包含的点表模板，将指定的采集点和控制点信息上传到EnOS。EnOS再根据云端定义的Edge模板，将点表中的原始数据，经过映射或者脚本的处理，关联到该设备在EnOS上所属模型的属性上。

.. image:: ../media/edge_work_flow.png
   :width: 400px

## 通过规约与EnOS连接

Edge的数据采集能力，主要是基于Edge对各种通讯规约的支持能力。EnOS™ Edge规约库中不仅积累了大量的行业标准通讯规约，同时也有丰富的特定类型设备的私有通讯规约。EnOS支持的规约列表，参见[已支持的规约列表](../reference/protocol_list)

## 数据采集

基于设备规约库，Edge能够快速地支持工业领域设备的接入并完成数据采集。EnOS支持的设备包含但不限于下表所列。

.. list-table:: 表：EnOS™ Edge支持数据采集的设备类型

   * - 应用领域
     - 设备类型
     - 备注
   * - 光伏
     - 逆变器
     - 设备
   * - 汇流箱
     - 设备
     - --
   * - 气象站
     - 设备
     - --
   * - 电能表
     - 设备
     - --
   * - 集中式电站监控系统
     - 第三方系统
     - --
   * - 升压站综自系统
     - 设备
     - --
   * - 风能
     - 风机
     - 设备
   * - 箱变
     - 设备
     - --
   * - 测风塔
     - 设备
     - --
   * - 升压站综自系统
     - 第三方系统
     - --
   * - 工业园区/商业楼宇
     - 电能表
     - 设备
   * - 充电桩
     - 设备
     - --
   * - 配电管理系统
     - 第三方系统
     - --
   * - 储能电池PCS
     - 设备
     - --
   * - 传统电力(火电、水电、燃气发电等)
     - DCS/综自后台系统等
     - 第三方系统

## 数据时间戳处理

为支持云端上层应用复杂的数据处理逻辑，Edge不仅支持对接入数据打上接入时刻的最新时标，同时也支持保留设备数据上送的原始时间。具体处理规则如下：

- 数据原始时间将会保存在每一条数据的一个属性中上传的云端供领域应用灵活使用；

- Edge对接入时间打时标时，都使用UTC+0时间进行统一时间标注；

- Edge中的前置接入模块支持对不同规约上送的数据原始时标进行时区转换配置，如某一种设备型号上送的原始数据时标是UTC+8时区,则可以做相应配置，将接入的数据原始时标转换成UTC+0时区。

## 数据模型化

完成数据采集后，Edge的另一个核心功能就是按照云端定义的设备模型，将采集到的数据模型化，并映射到对应的设备上。

.. image:: ../media/edge_data_processing_flow.png
   :alt: 图：Edge数据处理流程

EnOS Edge采集到的数据，可以分为采集点和控制点。

采集点是设备向云端上送的测点，如风速、电动机转速等。

控制点是云端向设备下发的测点，如设备的启动、停止、复位等，控制点又分为AO型，取值可为整型或其他数据类型；与DO型控制点，取值通常为整型。

采集点和控制点的数据类型有以下几种：

- AI：即模拟输入（analogous input）
- DI：即数字输入（digital input）
- PI：即脉冲输入（pulse input）
- AO：即模拟输出（analogous output）
- DO：即数字输出（digital output）

对于采集点的映射，用户有以下映射方式：
- 一对一映射：采集点的值无需任何处理即成为模板属性点的值。在采集点列表中，为模型属性选择相应的采集点即可。
- 公式映射：对采集点进行公式运算，再映射到模型的属性上。EnOS为用户预置了一系列公式，参见[边缘计算](edge_computing)
- 自定义脚本处理：对于复杂的数据处理，用户还可以通过自定义脚本的方式实现运算。

对于控制点的映射,用户只能采用简单映射方式。同一个模型点，既可以关联采集点，又可以关联控制点。

原始数据经过运算、映射处理后，变成标准的设备模型数据点，然后上送到EnOS。


<!--end-->
n points, calculation scripts, etc. When connecting
with a device of the same model again, users can simply choose the
corresponding device model template from the library to complete the
device connection in a short time.

Currently, the device model library has accumulated the model
information of almost all energy devices, supporting the business
scenaros of solar power, wind power, industrial parks, buildings, etc.
Besides, with the data processing capability of its front-end module,
the Edge also supports data ingestion transferred from third party
systems.

.. note:: The data ingestion supported by Edge is real-time data only.

.. list-table:: Device Types Supported by EnOS Edge
   :widths: 25 25 50

   * - Domain
     - Device Type
     - Remarks
   * - Solar Power
     - Inverter
     - Device
   * - Combiner Box
     - Device
     - /
   * - Meteorological Station
     - Device
     - /
   * - Electric Energy Meter
     - Device
     - /
   * - Centralized Plant Monitoring System
     - Third Party System
     - /
   * - Substation Integrated Automatic System
     - Device
     - /
   * - Wind Power
     - Wind Turbine
     - Device
   * - Box Transformer Substation
     - Device
     - /
   * - Anemometer Tower
     - Device
     - /
   * - Substation Integrated Automatic System
     - Third Party System
     - /
   * - Industrial parks / Commercial Buildings
     - Electric Energy Meter
     - Device
   * - Charging Pile
     - Device
     - /
   * - Power Distribution Management System
     - Third Party System
     - /
   * - Battery PCS
     - Device
     - /
   * - Traditional Electric Power (Thermal power, Hydropower, Gas power, etc.)
     - DCS, Substation Integrated Automatic System, etc
     - Third Party System

.. note:: Including, but not limited to the types listed in the table.

## Data Timestamp Processing

Normally, EnOS Edge will add a timestamp to each data tags when
receiving it, and the edge server time will be used as this timestamp.
Meanwhile, in order to support the complicated data process logic in the
Cloud platform, the original OEM device timestamp (if available) of each
data tag will also be recorded and send to the cloud. The detailed
processing rules are as follow:

- The Edge will tag received data with timestamp using UTC+0 time zone.

- The original OEM device timestamp (if available) will be recorded as an attribute of the normalized data tag and sent to the cloud with the data flow.

- The original OEM device timestamp will be converted to unified timestamp using UTC+0 time.

## Protocols Supported by EnOS Edge

The data ingestion capability of an edge mainly depends on how many
communication protocols it supports. The protocol library of EnOS Edge
accumulated a large number of industrial standard communication
protocols and a rich private protocol library used for specific devices.
The following tables list the protocols that EnOS Edge supports.

.. list-table:: Industrial standard protocols that EnOS Edge supports
   :widths: 20 20 20 40

   * - Protocol
     - Data Type
     - Communication Type
     - Network
   * - ModbusTCP
     - Bit/Short/Ushort/Int/Uint/Float
     - Client/Server
     - Ethernet
   * - ModbusRTU
     - <td">Bit/Short/Ushort/Int/Uint/Float
     - Master
     - Need to be converted to Ethernet
   * - IEC60870-5-104
     - Int/Float
     - Client/Server
     - Ethernet
   * - DNP3.0
     - Int/Float
     - Client
     - Ethernet
   * - OPC-DA
     - Uint/Double/Float/Int/Long/Char/Ushort/Short/Bool
     - Client
     - Ethernet
   * - OPC-XML-DA
     - Uint/Double/Float/Int/Long/Char/Ushort/Short/Bool
     - Client
     - Ethernet
   * - OPC-UA
     - Uint/Double/Float/Int/Long/Char/Ushort/Short/Bool
     - Client
     - Ethernet
   * - HTTP(s)
     - Int/Float
     - Web Service
     - Ethernet
   * - DL/T645-1997
     - Int
     - Master
     - Need to be converted to Ethernet
   * - DL/T645-2007
     - Int
     - Master
     - Need to be converted to Ethernet



.. list-table:: Devices with private protocols that EnOS Edge supports
   :widths: auto

   * - Manufacturer
     - Devices
   * - Growatt
     - Growatt
   * - Goodwe
     - GoodweTcp
   * - GoodweWebService
     - --
   * - Jinlang
     - JinlangTCP
   * - KSTAR(ksg)
     - KSTAR(ksg)
   * - Lekong
     - Lekong
   * - Omnik
     - Omnik
   * - TaiDa
     - TaiDa
   * - Taoke
     - Taoke
   * - SunGrow
     - SunGrow
   * - Apsystems
     - Apsystems
   * - YunKong
     - YunKong
   * - Trannergy
     - Trannergy
   * - Trinasolar
     - --
   * - Solarman
     - Solarman
   * - Aifu
     - Aifu
   * - Dingyang
     - dingyangTcp
   * - dingyangTcp-jingfuyuan
     - --
   * - SMA
     - SMA


<!--end-->
