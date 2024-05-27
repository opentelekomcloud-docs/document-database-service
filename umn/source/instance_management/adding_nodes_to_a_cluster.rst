:original_name: en-us_topic_increase_nodes.html

.. _en-us_topic_increase_nodes:

Adding Nodes to a Cluster
=========================

**Scenarios**
-------------

This section describes how to add nodes to a cluster instance.

.. note::

   -  You can add nodes when the instance status is **Available**, **Deleting backup**, or **Checking restoration**.
   -  A DB instance cannot be deleted when nodes are being added.
   -  dds mongos and shard nodes that are successfully added cannot be deleted.

Add dds mongos
--------------

#. :ref:`Log in to the DDS console. <dds_02_0043>`

#. On the **Instance Management** page, click the target cluster instance.

#. On the dds mongos tab in the **Node Information** area, click **Add dds mongos**.

#. On the displayed page, specify **Node Class**, **Nodes**, and **Parameter Template** and click **Submit**.

   A cluster instance of Community Edition supports up to 32 dds mongos nodes.

#. View the result of adding nodes.

   -  This process takes up to 15 minutes. The status of the DB instance in the instance list is **Adding node**.
   -  In the upper right corner of the DB instance list, click |image1| to refresh the list. The instance status changes to **Available**.
   -  On the dds mongos tab in the **Node Information** area, view the information about the node you added.
   -  If the dds mongos fail to be added, you can revert them in batches or delete them one by one. For details, see section :ref:`Reverting and Deleting Failed Cluster Instance Nodes <dds_03_0018>`.

Add shard
---------

#. :ref:`Log in to the DDS console. <dds_02_0043>`
#. On the **Instance Management** page, click the target cluster instance.
#. On the **shard** tab in the **Node Information** area, click **Add shard**.
#. Specify **Node Class**, **Storage Space**, **Nodes**, and **Parameter Template** and click **Submit**.

   -  The storage space you applied for will contain the system overhead. The storage space can be configured from 10 GB to 2000 GB and must be an integer multiple of 10.
   -  A cluster instance of Community Edition supports up to 32 shard nodes.

#. View the result of adding nodes.

   -  This process takes up to 15 minutes. The status of the DB instance in the instance list is **Adding node**.
   -  In the upper right corner of the DB instance list, click |image2| to refresh the list. The instance status changes to **Available**.
   -  On the **shard** tab in the **Node Information** area, view the information about the node you added.
   -  If the shards fail to be added, you can revert them in batches or delete them one by one. For details, see section :ref:`Reverting and Deleting Failed Cluster Instance Nodes <dds_03_0018>`.

.. |image1| image:: /_static/images/en-us_image_0000001142773957.png
.. |image2| image:: /_static/images/en-us_image_0000001142773957.png
