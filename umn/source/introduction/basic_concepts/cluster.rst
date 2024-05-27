:original_name: dds_01_0002.html

.. _dds_01_0002:

Cluster
=======

Each DDS cluster consists of a config node, and multiple dds mongos and shard nodes. The following diagram shows the node relationships.


.. figure:: /_static/images/en-us_image_0000001845343652.png
   :alt: **Figure 1** Diagram of node relationships

   **Figure 1** Diagram of node relationships

dds mongos
----------

A dds mongos is a router for reading and writing data, providing a unified interface for accessing DB instances.

-  Each DB instance has 2 to 32 dds mongos. You can specify the quantity.
-  A dds mongos reads configuration settings from configs and allocates read and write requests to shards. You can connect to a dds mongos directly.

config
------

A config stores configuration settings for DB instances and consists of one replica set.

-  The availability of a config is the prerequisite to deploying a DB instance or modifying the instance information.
-  You cannot connect to a config directly.

shard
-----

In the cluster instance, shards are used to store user data.

-  Each cluster instance has 2 to 32 shards. You can specify the quantity.
-  Each shard is deployed as a replica set to ensure data redundancy and high reliability.
-  You cannot connect to a shard directly.
