:original_name: en-us_topic_error_log.html

.. _en-us_topic_error_log:

Error Log
=========

DDS log management allows you to view database-level logs, including warning- and error-level logs generated during database running, which help you analyze system problems.

Procedure
---------

#. :ref:`Log in to the DDS console. <dds_02_0043>`
#. On the **Instance Management** page, click the target DB instance.
#. In the navigation pane on the left, click **Error Logs**.
#. On the displayed page, click **Error Logs**. Then, view the log details.

   -  Log records of different node types of a cluster instance in batches

      -  If you select **All nodes**, the logs of all nodes in the cluster instance are displayed.
      -  If you select **All mongos**, the logs of all mongos in the cluster instance are displayed.
      -  If you select **All shards**, the logs of all shards in the cluster instance are displayed.
      -  If you select **All configs**, the logs of all configs in the cluster instance are displayed.

   -  Log records of all nodes of a replica set instance
   -  Log records of a node in different time periods
   -  Time, levels, and descriptions of the logs
