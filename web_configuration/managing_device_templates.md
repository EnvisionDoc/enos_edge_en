# Managing Device Templates

A device template is the bridge for device connection, which comprises
two parts:

- The mapping between the standard model points and the actually acquisition points of the device instance

- The protocol that is used for connecting the device.

For an actual device, in most cases, the names of the data acquisition points are specified by customers and the system cannot recognize the customer-specified names. Therefore, you need to configure the mapping between the standard device model points and the corresponding actual data acquisition points. As the same time, you need to configure the communication protocol for device connection.

Creating of the device template mainly includes three parts:

.. image:: media/image035.png
   :alt: Figure: Process of managing device template
   

Device template can be created in two ways:

- Create from scratch

- Create based on a existing device template. If the two device
 templates are similar, you can reduce you workload by cloning and
 modifing the existing device template.

## Creating from Scratch

To create a device template from scratch, do the following steps:

1. Click Template Lib > Add.

2. Enter the basic information of fthe device in the pop-up windows.

3. Click **Save**.

   .. image:: media/image036.png
      :alt: Figure: New Creation of Device Template
      

4. Click |add| of the newly adding device.

   .. |add| image:: media/image037.png

5. In the **Device Detail** page, you can find the following information.

   - The basic information of the template,

   - The configuration bar

   - The model selection and mappings

   .. image:: media/image038.png
      :alt: Figure: Example of the Device Template Edit Page with Wind turbine information.
      

### Providing the Basic Information

Enter in the basic information, select the type and specific protocol.

1. Select the protocol type.

2. Select the specific protocol in that type.

   For more detailed information about protocol configuration, see the related chapter.

   .. image:: media/image039.png
      :alt: Figure: Edit Basic Information of Template
      

3. (Optional)Click **Details** to check the details of the protocal.

4. (Optional) In the pop-up dialog box, click the |view| icon to view information for each protocol that helps you determine the protocol to use. If you do not find the appropriate protocol, contact the system administrator.

   .. |view| image:: media/image040.png

   .. image:: media/image041.png
      :alt: Figure: Details page
      

### Uploading Point Table

The **Config.sys** file defines parameters related to the communication protocol.

The **Point.csv** file contains the actual aquisition points of the device.

1. Download the config.sys template and the point.csv template respectively.

   .. image:: media/image042.png
      :alt: Figure: Download Template
      

2. Open the files locally and modify the parameters.

3. Upload the templates.

   .. note:: If you have completed communication protocol selection in the previous section, after you upload the point.csv table, you can preview the acquisition points information in point.csv in the preview area as shown below.

   .. image:: media/image043.png
      :alt: Figure: Upload the template
      

   .. note:: Point.csv Point table must be formatted in UTF-8 BOM, incorrect format might cause problems such as display errors.

   If the alias column has values in the point.csv table，you need to import an empty table to override the original point table and then update the actually point table to avoid errors.

### Mapping Model Points to Acquisition Points

To map the standard model points to the customer-defined actual data
acquisition points, do the following steps:

1. Select the device model.

2. For each model point, click |mapping| of in the **Mappings** column.

   .. |mapping| image:: media/image044.png

   .. image:: media/image045.png
      :alt: Figure: Standard Model Selection and Mapping Relation Configuration
      

3. In the window that pops out, enter keywords of the data aquisition point in the search bar and locate the point to map to. Click **OK** to complete mapping one point.

   .. image:: media/image046.png
      :alt: Figure: Mapping Relation Configuration
      

   For simple direct mapping relation, select the corresponding acquisition point.

   For complex mapping relation, click **Add Formula** to configure the mapping formula, which is shown in the following figure:

   .. image:: media/image047.png
      :alt: Figure: Add Formula Button
      

4. Add formula (for complicated mapping relation).

   .. image:: media/image048.png
      :alt: Figure: Formula Selection
      

   The following is an example of adding the "SUM" formula.

   a.  Select **SUM** for Algorithm.

   b.  In the **Select Point** column, click |049| for each point to add up.

   .. image:: media/image050.png
      :alt: Figure: The description of the formula addition
      

   .. note:: The sequence that the points are added is important for some formulas. For example, the **CROSS\_PRODUCT** fomula, if the sequence that the points are selected is: ai.0, ai4, ai8, ai12, the formula would be \"(ai. 0 \* ai. 4 + ai. 8 \* ai. 12)\".

   The operand config in the following screenshot is similar to the coefficiency: 0 indicates no operation, 0.01 indicates the formula would be \"(ai. 0 \* ai. 4 + ai. 8 \* ai. 12) \* 0.01\".

   .. image:: media/image051.png
      :alt: Figure: Select sequence and operands
      

#### Configuring Mapping Relation in Batches

1. Click **Export** to download the point mapping table.

   .. image:: media/image052.png
      :alt: Figure: Configure Mapping Relation in Batches
      

   .. image:: media/image053.png
      :alt: Figure: Mapping Relation Table
      

2. In the table, enter the name of the data acquisition point to map to for each model point. The mdesp column refers to the description of the acquisition point, which can be left empty.

3. Save and upload the table.

4. After you have successfully uploaded the mapping table, download the domain point list to obtain a table that contains the mapping relations. The table will also contain the description of the aquisition points (because the description can be automatically acquired from the configuration file point.csv).

5. Information of the model points and aquisition points can be viewed in the page, which is as shown in the following figure. Click **Save** to complete configuration of the device template.

   .. image:: media/image045.png
      :alt: Figure: Configure Mapping Relation
      


.. note:: - Not all model points need to be related to an aquisition point. Perform configuration based on your needs.
   - The points that need to be mapped through formulas must be configured manually instead of through the import/export operations.
   - In the exported mapping relation table,the points that are mapped through formulas do not appear in the exported CSV file, but the formula exists in the backstage.


## Creating Device Template by Cloning Existing Template

To create a device template by cloning an existing template:

1. In the **Template lib** page, you can view all device templates that you have access to.

2. Find the device template to clone and click **Copy**.

3. Enter in the unique name of the new device template.

4. Modify the device template according to your needs.

.. note:: The device template name must be unique, otherwise, an error will be reported.

.. image:: media/image054.png
   :alt: Figure: Copy Device Template
   

.. image:: media/image055.png
   :alt: Figure: Enter the Template Name
   

## Modifying Device Template

From the **Template Lib** page, click the edit icon to enter the device template detail page as shown in the following figure.

.. image:: media/image056.png
   

As the same device template might be shared by devices from different sites of a client, the modification to the device template can affect several sites. If only part of the sites want adopt the modified device tempate while the other sites want to retain the original device template, a mechanism is needed to support the scenairo. The mechanism is described as follows:

When you are modifying the device template, you can view the sites that are using this device template within your authorized scope of sites.
You can determine whether to apply the change to all or only partial of the relevant sites.

- If the change applies to all relevant sites, directly modify the original device template.

- If the change applies to only part of the relevant sites, generate new device templates for the affected sites.

In the **Template Lib**. page, click |057| (the associate icon) to open a dialog box to view the sites that are using the template.

.. image:: media/image058.png
   :alt: Figure: View the Associated Sites
   

After you modify the template, click **Save** and you'll be prompted to
select which sites to apply the change to.

- When you select all, the original template is directly modified.

- When you select only part of the sites that are listed in the dialog box, a new device template is generated for each site that are affected. The original device template remains unchanged and is associated only to the the unaffected sites as shown in following figure:

.. image:: media/image059.png
   :alt: Figure: Select the Sites to Be Affected
   

.. |049| image:: media/image049.png

.. |057| image:: media/image057.png

<!--end-->
