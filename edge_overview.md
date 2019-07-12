# EnOS™ Edge Overview

EnOS™ Edge is the data collector of EnOS Cloud that collects field device data at the edge of IoT or integrates with 3rd-party systems to capture, analyze, and forward data to the EnOS™ cloud.

EnOS™ Edge itself is a software stack that significantly reduces the computing load on the cloud by moving some computing loads into the edge, and provides quicker response to device control.

The software architecture of EnOS Edge is as follows:

.. image:: media/edge_software_architecture.png
   :alt: Figure: Edge software architecture


## Functionality

As the data collector of Envision EnOS™, EnOS™ Edge features fast device connection, device control, automatic data synchronization to the cloud, breakpoint resumption, remote centralized management, and open and rich protocol library.

### Device Connection

- Based on the built-in protocol library, template library, and the optimized connection process, users can quickly connect devices with multiple protocols.

  EnOS™ Edge has a rich protocol library that supports most of the device connection scenarios in the power industry. In addition, it also provides open protocol development capabilities on the Envision developer platform. Developers can develop their own protocols and upload them to the developer platform as necessary, and then publish them to the Edge.

- The testing function on the console helps users remotely test Edge devices.

### Device Control

EnOS™ Edge supports forwarding commands from the cloud to specific devices.

For details, see [Device Control] (learn/device_control)

### Synchronization with EnOS Cloud

As an extension of the cloud functionality, EnOS™ Edge enables the following capabilities:

- Synchronize device data to the cloud;

- Automatically or manually update the model changes in the cloud;

- Download the configurations, such as connection parameters, from the cloud

### Edge computing

- The Edge provides edge computing capability, supporting common formula processing for measuring points. Users can also write and customize calculation scripts on the console.
  
- The Edge has common function operators for edge computing, and supports operator expansion.

See [Edge Computing](learn/edge_computing)

### Breakpoint resumption

If network communication between the Edge and the cloud is interrupted, the data generated in the communication interruption period is automatically cached. After the communication is restored, the cached data will be automatically re-transferred to the cloud in chronological order. How much data can be cached is subject to hardware configuration.

See [Breakpoint Resumption](learn/breakpoint_resumption)

### Remote Centralized Management

- The EnOS console provides communication configuration, testing, and device connection functions;

- The Edge supports firmware OTA upgrade and the modification of configuration parameters;

- The cloud monitors the status of each Edge device and its connected devices in real time, and provides APIs for applications.

<!--end-->
