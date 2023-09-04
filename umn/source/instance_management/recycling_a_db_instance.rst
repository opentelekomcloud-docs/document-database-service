:original_name: dds_03_0101.html

.. _dds_03_0101:

Recycling a DB Instance
=======================

DDS can move deleted DB instances to the recycle bin, so you can restore them easily.

Precautions
-----------

-  The recycling policy is enabled by default and cannot be disabled. Instances in the recycle bin are retained for 7 days by default, and this will not generate any charges.

-  Up to 100 instances can be moved to the recycle bin. Once the recycle bin is full, you can still delete instances, but they cannot be placed in the recycle bin, so the deletions will be permanent.

Modifying the Recycling Policy
------------------------------

.. important::

   You can modify the retention period, and the changes only apply to the DB instances deleted after the changes, so exercise caution when performing this operation.

#. :ref:`Log in to the DDS console <dds_02_0043>`.
#. In the navigation pane on the left, choose **Recycling Management**.
#. On the **Recycling Management** page, click **Modify Recycling Policy**. In the displayed dialog box, set the retention period for the deleted DB instances from 1 day to 7 days. Then, click **OK**.

Rebuilding a DB Instance
------------------------

You can rebuild DB instances from the recycle bin within the retention period to restore data.

#. :ref:`Log in to the DDS console <dds_02_0043>`.
#. In the navigation pane on the left, choose **Recycling Management**.
#. On the **Recycling Management** page, locate the DB instance to be rebuilt and in the **Operation** column, click **Rebuild**.
#. On the displayed page, set required parameters and submit the rebuilding task.

   -  The database type, DB instance type, compatible MongoDB version, storage engine, and storage type must be the same as those of the original and cannot be changed.
   -  The storage space is the same as that of the original instance by default. You can only increase the storage space.
   -  Other settings have default values and can be modified. For details, see the following sections.

      -  :ref:`Creating a Cluster Instance <en-us_topic_0044018333>`
      -  :ref:`Creating a Replica Set Instance <dds_02_0012>`
      -  :ref:`Creating a Single Node Instance <dds_02_0023>`

   -  A full backup is triggered after the new instance is created.

   .. note::

      After the instance has been rebuilt, it also stays in the recycle bin and cannot be deleted.
