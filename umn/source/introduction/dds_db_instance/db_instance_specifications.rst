:original_name: dds_01_0024.html

.. _dds_01_0024:

DB Instance Specifications
==========================

DB instance specifications are listed in the following table.

.. note::

   The DB instance specifications depend on service requirements.

   You can change the maximum number of connections of a DB instance by modifying the **net.maxIncomingConnections** parameter. For details about how to change the parameter value, see :ref:`Modifying a Parameter Template <en-us_topic_configuration>`.

.. _dds_01_0024__section87233314314:

Cluster
-------

For details about the cluster instance specifications, see :ref:`Table 1 <dds_01_0024__table93922044142815>` and :ref:`Table 2 <dds_01_0024__table3885614174718>`.

.. _dds_01_0024__table93922044142815:

.. table:: **Table 1** config specifications

   ======== ===== =========== =====================================
   CPU Type vCPUs Memory (GB) Default Maximum Number of Connections
   ======== ===== =========== =====================================
   x86      2     4           600
   Kunpeng
   ======== ===== =========== =====================================

.. _dds_01_0024__table3885614174718:

.. table:: **Table 2** shard and dds mongos specifications

   ===== =========== =====================================
   vCPUs Memory (GB) Default Maximum Number of Connections
   ===== =========== =====================================
   1     4           400
   2     8           400
   4     16          1000
   8     32          4000
   16    64          8000
   ===== =========== =====================================

Replica Set
-----------

The specifications supported by a replica set are the same as those supported by shard and dds mongos. For details, see :ref:`Table 2 <dds_01_0024__table3885614174718>`.

Single Node
-----------

The specifications supported by a single node are the same as those supported by shard and dds mongos. For details, see :ref:`Table 2 <dds_01_0024__table3885614174718>`.
