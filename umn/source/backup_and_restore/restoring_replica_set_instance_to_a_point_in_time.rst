:original_name: dds_03_0064.html

.. _dds_03_0064:

Restoring Replica Set Instance to a Point in Time
=================================================

**Scenarios**
-------------

You can restore the data of a replica set instance to a specified time point.

Restoration Precautions
-----------------------

-  Currently, you can restore a replica set instance to a new or original DB instance at a point in time.
-  In case of point-in-time recovery, the "local" database (which is a default database in DDS instances) will not be restored.
-  When you enter the time point that you want to restore the DB instance to, DDS downloads the latest full backup file before the specified time point from OBS to the DB instance. Then, incremental backups are also restored to the specified point in time on the DB instance. Data is restored at an average speed of 30 MB/s.

Constraints
-----------

Data can be restored to a specified time point only after the automated backup policy is enabled.

Procedure
---------

#. :ref:`Log in to the DDS console. <dds_02_0043>`

#. On the **Instance Management** page, click the target replica set instance.

#. In the navigation pane on the left, click **Backups & Restorations**.

#. On the **Backups & Restorations** page, click **Restore to Point In Time**.

#. .. _dds_03_0064__li101168184011:

   Select the date and time range, select or enter a time point within the acceptable range, and select **Create New Instance** or **Restore to Original**.

#. On the displayed page, the DB instance is restored based on the restoration method you selected in :ref:`5 <dds_03_0064__li101168184011>`.

   -  Create New Instance

      The **Create New Instance** page is displayed for you to create a DB instance using the backup data. The new DB instance is independent from the original one.

      -  The database type, DB instance type, compatible MongoDB version, storage engine, and storage type must be the same as those of the original and cannot be changed.
      -  The storage space is the same as that of the original instance by default. You can only increase the storage space.

   -  Restore to Original

      .. important::

         -  Restoring to the original DB instance will overwrite all existing data and the DB instance will be temporarily unavailable during the restoration.
         -  The administrator password of the database instance remains unchanged after the restoration.
