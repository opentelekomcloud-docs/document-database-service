:original_name: dds_03_0030.html

.. _dds_03_0030:

Changing a Single Node DB Instance Class
========================================

Procedure
---------

#. :ref:`Log in to the DDS console. <dds_02_0043>`

#. On the **Instance Management** page, locate the target single node instance and click **Change Instance Class** in the **Operation** column.

   Alternatively, on the **Instance Management** page, click the name of the single node instance. In the **DB Information** area on the **Basic Information** page, click **Change** to the right of the **Node Class** field.

#. On the displayed page, modify required parameters and click **Submit**.

#. View the DB instance class change result.

   -  When the CPU or memory of a DB instance is being changed, the status displayed in the **Status** column is **Changing instance class**. This process takes up to 10 minutes.
   -  In the upper right corner of the DB instance list, click |image1| to refresh the list. The instance status changes to **Available**.
   -  Go to the **Basic Information** page of the single node you scaled up and check whether the scaling process is successful in the **Configuration** area.

.. |image1| image:: /_static/images/en-us_image_0000001095974074.png
