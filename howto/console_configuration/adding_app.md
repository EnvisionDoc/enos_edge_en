# Adding and Lauching an Application on Edge

As an edge computing platform, EnOS Edge supports application management. You can let your application read from and write to all asset data on Edge and use the APIs of Edge.

## About This Task

This topic introduces how to add an app to EnOS Edge and launch the app online.

## Before You Begin

- Obtain the access to Edge management. If you don't have the access, contact your OU administrator. For more information, see [Policies, Roles and Permissions](/docs/iam/en/latest/access_policy).
- Register an app on EnOS Cloud. For more information, see [Managing Application](/docs/app-development/en/latest/managing_apps).

## Procedure

1. Select **EnOS Edge > Edge Management** . Click **View** for the Edge you want to add an app to in the **Operations** column.

 .. image:: ../../media/adding_app_1.png

2. Select **Application** tab. Click **Add app** .

 .. image:: ../../media/adding_app_2.png

3. Select one or multiple apps from the list of all apps registered on this OU which has not been added to this Edge instance. Click **Confirm** .

  You can add an app that has been added to another Edge instance.

  The selected app has been added to this app.

 .. image:: ../../media/adding_app_3.png

4. Click |online| in the **Operations** column and confirm your operation.

 .. |online| image:: ../../media/button_online.png


## Results

You have added the selected app or apps to the Edge instance and granted access to read from, write to the asset data on Edge, and call APIs. To fully run your app on Edge, you still need to deploy the app on Edge.

.. image:: ../../media/adding_app_4.png

## Next Step

- [Managing Applications on Edge](managing_app).

