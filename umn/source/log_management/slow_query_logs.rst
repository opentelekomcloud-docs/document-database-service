:original_name: en-us_topic_slow_query_log.html

.. _en-us_topic_slow_query_log:

Slow Query Logs
===============

**Scenarios**
-------------

Slow query logs record statements whose execution period exceeds the value of **operationProfiling.slowOpThresholdMs** (500 ms by default). With slow query logs, you can identify and optimize slowly executed statements.

.. note::

   If the user would like to change this, they can do this in Section :ref:`Modifying a Parameter Template <en-us_topic_configuration>`.

Procedure
---------

#. :ref:`Log in to the DDS console. <dds_02_0043>`
#. On the **Instance Management** page, click the target DB instance.
#. In the navigation pane on the left, click **Slow Query Logs**.
#. On the **Slow Query Logs** page, set search criteria and click **Search** to view log information.

   -  Log records of all shards or a shard-specific node of a cluster instance
   -  Log records of all nodes of a replica set instance
   -  Slow query statements of the following level

      -  All statements
      -  INSERT
      -  QUERY
      -  UPDATE
      -  REMOVE
      -  GETMORE
      -  COMMAND

   -  You can view up to 2,000 slow query logs of a specified node type, of a specified statement type, and within a specified period.
