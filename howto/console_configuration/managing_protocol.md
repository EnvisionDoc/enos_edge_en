# Managing Protocols

Users can manage the protocols in **EnOS Edge > Protocol**.

## About This Task

This topic describes how to edit, release, upgrade and delete protocols.

## Before You Start

Obtain permissions to manage protocols. For more information, see [Policies, roles, and permissions](/docs/iam/en/latest/access_policy).

## Editing protocols

Click **+** in front of the protocol name to expand the list of protocol versions. For debug-suffixed versions (**_debug**), you can click |edit| in **Operations** column to edit them. Users can perform the following operations:

.. |edit| image:: ../../media/button_edit.png

- Update the protocol program package by first downloading, then editing, and at last replacing the package with the edited version.
- Update the system configuration file *protocol.sys* in the same way as protocol program package
- Update point.csv  in the same way as protocol program package
- Update the description

  .. image:: ../../media/edge_protocol_edit.png

<!--For the documents for which the debug status is editable, how to set their status? -->

## Releasing Protocols

For protocols that have a version number with **_debug** suffix, you can release them by clicking |release| in the **Operations** column. The suffix will change from **_debug** to **_release**. The protocol becomes uneditable.

.. |release| image:: ../../media/button_release.png

## Upgrading protocols

If all the versions of a current protocol are released, the user can add a new version to the protocol by upgrading the protocol. Select |update| in the **Operations** column and enter the following information in the pop-up window:

.. |update| image:: ../../media/button_update.png

.. list-table::
   :widths: auto

   * - Parameters
     - Parameter descriptions
   * - Upgrade Reason
     - There are two options available, including "New Feature" and "Bug Fix". Select the reason for your update. 
   * - Package
     - Upload the *.bin* file of protocol program
   * - System Configuration
     - Upload protocol.sys template of the updated protocol
   * - Point
     - Upload *point.csv* of the new protocol
   * - Description
     - Enter the description of this update
   * - Impact Scope
     - Since the original protocol version may have been applied to multiple Edge devices, you can select which Edge devices the updated protocol applies to. Click **Click to select** to specify the Edge devices.

## Deleting protocols

Click |delete| in the **Operations** column to delete any protocol not needed.

.. |delete| image:: ../../media/button_delete.png

<!-- end  -->
