:original_name: en-us_topic_0104472218.html

.. _en-us_topic_0104472218:

Changing a Cluster DB Instance Class
====================================

Changing mongos
---------------

#. :ref:`Log in to the DDS console. <dds_02_0043>`
#. On the **Instance Management** page, click the target cluster instance.
#. In the **Node Information** area on the **Basic Information** page, click the **mongos** tab, locate the target mongos, and click **Change Instance Class** in the **Operation** column.
#. On the displayed page, select the new instance class and click **Submit**.
#. View the DB instance class change result.

   -  When the CPU or memory of a DB instance is being changed, the status displayed in the **Status** column is **Changing instance class**. This process takes up to 10 minutes.
   -  In the upper right corner of the DB instance list, click |image1| to refresh the list. The instance status changes to **Available**.
   -  In the **Node Information** area on the **Basic Information** page, click the **mongos** tab and view the new instance class.

Changing shard
--------------

#. :ref:`Log in to the DDS console. <dds_02_0043>`
#. On the **Instance Management** page, click the target cluster instance.
#. In the **Node Information** area on the **Basic Information** page, click the **shard** tab, locate the target shard, and click **Change Instance Class** in the **Operation** column.
#. On the displayed page, select the new instance class and click **Submit**.
#. View the DB instance class change result.

   -  When the CPU or memory of a DB instance is being changed, the status displayed in the **Status** column is **Changing instance class**. This process takes up to 30 minutes.
   -  In the upper right corner of the DB instance list, click |image2| to refresh the list. The instance status changes to **Available**.
   -  Go to the **Basic Information** page of the cluster instance you scaled up, click the **shard** tab in the **Node Information** area, and view the new instance class.

.. |image1| image:: /_static/images/en-us_image_0000001095974074.png
.. |image2| image:: /_static/images/en-us_image_0000001095974074.png
