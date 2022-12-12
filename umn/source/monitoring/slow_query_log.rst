:original_name: en-us_topic_slow_query_log.html

.. _en-us_topic_slow_query_log:

Slow Query Log
==============

Slow query logs record statements whose execution period exceeds the value of **slowms** (100 ms by default), allowing you identify and optimize slowly executed statements.

Procedure
---------

#. :ref:`Log in to the DDS console. <dds_02_0043>`
#. On the **Instance Management** page, click the target DB instance.
#. In the navigation pane on the left, click **Slow Query Logs**.
#. On the displayed page, click **Slow Query Logs**. Then, view the log details.

   -  Log records of all shards of a cluster instance
   -  Log records of all nodes of a replica set instance
   -  Log records of a node in different time periods
   -  Statements of the following level

      -  All statement type
      -  INSERT
      -  QUERY
      -  UPDATE
      -  REMOVE
      -  GETMORE
      -  COMMAND
