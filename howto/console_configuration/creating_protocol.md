# Creating Protocols

The administrator users can manage the communication protocols that EnOS Edge supports at **EnOS Edge > Protocol**, including adding, viewing, updating, publishing and deleting protocols. Non-administrator users can view various protocols supported by EnOS.

## About This Task

This topic describes how to create protocols on EnOS console.

## Before You Start

- You should obtain the OU administrator account if you want to create a protocol.

## Creating a protocol

1. Select **EnOS Edge > Communication Protocol**. and then click **Add**;

2. In the protocol creation window, fill in the following information: 

   .. list-table::
      :widths: auto

      * - Parameter
         - Parameter description
      * - Protocol type
         - Select from the protocols pre-defined by EnOS
      * - Roles
         - Select whether Edge acts as a server or client in its communication with sub-devices
      * - Name
         - Identifier for the protocol
      * - Package
         - bin file of protocol program
      * - Description
         - /
      * - Protocol document
         - /
      * - System Configuration
         - Upload protocol.sys that contains communication configuration for this protocol
      * - Point
         - Point.csv of this protocol
<!--end-->

   .. image:: ../../media/edge_protocol_create.png

3. Click **Confirm** to complete the creation of a new protocol. You can view the new protocol in the list.

## Releasing a protocol

For protocols that have a version number with **_debug** suffix, you can release them by clicking the |Release| button in the **Operations** column. The suffix of released protocols will change from **_debug** to **_release**, and become non-editable.

.. |Release| image:: ../../media/button_release.png

## Results

The new protocol is displayed in the form of *Protocol Type* - *Role* - *Protocol Name*. For example, if you create a new client protocol of BACnet with the name "bacnet_test_renbin", its name will be BACnet-Client-bacnet_test_renbin".

The default version of the new protocol is **v1.0_debug**. The protocol version is named as per the following rules:

v*Main Version No.*.*Revision No.*_*State suffix*

.. csv-table::
       
   "Fields", "Descriptions"
   "Main Version No.", "Represents a version containing new functions. Its value is an integer starting from 1. The main version number increments by 1 for every new version. For example, if the original version is v1.0_release, then the main version number should be modified to v2.0_release when a new function is added"
   "Revision number", "Identifies a fixed problem. Its value is an integer starting from 0. When a problem is fixed, the revision number increments by 1. For example, if the original version is v1.0_release, when only a problem is fixed for current version without any function added, the version number should be modified to v1.1_release."
   "State suffix", "Identifies the release state. Its value may be **_debug** or **_release**. The protocols with **_debug** are usually the beta-version protocols that have just become available. The protocol manager can still modify a **_debug** protocol. Protocols with **_release** are the officially released protocols, which are locked and can only be used, viewed and downloaded and cannot be modified."

<!--End-->

## Next step

Users can manage the protocols. See [Managing Protocols](managing_protocols).








