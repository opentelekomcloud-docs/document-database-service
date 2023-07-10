:original_name: en-us_topic_0000001159335385.html

.. _en-us_topic_0000001159335385:

Changing the DB Instance Class
==============================

Scenarios
---------

This section describes how to change the DB instance class.

.. note::

   -  A DB instance cannot be deleted when you are changing its instance class.
   -  Instances can be scaled up or down.
   -  For cluster and replica set instances, when the DB instance class is changed, a primary/secondary switchover may occur and the database connection will be interrupted for up to 30s. You are advised to change the specifications during off-peak hours to reduce impacts and ensure that your client can reconnect to the database if the connection is interrupted.
   -  For a single node instance, services will be interrupted up to 10 minutes when you change DB instance class. You are advised to perform this operation during off-peak hours. After the restart is complete, the cached memory will be automatically cleared. The DB instance needs to be warmed up to prevent congestion during peak hours.

-  :ref:`Changing a Cluster DB Instance Class <en-us_topic_0104472218>`
-  :ref:`Changing a Replica Set DB Instance Class <en-us_topic_0104721795>`
-  :ref:`Changing a Single Node DB Instance Class <dds_03_0030>`

.. toctree::
   :maxdepth: 1
   :hidden: 

   changing_a_cluster_db_instance_class
   changing_a_replica_set_db_instance_class
   changing_a_single_node_db_instance_class
