:original_name: dds_03_0004.html

.. _dds_03_0004:

Deleting a DB Instance
======================

**Scenarios**
-------------

This section guides you on how to delete a DB instance no longer used to release resources. You can delete the following types of DB instances:

-  Cluster instance
-  Replica set instance
-  Single node instance

.. important::

   -  DB instances cannot be deleted when operations are being performed on them. They can be deleted only after the operations are completed.

   -  After you delete an instance, all nodes in the instance are also deleted.

   -  After you delete the DB instance, all data in it and all automated backups are automatically deleted and cannot be restored. Exercise caution when performing this operation.

   -  By default, all manual backups are retained in DDS. You can use a backup to restore a deleted instance.

**Procedure**
-------------

#. :ref:`Log in to the DDS console. <dds_02_0043>`
#. On the **Instance Management** page, locate the target DB instance and choose **More** > **Delete** in the **Operation** column.
#. In the displayed dialog box, click **Yes**.
