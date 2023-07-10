:original_name: dds_01_0006.html

.. _dds_01_0006:

Functions and Features
======================

Three Architectures
-------------------

DDS supports three deployment architectures: cluster, replica set, and single node. They meet requirements of different service scenarios.

-  Cluster

   A cluster consists of three types of nodes: mongos, shard, and config. You can select the number and configuration of mongos and shard nodes to create cluster instances with different levels of service performance.

-  Replica set

   DDS automatically builds the replica set architecture, and you can directly operate the primary and secondary nodes. DDS provides you with advanced functions such as high availability (HA) and disaster recovery (DR) switchover, and is invisible to applications.

-  Single node

   A database that is deployed on a single VM does not have the HA feature. To ensure data consistency during full backup, tables are locked to prevent data from being changed. The single-node architecture features low costs and is a preferred option for R&D and testing environment, learning and training environment, and internal systems of small-sized enterprises.

Elastic Scaling
---------------

With the development of your services, you can change CPU and memory specifications of instances, expand storage space, and add mongos and shard nodes of cluster DB instances in real time. You are advised to perform the change during off-peak hours to avoid the impact of changes on your services.

Key Features
------------

.. table:: **Table 1** Key feature description

   +--------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Features                                   | Description                                                                                                                                                                                                                                                                              |
   +============================================+==========================================================================================================================================================================================================================================================================================+
   | SLA                                        | 99.95%                                                                                                                                                                                                                                                                                   |
   +--------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Instant availability                       | You can create a DB instance on the management console and access DDS through an Elastic Cloud Server (ECS) to reduce the application response time. If you need to access a DB instance from your local devices, you can bind an elastic IP address (EIP) to the instance.              |
   +--------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | High compatibility                         | DDS is a document-oriented NoSQL database. It is fully compatible with MongoDB.                                                                                                                                                                                                          |
   +--------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Visualized operation and maintenance (O&M) | You can easily perform restart, backup, and data recovery operations on instances using a graphical user interface (GUI)                                                                                                                                                                 |
   +--------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Data security                              | -  A security protection system consists of VPCs, subnets, security groups, storage encryption, SSL, and DDoS protection, which is capable of defending against various malicious attacks and ensuring data security.                                                                    |
   |                                            | -  DDS supports fine-grained permission control.                                                                                                                                                                                                                                         |
   +--------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | High availability                          | The cluster and replica set support high availability. If the primary node is faulty, the secondary node takes over services in a short time. The switchover process is invisible to applications.                                                                                       |
   +--------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Metric monitoring                          | DDS monitors key performance metrics of DB instances and DB engines in real time, including the CPU usage, memory usage, storage space usage, command execution frequency, delete statement execution frequency, insert statement execution frequency, and number of active connections. |
   +--------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Backups and restorations                   | -  DDS supports automated backup and manual backup. The maximum retention period of an automated backup is 732 days. There is no limit on the manual backup retention period. You can delete manual backup files as needed.                                                              |
   |                                            | -  DB instances can be restored using backup data.                                                                                                                                                                                                                                       |
   +--------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Setting parameters                         | DDS allows you to manage parameter Templates and modify configuration parameters on the console.                                                                                                                                                                                         |
   +--------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
