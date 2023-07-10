:original_name: en-us_topic_configuration.html

.. _en-us_topic_configuration:

Modifying a Parameter Template
==============================

You can modify parameters in custom parameter templates as needed to get the most out of DDS performance.

You can modify parameters in either of the following ways:

-  Directly modify the parameters of a specified instance.

   If you change a dynamic parameter value in a parameter template and save the change, the change takes effect immediately regardless of the **Effective upon Reboot** setting. If you modify static parameters on the **Parameters** page of an instance and save the modifications, the modifications take effect only after you manually restart the target instance.

-  Modify the parameters in a parameter template and apply the template to the instance.

   The changes only take effect after you apply the template to the instance. If you modify static parameters in a custom parameter template on the **Parameter Template Management** page and save the modifications, the modifications take effect only after you apply the parameter template to instances and manually restart the instances. For operation details, see :ref:`Applying a Parameter Template <dds_03_0014>`.

Precautions
-----------

-  You can change parameter values in custom parameter templates but cannot change the default parameter templates provided by the system. You can only click the name of a default parameter template to view its details.
-  If a custom parameter template is set incorrectly, the instance associated with the template may fail to start. You can re-configure the custom parameter template according to the configurations of the default parameter template.

Modifying Parameters of an Instance
-----------------------------------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select a region and a project.

#. Click **Service List**. Under **Database**, click **Document Database Service** to go to the DDS console.

#. In the navigation pane on the left, choose **Instance Management**. On the displayed page, click the DB instance whose parameters you wish to modify.

#. In the navigation pane on the left, choose **Parameters**. On the displayed page, modify parameters as required.

   -  To save the modifications, click **Save**.
   -  If you want to cancel the modifications, click **Cancel**.
   -  If you want to preview the modifications, click **Preview**.

#. After parameters are modified, click **Change History** to view parameter modification details.

   For details about how to view parameter modification details, see :ref:`Viewing Parameter Change History <dds_03_0110>`.

   .. important::

      After you modify instance parameters, the modifications immediately take effect for the instance.

      Check the value in the **Effective upon Restart** column.

      -  If the value is **Yes** and the instance status on the **Instance Management** page is **Pending restart**, restart the DB instance for the modifications to take effect.
      -  If the value is **No**, the modifications take effect immediately.

Modifying Parameters in a Custom Parameter Template
---------------------------------------------------

#. Log in to the management console.

#. Click |image2| in the upper left corner and select a region and a project.

#. Click **Service List**. Under **Database**, click **Document Database Service** to go to the DDS console.

#. In the navigation pane on the left, click **Parameter Template Management**.

#. On the **Parameter Template Management** page, click **Custom Templates**. Select the **Clusters**, **Replica Sets**, or **Single Nodes** sub-tab and click the parameter template you created.

#. Modify the required parameters.

   -  If you want to save the modifications, click **Save**.
   -  If you want to cancel the modifications, click **Cancel**.
   -  If you want to preview the modifications, click **Preview**.

#. After parameters are modified, click **Change History** to view parameter modification details.

   For details about how to view parameter modification details, see :ref:`Viewing Parameter Change History <dds_03_0110>`.

   .. important::

      -  The modifications take effect only after you apply the parameter template to instances. For details, see :ref:`Applying a Parameter Template <dds_03_0014>`.
      -  The change history page displays only the modifications of the last seven days.
      -  For details about the parameter template statuses, see :ref:`DB Instance Status <dds_01_0026>`.
      -  After modifying a parameter, view the associated instance status in the instance list. If **Pending restart** is displayed, restart the instance for the modification to take effect. For details, see :ref:`Restarting a DB Instance or a Node <dds_03_0003>`.

.. |image1| image:: /_static/images/en-us_image_0000001268771757.png
.. |image2| image:: /_static/images/en-us_image_0000001268771757.png
