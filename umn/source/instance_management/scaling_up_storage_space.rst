:original_name: en-us_topic_increase_storage.html

.. _en-us_topic_increase_storage:

Scaling Up Storage Space
========================

**Scenarios**
-------------

This section describes how to scale up the storage space of a DB instance to suit your service requirements.

.. note::

   -  You can scale up a DB instance a maximum of eight times.
   -  You cannot scale up a DB instance in **Creating**, **Changing instance class**, **Adding node**, or **Deleting node** status.
   -  Storage space can only be scaled up. It cannot be scaled down.
   -  If you scale up a DB instance with disks encrypted, the expanded storage space will be encrypted using the original encryption key.
   -  You cannot scale up the storage space of a config for the cluster instances.
   -  During the scale-up process, the DB instance will not restart, and your services will not be interrupted.

Cluster
-------

#. :ref:`Log in to the DDS console. <dds_02_0043>`

#. On the **Instance Management** page, click the target cluster instance.

#. In the **Node Information** area on the **Basic Information** page, click the **shard** tab, locate the target shard, and click **Scale Storage Space** in the **Operation** column.

#. On the displayed page, specify the desired storage space, and click **Submit**.

   You must add a minimum of 10 GB each time you scale up, and only multiples of 10 GB are allowed. The maximum amount of storage space is 2000 GB.

#. Check the scale-up result.

   -  This process takes up to 5 minutes. The status of the DB instance in the instance list is **Scaling up**.
   -  In the upper right corner of the DB instance list, click |image1| to refresh the list. The instance status changes to **Available**.
   -  In the **Node Information** area on the **Basic Information** page, click the **shard** tab and check whether the scale up was successful.

Replica Set
-----------

#. :ref:`Log in to the DDS console. <dds_02_0043>`

#. On the **Instance Management** page, locate the target replica set instance and click **Scale Storage Space** in the **Operation** column.

   Alternatively, you can click the target cluster instance, in the **Storage Space** area on the **Basic Information** page, click on the **Scale** button.

#. On the displayed page, specify the desired storage space, and click **Submit**.

   You must add a minimum of 10 GB each time you scale up, and only multiples of 10 GB are allowed. The maximum amount of storage space is 3000 GB.

#. Check the scale-up result.

   -  This process takes up to 5 minutes. The status of the DB instance in the instance list is **Scaling up**.
   -  In the upper right corner of the DB instance list, click |image2| to refresh the list. The instance status changes to **Available**.
   -  In the **Storage Space** area on the **Basic Information** page, check whether the scaling up is successful.

Single Node
-----------

#. :ref:`Log in to the DDS console. <dds_02_0043>`

#. On the **Instance Management** page, locate the target single node instance and click **Scale Storage Space** in the **Operation** column.

   Alternatively, you can click the target cluster instance, in the **Storage Space** area on the **Basic Information** page, click on the **Scale** button.

#. On the displayed page, specify the desired storage space and click **Submit**.

   You must add a minimum of 10 GB each time you scale up, and only multiples of 10 GB are allowed. The maximum amount of storage space is 1000 GB.

#. Check the scale-up result.

   -  This process takes up to 5 minutes. The status of the DB instance in the instance list is **Scaling up**.
   -  In the upper right corner of the DB instance list, click |image3| to refresh the list. The instance status changes to **Available**.
   -  In the **Storage Space** area on the **Basic Information** page, check whether the scaling up is successful.

.. |image1| image:: /_static/images/en-us_image_0000001095974074.png
.. |image2| image:: /_static/images/en-us_image_0000001095974076.png
.. |image3| image:: /_static/images/en-us_image_0000001095974074.png
