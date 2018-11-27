# Data ingestion

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

**Note:** The data ingestion supported by Edge is real-time data only.

*Table: Device Types Supported by EnOS Edge*


<table>
  <tr>
    <td>Domain</td>
    <td>Device Type</td>
    <td>Remarks</td>
  </tr>
  <tr>
    <td>Solar Power</td>
    <td>Inverter</td>
    <td>Device</td>
  </tr>
  <tr>
    <td>Combiner Box</td>
    <td>Device</td>
  </tr>
  <tr>
    <td>Meteorological   Station</td>
    <td>Device</td>
  </tr>
  <tr>
    <td>Electric   Energy Meter</td>
    <td>Device</td>
  </tr>
  <tr>
    <td>Centralized   Plant Monitoring System</td>
    <td>Third Party   System</td>
  </tr>
  <tr>
    <td>Substation Integrated   Automatic System</td>
    <td>Device</td>
  </tr>
  <tr>
    <td>Wind Power</td>
    <td>Wind Turbine</td>
    <td>Device</td>
  </tr>
  <tr>
    <td>Box   Transformer Substation</td>
    <td>Device</td>
  </tr>
  <tr>
    <td>Anemometer   Tower</td>
    <td>Device</td>
  </tr>
  <tr>
    <td>Substation Integrated   Automatic System</td>
    <td>Third Party   System</td>
  </tr>
  <tr>
    <td>Industrial   parks / Commercial Buildings</td>
    <td>Electric   Energy Meter</td>
    <td>Device</td>
  </tr>
  <tr>
    <td>Charging Pile</td>
    <td>Device</td>
  </tr>
  <tr>
    <td>Power Distribution   Management System</td>
    <td>Third Party   System</td>
  </tr>
  <tr>
    <td>Battery PCS</td>
    <td>Device</td>
  </tr>
  <tr>
    <td>Traditional   Electric Power (Thermal power, Hydropower, Gas power, etc.)</td>
    <td>DCS, Substation   Integrated Automatic System, etc</td>
    <td>Third Party   System</td>
  </tr>
</table>

**Note:** Including, but not limited to the types listed in the table.

## Data timestamp processing

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

## Protocols Supported by EnOS edge

The data ingestion capability of an edge mainly depends on how many
communication protocols it supports. The protocol library of EnOS Edge
accumulated a large number of industrial standard communication
protocols and a rich private protocol library used for specific devices.
The following tables list the protocols that EnOS Edge supports.

*Table: Industrial standard protocols that EnOS Edge supports*


<table>
  <tr>
    <td>Protocol</td>
    <td>Data Type</td>
    <td>Communication Type</td>
    <td>Network</td>
  </tr>
  <tr>
    <td>ModbusTCP</td>
    <td>Bit/Short/Ushort/Int/Uint/Float</td>
    <td>Client/Server</td>
    <td>Ethernet</td>
  </tr>
  <tr>
    <td>ModbusRTU</td>
    <td">Bit/Short/Ushort/Int/Uint/Float</td>
    <td>Master</td>
    <td>Need to be converted to   Ethernet</td>
  </tr>
  <tr>
    <td>IEC60870-5-104</td>
    <td>Int/Float</td>
    <td>Client/Server</td>
    <td>Ethernet</td>
  </tr>
  <tr>
    <td>DNP3.0</td>
    <td>Int/Float</td>
    <td>Client</td>
    <td>Ethernet</td>
  </tr>
  <tr>
    <td>OPC-DA</td>
    <td>Uint/Double/Float/Int/Long/Char/Ushort/Short/Bool</td>
    <td>Client </td>
    <td>Ethernet</td>
  </tr>
  <tr>
    <td>OPC-XML-DA</td>
    <td>Uint/Double/Float/Int/Long/Char/Ushort/Short/Bool</td>
    <td>Client</td>
    <td>Ethernet</td>
  </tr>
  <tr>
    <td>OPC-UA</td>
    <td>Uint/Double/Float/Int/Long/Char/Ushort/Short/Bool</td>
    <td>Client</td>
    <td>Ethernet</td>
  </tr>
  <tr>
    <td>HTTP(s)</td>
    <td>Int/Float</td>
    <td>Web Service</td>
    <td>Ethernet</td>
  </tr>
  <tr>
    <td>DL/T645-1997</td>
    <td>Int</td>
    <td>Master</td>
    <td>Need to be converted to   Ethernet</td>
  </tr>
  <tr>
    <td>DL/T645-2007</td>
    <td>Int</td>
    <td>Master</td>
    <td>Need to be converted to   Ethernet</td>
  </tr>
</table>

*Table: Devices with private protocols that EnOS Edge supports*

<table>
  <tr>
    <td>Manufacturer</td>
    <td>Devices</td>
  </tr>
  <tr>
    <td>Growatt</td>
    <td>Growatt</td>
  </tr>
  <tr>
    <td>Goodwe</td>
    <td>GoodweTcp</td>
  </tr>
  <tr>
    <td>GoodweWebService</td>
  </tr>
  <tr>
    <td>Jinlang</td>
    <td>JinlangTCP</td>
  </tr>
  <tr>
    <td>KSTAR(ksg)</td>
    <td>KSTAR(ksg)</td>
  </tr>
  <tr>
    <td>Lekong</td>
    <td>Lekong</td>
  </tr>
  <tr>
    <td>Omnik</td>
    <td>Omnik</td>
  </tr>
  <tr>
    <td>TaiDa</td>
    <td>TaiDa</td>
  </tr>
  <tr>
    <td>Taoke</td>
    <td>Taoke</td>
  </tr>
  <tr>
    <td>SunGrow</td>
    <td>SunGrow</td>
  </tr>
  <tr>
    <td>Apsystems</td>
    <td>Apsystems</td>
  </tr>
  <tr>
    <td>YunKong</td>
    <td>YunKong</td>
  </tr>
  <tr>
    <td>Trannergy</td>
    <td>Trannergy</td>
  </tr>
  <tr>
    <td>Trinasolar</td>
  </tr>
  <tr>
    <td>Solarman</td>
    <td>Solarman</td>
  </tr>
  <tr>
    <td>Aifu</td>
    <td>Aifu</td>
  </tr>
  <tr>
    <td>Dingyang</td>
    <td>dingyangTcp</td>
  </tr>
  <tr>
    <td>dingyangTcp-jingfuyuan</td>
  </tr>
  <tr>
    <td>SMA</td>
    <td>SMA</td>
  </tr>
</table>
