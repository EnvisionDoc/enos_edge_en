# Creating Device Templates

The device templates can be created in the following ways:

- Creating a new template online by using the **Add** button in **EnOS Edge > Template** .
- Export a template of an existing device template, then modify it offline, save it as a new template, and import it into EnOS

The latter is applicable to the scenario where the template to be created is just slightly different to an existing one.

## About This Task

This topic describes how to manage templates in the EnOS console.

## Before You Start

- Obtain the access to template management. If you don't have the access, contact your OU administrator. For more information, see [Policies, Roles and Permissions](/docs/iam/en/latest/access_policy).

## Creating a Template Online

### Creating Basic Information

1. Select **EnOS Edge > Template** and then click the **New Template** button. Fill in the following fields.

   .. csv-table::

      "Fields", "Descriptions"
      "Template Name", "/"
      "Device Brand", "/"
      "Device Model", "/"
      "Version", "/"
      "Device Model", "Select the model for the sub-devices."
      
   .. image:: ../../media/edge_template_create.png

2. Click **Confirm** to complete the creation of basic template information.

### Editing and uploading the point table file point.csv

1. Select the template you created and click |edit| in the **Operations** column.

   .. |edit| image:: ../../media/button_edit.png

2. At **Point File** in the basic information section, click |download template|, select a template, and then click |download| to download the *point.csv* file;
   
   .. |download template| image:: ../../media/button_download_template.png
   .. |download| image:: ../../media/button_download.png

3. Open *point.csv*. Enter the measuring point information in the file.

   .. csv-table::

      "Fields", "Descriptions"
      "Measuring Point Name", "The name of collection points from the device."
      "Point Number", "Information indicating the location of the data. EnOS use this number to map collection points to measuring points."
      "Value Type", "Data type of measurepoint. See below for details"
      "Point Type", "Point types supported by EnOS"
      "Coefficient", "If you want to convert the data type or unit, you need to perform an operation similar to a(x+b) in the communication protocol, where a is the coefficient. In this scenario, you must set this value."
      "Base Value", "If you want to convert the data type or unit, you need to perform an operation similar to a(x+b) in the communication protocol, where b is the base value. In this scenario, you must set this value."
      "Alias", "The alias is an attribute of the measuring point. Its default value is the point number"


   Different protocols support different types of measuring points. It is usually necessary to configure the following types of measuring points:

   - byte
   - short
   - ushort
   - int
   - uint
   - long
   - float
   - double

4. Fill in all the required fields and save the file, then click **Upload**.

   You can click |edit| to edit point.csv online.

   .. |edit| image:: ../../media/button_edit.png

### Configuring Point Mapping

After uploading *point.csv* , you need to map the device collection points and control points to the model measuring points.

1. In **Operations** column of the selected template, click |edit| to enter **Edit Template** page.

   .. |edit| image:: ../../media/button_edit.png

2. The list in **Points Mapping** displays all the measuring points as defined in the model

   .. image:: ../../media/edge_template_measuring_points.png

3. In the **Mapping** column, click |edit| to enter the mapping configuration page:

   .. |edit| image:: ../../media/button_edit.png
   .. image:: ../../media/edge_template_collection_points.png

4. To map collection point, on **Collect** tab, Select one-to-one mapping or formula mapping. For more information, see [Mapping](../../learn/edge_conputing). 
   For one-to-one mapping, just select the collection point or control point you want this measuring point to map to. 

   For formula mapping, click **Add Formula**. Then select the formula and parameters for the calculation in the pop-up.

5. If you want to map the control points to the measuring points, go to **Control** tab, select the control point you want this measuring point to map to. You can only use one-to-one mapping for control points.

   In **Control** tab, the value of AO control point cannot be set but is issued by the application directly. You can enter the value of DO control points. The DO default value is the value set by an application.

   .. image:: ../../media/edge_template_control_points.png

   You can also configure point mapping in batch by exporting and then importing *mapping.csv*. Only one-to-one mapping can be configured if you select this way. Formula mapping cannot be configured.

6. Set the **Upload Type** for the measuring points. EnOS supports the following uploading types:

   - REALTIME: Once the Edge collects a point, it will send it to the cloud immediately
   - TIMER: The Edge sends the collection point value to EnOS every specific time interval. Set the interval in **Upload Interval**.
   - CHANGE: The Edge sends the latest point value to EnOS when the value of the point changes.

### Script Processing

Select **Create** under **Script** and edit the script online in the pop-up.

You can also select **Export** to download the script template and edit it offline, and then select **Import** to upload edited script.

For scripting specifications, see [Edge Computing](../../learn/edge_specification/edge_computing)

Click **OK** to complete the script.

## Configuring a Template by Exporting/Importing

1. Select **EnOS Edge > Template**, select a template in the template list, and click **Export** to download the existing template.

2. In the downloaded JSON file, modify the values and save it. Click **Import** to upload the modified JSON file.

## Modifying Device Template

After a template is created, you can click |edit| to modify it. If the template is being used by an Edge device, you need to select the Edge devices affected by your modification after you save your changes.

.. |edit| image:: ../../media/button_edit.png

- If all the Edge devices are selected, EnOS will update the original template directly;
- If only part of the Edge devices are selected, EnOS will create a new template for the selected Edge devices, whose name is "originalTemplate Name_copy", as shown below:

.. image:: ../../media/edge_template_edit_confirm.png



<!--end-->
