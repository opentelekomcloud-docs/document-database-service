:original_name: dds_01_0009.html

.. _dds_01_0009:

Scalability
===========

Elastic Scaling
---------------

DDS supports the cluster mode. You can select multiple mongos and shards. When your service changes or the current instance configuration cannot meet the application performance requirements, DDS allows you to scale up storage space of shards, or add new shards. During the expansion, your services will not be interrupted.

On-demand Scaling
-----------------

DDS supports the three-node replica set mode. You can scale up the storage space based on your service requirements and only pay for the resources you consumed. If the storage space of the current DB instance cannot meet your application requirements, you can expand the storage capacity. During the expansion, your services will not be interrupted.
