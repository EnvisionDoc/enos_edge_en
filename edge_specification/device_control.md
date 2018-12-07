# Device Control

EnOS Edge supports device control by receiving control commands from the applications in the cloud, converting them to protocol commands, and sending the commands to devices.

The prerequisites for device control include:

- The application in the cloud platform has the function of sending out commands.

- The device communication protocol supports control commands.

- The Edge supports the following control commands:

  - DO: Digital output, 0/1 command, Boolean

  - AO: Analog output
