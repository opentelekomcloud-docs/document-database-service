:original_name: dds_03_0018.html

.. _dds_03_0018:

Reverting and Deleting Failed Cluster Instance Nodes
====================================================

Scenarios
---------

This section describes how to revert nodes that fail to be added.

Reverting Nodes in Batches
--------------------------

#. :ref:`Log in to the DDS console. <dds_02_0043>`

#. On the **Instance Management** page, locate the cluster instance to which nodes fail to be added and choose **More** > **Revert** in the **Operation** column.

#. In the displayed dialog box, click **Yes**.

   During reversal, the instance status is **Deleting node**. This process takes about 1 to 3 minutes.

Deleting Failed Cluster Instance Nodes
--------------------------------------

#. :ref:`Log in to the DDS console. <dds_02_0043>`

#. On the **Instance Management** page, click the target cluster instance to which the node fails to be added.

#. In the **Node Information** area on the **Basic Information** tab, click the **mongos** or **shard** tab, locate the mongos or shard that failed to be added, and choose **More** > **Delete**.

#. In the displayed dialog box, click **Yes**.

   During deletion, the node status is **Deleting node**. This process takes about 1 to 3 minutes.
