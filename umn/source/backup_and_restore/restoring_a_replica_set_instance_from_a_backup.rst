:original_name: dds_03_0043.html

.. _dds_03_0043:

Restoring a Replica Set Instance from a Backup
==============================================

**Scenarios**
-------------

This section describes how to restore a replica set instance from a backup.

Restoration Precautions
-----------------------

-  When you restore the DB instance from a backup file, a full backup file is downloaded from OBS and then restored to the DB instance at an average speed of 40 MB/s.

Method 1
--------

#. :ref:`Log in to the DDS console. <dds_02_0043>`
#. On the **Instance Management** page, click the target replica set instance.
#. In the navigation pane on the left, click **Backups & Restorations**.
#. On the **Backups & Restorations** page, locate the target backup and click **Restore** in the **Operation** column.
#. Select either of the following restoration methods and click **OK**.

   -  Create New Instance

      The **Create New Instance** page is displayed for you to create a DB instance using the backup data. The new DB instance is independent from the original one.

      -  The database type, DB instance type, compatible MongoDB version, storage engine, and storage type must be the same as those of the original and cannot be changed.
      -  The storage space is the same as that of the original instance by default. You can only increase the storage space.
      -  Other settings have default values and can be modified. For details, see section :ref:`Creating a Replica Set Instance <dds_02_0012>`.

   -  Restore to Original

      .. important::

         -  Restoring to the original DB instance will overwrite all existing data and the DB instance will be temporarily unavailable during the restoration.
         -  The administrator password of the database instance remains unchanged after the restoration.

Method 2
--------

#. :ref:`Log in to the DDS console. <dds_02_0043>`

#. In the navigation pane on the left, click **Backup Management**.

#. On the **Backup Management** page, locate the target backup on the **Replica Sets** tab and click **Restore** in the **Operation** column.

   -  If you use an automated backup, go to :ref:`4 <dds_03_0043__l02b85d494b33478aa0354867be338dda>`.
   -  If you use a manual backup, check whether the original instance of the manual backup exists:

      -  If yes, go to :ref:`4 <dds_03_0043__l02b85d494b33478aa0354867be338dda>`.
      -  If no, you can only restore the backup to a new DB instance. Go to :ref:`Create New Instance <dds_03_0043__li969750316413>` step under Step 4.

#. .. _dds_03_0043__l02b85d494b33478aa0354867be338dda:

   Select either of the following restoration methods and click **OK**.

   -  .. _dds_03_0043__li969750316413:

      Create New Instance

      The **Create New Instance** page is displayed for you to create a DB instance using the backup data. The new DB instance is independent from the original one.

      -  The database type, DB instance type, compatible MongoDB version, storage engine, and storage type must be the same as those of the original and cannot be changed.
      -  The storage space is the same as that of the original instance by default. You can only increase the storage space.
      -  Other settings have default values and can be modified. For details, see section :ref:`Creating a Replica Set Instance <dds_02_0012>`.

   -  Restore to Original

      .. important::

         -  Restoring to the original DB instance will overwrite all existing data and the DB instance will be temporarily unavailable during the restoration.
         -  The administrator password of the database instance remains unchanged after the restoration.
