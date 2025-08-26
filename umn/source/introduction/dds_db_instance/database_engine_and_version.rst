:original_name: dds_01_0014.html

.. _dds_01_0014:

Database Engine and Version
===========================

DDS supports versions 4.0, 4.2, 4.4 and 5.0, and you need to use a driver compatible with MongoDB 3.0 or later to access DDS. You can select the DB engine and version you need based on your service requirements.

.. table:: **Table 1** Supported DB engines and versions

   +-----------------------+-----------------------+-----------------------+
   | Compatibility         | DB Instance Type      | Storage Engine        |
   +=======================+=======================+=======================+
   | 5.0                   | -  Cluster            | RocksDB               |
   |                       | -  Replica set        |                       |
   +-----------------------+-----------------------+-----------------------+
   | 4.4                   | -  Cluster            | RocksDB               |
   |                       | -  Replica set        |                       |
   |                       | -  Single             |                       |
   +-----------------------+-----------------------+-----------------------+
   | 4.2                   | -  Cluster            | RocksDB               |
   |                       | -  Replica set        |                       |
   |                       | -  Single             |                       |
   +-----------------------+-----------------------+-----------------------+
   | 4.0                   | -  Cluster            | WiredTiger            |
   |                       | -  Replica set        |                       |
   |                       | -  Single             |                       |
   +-----------------------+-----------------------+-----------------------+
