:original_name: en-us_topic_0104472218.html

.. _en-us_topic_0104472218:

Changing the CPU or Memory of a Cluster DB Instance
===================================================

Scenarios
---------

This section guides you on how to change the CPU or memory of a cluster instance.

.. note::

   -  A DB instance cannot be deleted when you are changing its CPU or memory.
   -  Instances can be both scaled up and down.
   -  Services will be interrupted for 5 to 10 minutes when you change DB instance CPU and memory. You are advised to perform this operation during off-peak hours.

Changing mongos
---------------

#. :ref:`Log in to the DDS console. <dds_02_0043>`
#. On the **Instance Management** page, click the target cluster instance.
#. In the **Node Information** area on the **Basic Information** page, click the **mongos** tab, locate the target mongos, and click **Change Instance Class** in the **Operation** column.
#. On the displayed page, modify required parameters and click **Submit**.
#. View the DB instance CPU or memory modification result.

   -  When the CPU or memory of a DB instance is being changed, the status displayed in the **Status** column is **Changing instance class**. This process takes about 10 minutes.
   -  In the upper right corner of the DB instance list, click |image1| to refresh the list. The instance status changes to **Available**.
   -  In the **Node Information** area on the **Basic Information** page, click the **mongos** tab and check whether the scaling up is successful.

Changing shard
--------------

#. :ref:`Log in to the DDS console. <dds_02_0043>`
#. On the **Instance Management** page, click the target cluster instance.
#. In the **Node Information** area on the **Basic Information** page, click the **shard** tab, locate the target shard, and click **Change Instance Class** in the **Operation** column.
#. On the displayed page, modify required parameters and click **Submit**.
#. View the DB instance CPU or memory modification result.

   -  When the CPU or memory of a DB instance is being changed, the status displayed in the **Status** column is **Changing instance class**. This process takes about 25 to 30 minutes.
   -  In the upper right corner of the DB instance list, click |image2| to refresh the list. The instance status changes to **Available**.
   -  Go to the **Basic Information** page of the cluster instance you scaled up, click the **shard** tab in the **Node Information** area, and check whether the scaling up is successful.

.. |image1| image:: /_static/images/en-us_image_0284275046.png
.. |image2| image:: /_static/images/en-us_image_0284275046.png
