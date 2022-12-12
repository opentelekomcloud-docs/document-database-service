:original_name: dds_03_0050.html

.. _dds_03_0050:

Manually Switching the Primary and Secondary Nodes of a Replica Set
===================================================================

**Scenarios**
-------------

A replica set consists of the primary node, secondary node, and hidden node. Primary and secondary nodes allow access from external services by providing IP addresses. Hidden nodes are only used for backing up data. When a primary node becomes faulty, the system automatically selects a new primary node to ensure high availability. In addition, DDS supports the primary/secondary switchover so you can perform switchovers in scenarios such as disaster recovery.

.. note::

   -  You can perform a switchover when the DB instance status is **Available**, and **Changing a security group**.
   -  Services may be interrupted during the switchover. Ensure that your client supports reconnection.
   -  The longer the delay for primary/secondary synchronization, the more time is needed for a primary/secondary switchover. Therefore, if the primary to secondary synchronization delay exceeds 300s, the primary/secondary switchover is not allowed. For details about the delay for the primary/secondary synchronization, see :ref:`What Is the Time Delay for Primary/Secondary Synchronization in a Replica Set? <dds_faq_0006>`

Procedure
---------

#. :ref:`Log in to the DDS console. <dds_02_0043>`
#. On the **Instance Management** page, click the target replica set instance.
#. In the **Node Information** area on the **Basic Information** page, click **Switch**.
#. In the displayed dialog box, click **Yes**.
#. Check the result.

   -  During the switchover process, the DB instance status changes to **Switchover in progress**. After the switchover is complete, the status is restored to **Available**.
   -  In the **Node Information** area, you can view the switchover result.
   -  After the switchover, the previous primary node becomes the secondary node. You need to reconnect to the primary node. For details, see :ref:`Connecting to a DB Instance Through a Client <en-us_topic_0105284966>`.
