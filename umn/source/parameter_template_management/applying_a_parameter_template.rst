:original_name: dds_03_0014.html

.. _dds_03_0014:

Applying a Parameter Template
=============================

Modifications to parameters in a custom parameter template take effect for DB instances only after you have applied the template to the target DB instances or target nodes.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select a region and a project.

#. Click **Service List**. Under **Database**, click **Document Database Service** to go to the DDS console.

#. In the navigation pane on the left, click **Parameter Template Management**.

#. On the **Parameter Template Management** page, apply a default template or a custom template to the target DB instance:

   -  To apply a default template, click the **Default Templates** tab, locate the required parameter template, and click **Apply** in the **Operation** column.
   -  To apply a custom template, click **Custom Templates**, locate the target parameter template, and in the **Operation** column, choose **More** > **Apply**.

   A parameter template can be applied to one or more nodes and instances.

#. In the displayed dialog box, select the node or instance to which the parameter template will be applied and click **OK**.

   -  After the parameter template is successfully applied, you can view the application records by referring to :ref:`Viewing Application Records of a Parameter Template <dds_03_0113>`.
   -  For some parameters a reboot of target nodes or the target DB instance could be required, see :ref:`Restarting a DB Instance or a Node <dds_03_0003>`.

.. |image1| image:: /_static/images/en-us_image_0000001268771757.png
