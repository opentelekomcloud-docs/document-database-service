:original_name: dds_03_0026.html

.. _dds_03_0026:

DDS Metrics
===========

Cluster
-------

-  :ref:`Table 1 <dds_03_0026__table40856249142242>` lists the DB instance monitoring metrics.

   .. _dds_03_0026__table40856249142242:

   .. table:: **Table 1** DB instance monitoring metrics

      ======================================= =======
      Metrics                                 Unit
      ======================================= =======
      COMMAND Statements per Second           Count/s
      DELETE Statements per Second            Count/s
      INSERT Statements per Second            Count/s
      QUERY Statements per Second             Count/s
      UPDATE Statements per Second            Count/s
      GETMORE Statements per Second           Count/s
      Chunks of Shard 1                       Count
      Chunks of Shard 2                       Count
      Chunks of Shard 3                       Count
      Chunks of Shard 4                       Count
      Chunks of Shard 5                       Count
      Chunks of Shard 6                       Count
      Chunks of Shard 7                       Count
      Chunks of Shard 8                       Count
      Chunks of Shard 9                       Count
      Chunks of Shard 10                      Count
      Chunks of Shard 11                      Count
      Chunks of Shard 12                      Count
      Active Instance Connections             Count
      Chunk Migration Failures in Last 24 hrs Count
      ======================================= =======

-  The monitoring metrics of the primary nodes in the config's and shard's replica sets are as follows:

   -  :ref:`Table 2 <dds_03_0026__table884454374119>` lists the ECS monitoring metrics.

   -

      .. _dds_03_0026__table884454374119:

      .. table:: **Table 2** ECS monitoring metrics

         =========================== =======
         Metrics                     Unit
         =========================== =======
         CPU Usage                   Percent
         Memory Usage                Percent
         Network Output Throughput   bytes/s
         Network Input Throughput    bytes/s
         Disk Utilization            Percent
         IOPS                        Count/s
         Disk Read Throughput        bytes/s
         Disk Write Throughput       bytes/s
         Average Time per Disk Read  s
         Average Time per Disk Write s
         Total Disk Size             GB
         Disk Usage                  GB
         =========================== =======

   -  :ref:`Table 3 <dds_03_0026__table58063690142242>` lists database metrics.

      .. _dds_03_0026__table58063690142242:

      .. table:: **Table 3** Database metrics

         ================================================ =======
         Metrics                                          Unit
         ================================================ =======
         COMMAND Statements per Second                    Count/s
         DELETE Statements per Second                     Count/s
         INSERT Statements per Second                     Count/s
         QUERY Statements per Second                      Count/s
         UPDATE Statements per Second                     Count/s
         GETMORE Statements per Second                    Count/s
         Active Connections                               Count
         Resident Memory                                  MB
         Virtual Memory                                   MB
         Regular Asserts per Second                       Count/s
         Warning Asserts per Second                       Count/s
         Message Asserts per Second                       Count/s
         User Asserts per Second                          Count/s
         Number of Operations Queued Waiting for the Lock Count
         Operations Queued Waiting for a Read Lock        Count
         Operations Queued Waiting for a Write Lock       Count
         Page Faults                                      Count
         Slow Queries                                     Count
         Maintained Cursors                               Count
         Timeout Cursors                                  Count
         Bytes in WiredTiger Cache                        MB
         Tracked Dirty Bytes in WiredTiger Cache          MB
         Bytes Written Into Cache per Second              bytes/s
         Bytes Written From Cache per Second              bytes/s
         Oplog Window                                     h
         Oplog Growth Rate                                MB/h
         ================================================ =======

-  The monitoring metrics of the secondary or hidden nodes in the config's and shard's replica sets are as follows:

   -  The ECS monitoring metrics are the same as those of the primary nodes in the config's and shard's replica sets. For details, see :ref:`Table 2 <dds_03_0026__table884454374119>`.

   -  :ref:`Table 4 <dds_03_0026__table44287116142242>` lists database metrics.

      .. _dds_03_0026__table44287116142242:

      .. table:: **Table 4** Database metrics

         ========================================== =======
         Metrics                                    Unit
         ========================================== =======
         COMMAND Statements per Second              Count/s
         DELETE Statements per Second               Count/s
         INSERT Statements per Second               Count/s
         QUERY Statements per Second                Count/s
         UPDATE Statements per Second               Count/s
         GETMORE Statements per Second              Count/s
         Active Node Connections                    Count
         Resident Memory                            MB
         Virtual Memory                             MB
         Regular Asserts per Second                 Count/s
         Warning Asserts per Second                 Count/s
         Message Asserts per Second                 Count/s
         User Asserts per Second                    Count/s
         Operations Queued Waiting for a Lock       Count
         Operations Queued Waiting for a Read Lock  Count
         Operations Queued Waiting for a Write Lock Count
         Page Faults                                Count
         Slow Queries                               Count
         Maintained Cursors                         Count
         Timeout Cursors                            Count
         Bytes in WiredTiger Cache                  MB
         Tracked Dirty Bytes in WiredTiger Cache    MB
         Bytes Written Into Cache per Second        bytes/s
         Bytes Written From Cache per Second        bytes/s
         Replication Headroom                       s
         Replication Lag                            s
         Replicated COMMAND Statements per Second   Count/s
         Replicated UPDATE Statements per Second    Count/s
         Replicated DELETE Statements per Second    Count/s
         Replicated INSERT Statements per Second    Count/s
         ========================================== =======

-  mongos metrics are as follows:

   -  :ref:`Table 5 <dds_03_0026__table1066175075416>` lists the ECS monitoring metrics.

   -

      .. _dds_03_0026__table1066175075416:

      .. table:: **Table 5** ECS monitoring metrics

         ========================= =======
         Metrics                   Unit
         ========================= =======
         CPU Usage                 Percent
         Memory Usage              Percent
         Network Output Throughput bytes/s
         Network Input Throughput  bytes/s
         ========================= =======

   -  :ref:`Table 6 <dds_03_0026__table22601657142329>` lists database metrics.

      .. _dds_03_0026__table22601657142329:

      .. table:: **Table 6** Database metrics

         ============================= =======
         Metrics                       Unit
         ============================= =======
         COMMAND Statements per Second Count/s
         DELETE Statements per Second  Count/s
         INSERT Statements per Second  Count/s
         QUERY Statements per Second   Count/s
         UPDATE Statements per Second  Count/s
         GETMORE Statements per Second Count/s
         Active Node Connections       Count
         Resident Memory               MB
         Virtual Memory                MB
         Regular Asserts per Second    Count/s
         Warning Asserts per Second    Count/s
         Message Asserts per Second    Count/s
         User Asserts per Second       Count/s
         ============================= =======

Replica Set
-----------

-  Monitoring metrics of the primary node

   -  :ref:`Table 2 <dds_03_0026__table884454374119>` lists the ECS monitoring metrics.
   -  :ref:`Table 3 <dds_03_0026__table58063690142242>` lists database metrics.

-  Monitoring metrics of the secondary or hidden node

   -  :ref:`Table 2 <dds_03_0026__table884454374119>` lists the ECS monitoring metrics.
   -  :ref:`Table 4 <dds_03_0026__table44287116142242>` lists database metrics.
