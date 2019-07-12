# Concepts

Before you learn how Edge works, read the following key concepts:


## Sub-device

The devices connected to EnOS Edge are referred to as sub-devices.

## Connection

A connection refers to the TCP link established between the Edge and its sub-devices or 3rd-party systems. A connection can be used to access the data of a sub-device or a batch of sub-devices. A connection uses a protocol to communicate with sub-devices or 3rd-party systems.


## Template 

The template determines how data collected by using a protocol is mapped into the model measuring points defined on EnOS Cloud. Its main function is to map the measuring points prescribed in the protocol (to be specific, the *point.csv* file of the protocol) to the measuring points defined in the device model. In addition, the template includes calculation formulas and scripts, so that data from selected devices will be processed with the formula or calculation script before mapping it to measuring points.

## Protocol

The protocol refers to a system of rules to be executed for the communication between two entities (Edge and sub-devices, Edge and 3rd-party systems). It refers to the communication protocol on the application layer, such as IEC104, OPC and Modbus.

In EnOS Edge, the protocol includes *protocol program*, *configuration file* and *point.csv*.

### Protocol Program

If you are using C++ to develop the protocol, the protocol program refers to the *.bin* file to implement the protocol.

### Protocol.sys

This file is the parameter configuration file required by the protocol program. In **EnOS Edge > Protocol**, the *protocol.sys* of each protocol is provided for users to download and configure.

### Point.csv

Point.csv of a particular protocol contains the sequence of measuring points to be uploaded to EnOS or forwarded to a third-party system. In **EnOS Edge > Template**, you can download *point.csv*.

## Protocol Document

The is uploaded by the protocol developers along with the protocol program. The protocol document covers the configuration and usage instructions.

## Measuring Point

The measuing point refers to the data collected by Edge to be sent to EnOS. A measuing point can be a device collection point or a device control point.

### Collection Point

The collection point refers to the measuring point sent by sub-device to cloud through Edge, as defined in *point.csv*, such as the measuring points for wind speed and motor speed.

A colllection point can be one of the following type of data:

- AI: analogous input
- DI: digital input
- PI: pulse input

### Control Point

The control point is a measuring point the cloud sends to a sub-device through Edge, to set or reset value for a measuring point, or to give commands to the device to start or stop, as defined in *point.csv*. The control point is further divided into the following:
- Analogous output （AO, whose value can be any data type)
- Digital output (DO, whose value is usually an integer)







