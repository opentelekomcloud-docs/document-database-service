:original_name: dds_01_0024.html

.. _dds_01_0024:

DB Instance Specifications
==========================

DB instance specifications are listed in the following table.

.. note::

   DB instance specifications vary depending on the actual environment.

Cluster
-------

For details about the cluster instance specifications, see :ref:`Table 1 <dds_01_0024__table147993911564>` and :ref:`Table 2 <dds_01_0024__table196721422132317>`.

.. _dds_01_0024__table147993911564:

.. table:: **Table 1** config specifications

   =============== =========== ==========================
   Number of vCPUs Memory (GB) Max. Number of Connections
   =============== =========== ==========================
   2               4           1000
   =============== =========== ==========================

.. _dds_01_0024__table196721422132317:

.. table:: **Table 2** shard and mongos specifications

   =============== =========== ==========================
   Number of vCPUs Memory (GB) Max. Number of Connections
   =============== =========== ==========================
   1               4           400
   2               8           400
   4               16          1000
   8               32          4000
   16              64          8000
   =============== =========== ==========================

Replica Set
-----------

The supported replica set specifications are the same as those of shard and mongos nodes. For details, see :ref:`Table 2 <dds_01_0024__table196721422132317>`.
