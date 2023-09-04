:original_name: en-us_topic_0104721795.html

.. _en-us_topic_0104721795:

Changing a Replica Set DB Instance Class
========================================

Procedure
---------

#. :ref:`Log in to the DDS console. <dds_02_0043>`

#. On the **Instance Management** page, locate the replica set instance and choose **More** > **Change Instance Class** in the **Operation** column.

   Alternatively, on the **Instance Management** page, click the name of the replica set instance. In the **DB Information** area on the **Basic Information** page, click **Change** to the right of the **Node Class** field.

#. On the displayed page, modify required parameters and click **Submit**.

#. View the DB instance class change result.

   -  When the CPU or memory of a DB instance is being changed, the status displayed in the **Status** column is **Changing instance class**. This process takes up to 30 minutes.
   -  In the upper right corner of the DB instance list, click |image1| to refresh the list. The instance status changes to **Available**.
   -  Go to the **Basic Information** page of the replica set instance you scaled up and check whether the scaling up is successful in the **DB Information** area.

.. |image1| image:: /_static/images/en-us_image_0000001095974074.png
