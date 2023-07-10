:original_name: dds_01_0015.html

.. _dds_01_0015:

Typical Application Scenarios
=============================

Games
-----

Game players' information generated from game applications, such as players' equipment and bonus points, are stored in DDS databases. During peak hours, DDS cluster instances can handle large amounts of concurrent requests. DDS cluster and replica set provide high availability to ensure the stable running of games in high-concurrency scenarios.

In addition, DDS is compatible with MongoDB and provides the non-schema mode, which frees you from changing table structure when the game play mode changes. DDS can totally meet the flexible gaming requirements. You can store structured data with fixed patterns in RDS, services with flexible patterns in DDS, and hot data in Distributed Cache Service (DCS) to facilitate access to service data and reduce data storage costs.

Advantages:

-  Supports embedded documents that eliminate the need to use joins to reduce application development complexity. Flexible schemas also facilitate rapid development and iteration.
-  Sharded clusters provide enough capacity to store data into the TB range.

IoT
---

DDS is compatible with MongoDB and provides the high-performance and asynchronous data write function. In certain scenarios, DDS can process data in the memory database. In addition, cluster instances can dynamically add the number of mongos and shard nodes or upgrade specifications. The performance and storage space can be quickly expanded, making cluster instances suitable for IoT scenarios with high concurrent writes.

Intelligent IoT terminals need to collect various types of data, store device logs, and analyze information in multiple dimensions. In recent years, IoT services have grown rapidly, with huge volumes of data and increasing access traffic that require horizontal expansion capabilities for data storage.

DDS provides the secondary index to meet dynamic query requirements and uses the MapReduce aggregation framework that is compatible with MongoDB to analyze data from multiple dimensions.

Advantages:

-  **High Write Performance**: DDS sharded cluster provides high write performance to meet the requirements of terabyte-scale databases.
-  **High Performance and Scalability**: DDS supports applications with high QPS rates, and its sharding architecture can be scaled in or out to flexibly cope with application changes.

Internet
--------

DDS replica set uses the three-node HA architecture. Three data nodes form an anti-affinity group and are deployed on different physical servers to automatically synchronize data. The primary and secondary nodes provide services. Each node has a private IP address and works with Driver to allocate read workloads.

Many organizations need to process and store data into the TB range, requiring data to be written to databases in real time and dynamic analysis capabilities in big data computing.

Advantages:

-  **MapReduce:** With a complete data analysis utility, you can query statements or scripts, and distribute requests to DDS.
-  **Excellent Scalability**: DDS DB instances can be scaled up to support growing services and data volumes in content management systems.
