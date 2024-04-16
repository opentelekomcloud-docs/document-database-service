:original_name: dds_01_0011.html

.. _dds_01_0011:

Cluster
=======

Each DDS cluster is an independent document database. A sharded cluster consists of a config node, and multiple dds mongos and shard nodes.

Data read and write requests are forwarded by the dds mongos nodes, which read configuration settings from config, and then allocate the read and write requests to the shards, making it easy to cope with high concurrency scenarios. In addition, each config node, along with the shards in its cluster, is replicated in triplicate to ensure high availability. The following figure shows the DDS cluster architecture.


.. figure:: /_static/images/en-us_image_0000001891581965.png
   :alt: **Figure 1** Cluster architecture

   **Figure 1** Cluster architecture

-  A driver handles all interactions between your application and the database in a language appropriate to the application. For details, see `official documents <https://docs.mongodb.com/drivers/>`__.
-  Each dds mongos is a single node, but you can provision multiple dds mongos nodes for load balancing and failovers. A single cluster can contain 2 to 32 dds mongos nodes.
-  Each shard is a three-node replica set, and each cluster can contain 2 to 32 shards.
-  A config node is a necessary part of a cluster instance, and is also deployed as a replica set. The config node stores instance configuration data.
-  The number of dds mongos and shard nodes can be increased from the management console. You do not need to use native commands.
-  You can :ref:`enable IP addresses of shards and the config node <dds_02_0100>` to directly access the shards and the config node.
-  A three-node replica set cannot be directly upgraded to a cluster.
