:original_name: en-us_topic_increase_storage.html

.. _en-us_topic_increase_storage:

Scaling Up Storage Space
========================

**Scenarios**
-------------

This section guides you on how to scale up the storage space of a DB instance to suit your service requirements.

.. note::

   -  You can scale up a DB instance a maximum of eight times.
   -  You cannot scale up a DB instance in **Creating**, **Changing instance class**, **Adding node**, or **Deleting node** status.
   -  You cannot scale down storage space.
   -  If you scale up a DB instance with disks encrypted, the expanded storage space will be encrypted using the original encryption key.
   -  You cannot scale up the storage space of a config for the cluster instances.

Cluster
-------

#. :ref:`Log in to the DDS console. <dds_02_0043>`

#. On the **Instance Management** page, click the target cluster instance.

#. In the **Node Information** area on the **Basic Information** page, click the **shard** tab, locate the target shard, and click **Scale Storage Space** in the **Operation** column.

#. On the displayed page, specify the desired storage space, and click **Submit**.

   You must add a minimum of 10 GB each time you scale up, and only multiples of 10 GB are allowed. The maximum amount of storage space is 1,000 GB.

#. Check the scaling-up result.

   -  This process takes about 3 to 5 minutes. The status of the DB instance in the instance list is **Scaling up**.
   -  In the upper right corner of the DB instance list, click |image1| to refresh the list. The instance status changes to **Available**.
   -  In the **Node Information** area on the **Basic Information** page, click the **shard** tab and check whether the scaling up is successful.

Replica Set
-----------

#. :ref:`Log in to the DDS console. <dds_02_0043>`

#. On the **Instance Management** page, locate the target replica set instance and click **Scale Storage Space** in the **Operation** column.

#. On the displayed page, specify the desired storage space, and click **Submit**.

   You must add a minimum of 10 GB each time you scale up, and only multiples of 10 GB are allowed. The maximum amount of storage space is 2,000 GB.

#. Check the scaling-up result.

   -  This process takes about 3 to 5 minutes. The status of the DB instance in the instance list is **Scaling up**.
   -  In the upper right corner of the DB instance list, click |image2| to refresh the list. The instance status changes to **Available**.
   -  In the **Storage Space** area on the **Basic Information** page, check whether the scaling up is successful.

.. |image1| image:: /_static/images/en-us_image_0284275046.png
.. |image2| image:: /_static/images/en-us_image_0284275173.png
