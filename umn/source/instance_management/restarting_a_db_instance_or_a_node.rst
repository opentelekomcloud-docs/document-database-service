:original_name: dds_03_0003.html

.. _dds_03_0003:

Restarting a DB Instance or a Node
==================================

**Scenarios**
-------------

You may need to occasionally restart a DB instance to perform routine maintenance. For example, after modifying certain parameters, you must restart the DB instance for the modifications to take effect on the management console.

You can restart a DB instance only when its status is **Available**.

.. important::

   -  Restarting a DB instance interrupts services, so you should exercise caution when performing this operation.
   -  If you restart a DB instance, all nodes in the instance are also restarted.

Restarting a DB Instance
------------------------

#. :ref:`Log in to the DDS console. <dds_02_0043>`

#. On the **Instance Management** page, locate the target DB instance and in the **Operation** column, choose **More** > **Restart**.

   Alternatively, click the target DB instance and on the displayed **Basic Information** page, click **Restart** in the upper right corner of the page.

#. In the displayed dialog box, click **Yes**.

#. View the restart status.

   a. On the **Instance Management** page, the instance status is **Restarting**.
   b. On the **Basic Information** page, all nodes of the cluster instance cannot be restarted.

Restarting a Node (Cluster)
---------------------------

#. :ref:`Log in to the DDS console. <dds_02_0043>`

#. On the **Instance Management** page, click the target cluster instance.

#. In the **Node Information** area on the **Basic Information** page, click the **mongos**, **shard**, or **config** tab, locate the target node, and in the **Operation** column, click **Restart**.

#. In the displayed dialog box, click **Yes**.

#. View the node status.

   When one node status is **Restarting**, other nodes of the instance cannot be restarted.
