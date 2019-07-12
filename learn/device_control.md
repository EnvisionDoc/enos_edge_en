# Device Control

The prerequisites required for the Edge to control sub-devices include the following:

- The applications on the cloud can send device control commands;

- The protocol with which Edge communicates with the sub-device supports the command;

- The current Edge supports the following control types:

 - Remote control  DO: sending the switch quantity commands;

 - Remote tuning AO: sending the analog quantity commands.

Device control by EnOS™ Edge includes the following steps performed by Edge:

1. Receiving the control commands sent from applications on the cloud;

2. Converting them into protocol-conforming messages that the sub-device can process;

3. Sending messages to the sub-devices to for them to execute the commands.


