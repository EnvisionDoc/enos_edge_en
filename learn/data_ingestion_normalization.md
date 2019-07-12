# Data Collection and Processing

A sub-device communicates with EnOS Edge with a protocol. Edge uploads the specified collection point and control point information to EnOS according to *point.csv* in the protocol. EnOS then directly maps the raw data to measuring points defined in models or process the raw data with calculating scripts before mapping it to measuring points, as defined in the template.

.. image:: ../media/edge_work_flow.png

## Connecting with EnOS via Protocols

The data collection capability of Edge is based on a variety of communication protocols. The protocol library of EnOS™ Edge includes not only a large number of industry standard communication protocols but also various proprietary communication protocols. For a list of protocols supported by EnOS, see [ List of Supported Protocols](../reference/protocol_list).

## Data Collection

Based on the device protocol library, the Edge can quickly connect industrial devices and complete data collection. The sub-devices supported by Edge include, but are not limited to, the following list:

.. list-table:: Table: Device types that EnOS Edge supports

   * - Field or Industry
     - Device type
     - Remarks
   * - PV
     - Inverter
     - Device
   * - Junction box
     - Device
     - --
   * - Weather station
     - Device
     - --
   * - Electricity meters
     - Device
     - --
   * - Centralized power station monitoring system
     - Third-party system
     - --
   * - Substation comprehensive automation system 
     - Device
     - --
   * - Wind energy
     - Wind turbine
     - Device
   * - Box transformer
     - Device
     - --
   * - Anemometer tower
     - Device
     - --
   * - Substation comprehensive automation systems
     - Third-party system
     - --
   * - Industrial parks/buildings
     - Power meters
     - Device
   * - Charging pole
     - Device
     - --
   * - Power distribution management systems
     - Third-party system
     - --
   * - Energy storage battery PCS
     - Device
     - --
   * - Traditional power (thermal power, hydropower, gas-fired power, etc.)
     - DCS/comprehensive automation backend systems
     - Third-party system

## Data Timestamping

In support of the data processing logic of applications in the cloud, Edge not only tags collected data with the latest timestamp but also retains the earlier timestamp when the sub-device data comes in. Sub-device data is processed as the following rules:

- The raw data time is saved as an attribute of a data entry and uploaded to the cloud.

- Edge timestamps a data entry in coordinated universal time (UTC). 

- Edge converts earlier timestamps created with different protocols into a uniform format. If the earlier timestamp sent by a certain device is UTC+8, it can be converted to UTC+0.

## Data Mapping

In addition to data collection, another core function of Edge is to model the collected data according to the device model defined on the cloud, and then map them to the corresponding device.

.. image:: ../media/edge_data_processing_flow.png
   :alt: Figure: Data Processing in the Edge

Users can use the following methods to map data to measuring points defined in a model:
- One-one mapping: The value of a collection point is mapped to a measuring point of a model without any processing.
- Formula mapping: process a collection point with a formula and then map it to a measuring point. EnOS has  a set of formulas pre-defined for users. For more information, see [Formula Mapping](../reference/edge_computing)
- Script mapping: Users can create a script to process a collection point and then map it to a measuring point.

You can only use one-one mapping for a control point.

After being processed and mapped, the raw data becomes standard device model data and is then sent to EnOS.


<!--end-->
