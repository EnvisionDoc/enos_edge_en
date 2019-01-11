# Data Ingestion

With the device models and protocol library in the Cloud platform, the
Edge can be implemented to connect with different kinds of energy
devices quickly. The device model library in the Edge contains detailed
information of all connected devices, including domain points, protocol,
configuration files, mapping relationships between the raw data points
and standard domain points, calculation scripts, etc. When connecting
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

- The original OEM device timestamp (if available) will be recorded as an attribute of the normalized data tag and sent to the cloud with
    the data flow.

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
   :widths:: auto

   * - Manufacturer
     - Devices
   * - Growatt
     - Growatt
   * - Goodwe
     - GoodweTcp
   * - GoodweWebService
     - /
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
     - /
   * - Solarman
     - Solarman
   * - Aifu
     - Aifu
   * - Dingyang
     - dingyangTcp
   * - dingyangTcp-jingfuyuan
   * - SMA
     - SMA

<!--end-->
