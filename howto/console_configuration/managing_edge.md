# Managing Edge

To use the Edge as a gateway to collect data and perform other functions, you need to create the Edge device and configure the appropriate communication parameters in **EnOS Edge > Edge Management**.

## Before You Start

- Obtain the access to Edge management. If you don't have the access, contact your OU administrator. For more information, see [Policies, Roles and Permissions](/docs/iam/en/latest/access_policy).
- Create the Edge model, product and devices. See [Device Management](/docs/device-connection/en/latest/device_management_overview). Note that the name of the Edge model must be **EnOS_Edge_Standard_Model** and the name of the Edge product must be **EnOS_Edge_Standard_Product**.

## Creating Edges

1. Select **EnOS Edge > Edge Management**;

2. Click **New Edge**. In pop-up window, select the Edge devices to be created from the list. click **Confirm** when you are done.

## Creating Connections

After adding an Edge device, the next step is to add a connection so that sub-devices can connect to the Edge. 

1. In the **Operations** column, click **View**.

2. Select **Access Management** tab page, select the type of the connection: **Ethernet** or **COM Port**.

3. Click **Add Connection**. 

### Adding an Ethernet Connection

In the pop-up window, fill in the following fields:

.. csv-table::
   :widths: auto

   "Fields", "Descriptions"
   "Name", "Identifier for the connection"
   "Mode", "Whether Edge acts as a server or a client in a given protocol. Supports TCP/IP client, TCP/IP server, HTTP(s) client, HTTP(s) server, UDP and others. "
   "Short Connection", "Used to determine whether the connection is a long connection or a short connection."
   "Primary Interface", "See explanation below the table"
   "Standby Interface", "See explanation below the table"
   "Protocol Type", "You need to select the Protocol Type first before selecting a specific protocol version"
   "Protocol", "Select a protocol version in the drop-down list"
   "Configuration File", "After selecting the specific protocol, you can download the protocol.sys file and modify it as needed. Then upload it to the connection"

The meaning of **Primary Interface** in different modes are given as follows:

- TCP/IP Client: Fill in with the IP address and port number of the server that Edge connects to;
- TCP/IP Server: Fill in with the IP address and port number of the client that is allowed to be connected to the Edge;
- HTTP(s) Client: Fill in with the primary address of the HTTP(s) server that Edge connects to;
- HTTP(s) Server: Fill in with the address and port number of the Edge device in the format of "172.0.0.0: Port Number";
- UDP: In the UDP mode, there are two parameters: "Remote Address (Primary)" and "Local Address (Primary)". Fill in with these addresses and port numbers respectively with the primary addresses of server and client.
- Others: Select this mode when the connection does not fall into any of the above-mentioned modes. Consult support personnel on how to fill in the **Primary Interface** field.

The meaning of **Standby Interface** in different modes are given as follows:

- TCP/IP Client: Fill in with the IP address and port number of the standby server address that Edge connects.
- TCP/IP Server: Fill in with the IP address and port number of the standby client address that is allowed to be connected to Edge;
- HTTP(s) Client: Standby address is not supported in this mode. Leave it blank.
- HTTP(s) Server: Standby address is not supported in this mode. Leave it blank.
- UDP: In the UDP mode, there are two parameters: "Remote Address (Standby)" and "Local Address (Standby)". Fill in the remote and local addresses and port numbers respectively with the standby addresses of server and client.
- Others: Standby address is not supported in this mode. Leave it blank.

### Creating a COM Port Connection

To add a COM port connection, you need to fill in the following fields:

- Name: Identifier of the COM port.
- Serial Port: Type of the COM port.
- Baud Rate: The number of bits the port is able to transfer in a second.
- Data Bit: Length of the bits that represents data. Fixed at 8.
- Check Bit: Bit used for error detection.
- Stop Bit: End of binary data.
- Protocol Type: You need to select the Protocol Type first before selecting a specific protocol version.
- Protocol: Select a protocol version in the drop-down list
- Configuration file: After selecting the specific protocol, you can download the protocol.sys file and modify it as needed. Then upload it to the connection.

## Creating Sub-devices

After creating the connection, you should add the sub-devices that use the connection.

1. Click the connection you created to expand it.

2. Click **Add Device**. 

3. Select a product that the sub-device belongs to. 

4. In **Template Setting** , select the tempate for the sub-device.

## Editing Sub-devices

You can edit the sub-device information by clicking |edit| in the **Operation** column. if you need to edit the sub-device information in batch, you can select **Export** to the right of the connection and then edit in batch in the downloaded sub-device list, as shown below:

.. |edit| image:: ../../media/button_edit.png

.. image:: ../../media/editing_device_in_batch.png

## Configuring Logical Address or Offset for Sub-devices

Since multiple devices are connected using a single connection, each sub-device needs to be configured with its own logical address and the offset. The configuration method is subject to the communication protocol used and its settings. Configure the logical address and offset on a device-by-device basis. You can also export the sub-device information in batch and configure it offline, then import it into the system.

1. Device-by-device configuration

   Click on the |018| icon to edit the device, as shown below:

   .. |018| image:: ../../media/button_edit.png

   .. image:: ../../media/configuring_logical_address.png
      :alt: Figure: Configuring the Logical Address and Offset Device by Device

2. Batch configuration

   Click the Export button under the connection to download the connection information form. After filling in required fields, click the Import button to upload the information form.

.. note:: The exported table supports configuring AI, DI, PI, AO, DO and PO offsets. The format is n-n, where n is an integer, such as 0-50. When there are multiple offsets at the same time, use \# to separate them, such as 0-50\#1000-1050.

## Forwarding Data

You can also forward the data collected by Edge to third-party systems as needed. The steps for setting the data forwarding are similar to those done in **Access Management**, including adding connections, adding sub-devices, and configuring connection parameters. EnOS supports forwarding data by using the following protocols:

- IEC104

### Using IEC104 to Forward Data

1. Click **Add Connection**, fill in the following fields:

   - Name: Identifier of the connection
   - Mode: Whether Edge acts as a server or a client in a given protocol. Supports TCP/IP client, TCP/IP server, HTTP(s) client, HTTP(s) server, UDP and others.
   - Primary Interface: See explanation below.
   - Protocol: Select an IEC104 protocol.
   - Configuration File: You can download the profile and modify it as needed before uploading it.
  
  The meaning of **Primary Interface** in different modes are given as follows:

 - TCP/IP Client: Fill in with the IP address and port number of the primary server address that Edge connects.
 - TCP/IP Server: Fill in with the IP address and port number of the primary client address that is allowed to be connected to Edge;
 - HTTP(s) Client: Fill in with the primary address of the HTTP(s) server that Edge connects to;
 - HTTP(s) Server: Fill in with the address and port number of the Edge device in the format of "172.0.0.0: Port Number"
 - Others: Select this mode when the connection does not fall into any of the above-mentioned modes. Consult support personnel on how to fill in the **Primary Interface** field.

2. Click **Confirm**. 

3. Click to expand the connection. Select **Add Device**

4. Select the model, product and sub-device. 

5. Select a template for the sub-device in **Template Setting** and click **Save**

   After the device is added, the system automatically assigns an index to the sub-device according to the order in which the sub-device is added. Note that the indexes are natural numbers starting from 1, and must be continuous and non-repeatable under a connection.

## Publishing Connection

After completing required configurations, publish the connection to the corresponding Edge device or server to enable the connection. As show below:

.. image:: ../../media/publishing_device.png
   :alt: Figure: Releasing the Configurations to the Box

## Testing Connection

After adding the connections and sub-devices and publishing the connection, you can test the connection. Click the |test| button to the right of the connection to test it.

.. |test| image:: ../../media/button_test.png
   :alt: Figure: Testing Button

You can use the testing function to view the connections of Ethernet and serial ports created under this Edge device, including the following information:

- Data: Real-time device data. You can set a measuring point value for a device.
- Message: Communication messages under this connection
- Log: Communication log under this connection. Only the logs of warnings and errors are displayed.

### Setting Value

Click **Set** in the **Data** tab and set a value for a collection point, then click **Send** to let Edge send the value EnOS. This operation does not interrupt the uploading of real-time data from sub-devices to EnOS cloud but inserts the data you set into the uploading data stream.

.. |view| image:: ../../media/button_view.png

### Console

Common communication debugging commands are provided in **Console** tab, including basic ping testing command, local IP viewing command, Telnet command and TCP connection viewing command.

### Communication test for a single device

On the **Access Management** tab, click the |view| button for a single device to set value for the sub-device. This function is the same as the above setting value function, except that only a single device is tested here.

.. |view| image:: ../../media/button_view.png

<!--end-->
