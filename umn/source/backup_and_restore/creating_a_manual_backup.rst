:original_name: dds_03_0007.html

.. _dds_03_0007:

Creating a Manual Backup
========================

**Scenarios**
-------------

This section describes how to create a manual backup. Creating a backup for a DB instance helps ensure data can be restored if needed, ensuring data reliability.

.. note::

   When you delete a DB instance, its automated backups are also deleted but its manual backups are retained.

Method 1
--------

#. :ref:`Log in to the DDS console. <dds_02_0043>`
#. On the **Instance Management** page, locate an available DB instance and click **Create Backup** or choose **More** > **Create Backup**.
#. In the displayed dialog box, specify **Backup Name** and **Description** (optional) and click **OK**.

   -  The manual backup name can be 4 to 64 characters long. It must start with a letter and can contain only uppercase letters, lowercase letters, digits, hyphens (-), and underscores (_).
   -  The description contains a maximum of 256 characters and cannot contain the carriage return character and the following special characters: >!<"&'=

#. Check the result:

   -  During the creation of a manual backup, you can check the backup status on the **Backup Management** or an instance's **Backups & Restorations** page. The backup status is **Backing up**. The time it takes to complete the backup depends on the size of the job.
   -  If the manual backup is successfully created, the backup status is **Completed**. The manual backup type is **Manual**.

Method 2
--------

#. :ref:`Log in to the DDS console. <dds_02_0043>`
#. In the navigation pane on the left, click **Backup Management**.
#. On the **Backup Management** page, click **Create Backup**.
#. In the displayed dialog box, specify **DB Instance Type**, **DB Instance Name**, **Backup Name** and **Description** (optional) and click **OK**.

   -  Only DB instances in **Available** status can be manually backed up.
   -  The manual backup name can be 4 to 64 characters long. It must start with a letter and can contain only uppercase letters, lowercase letters, digits, hyphens (-), and underscores (_).
   -  The description contains a maximum of 256 characters and cannot contain the carriage return character and the following special characters: >!<"&'=

#. Check the result:

   -  During the creation of a manual backup, you can check the backup status on the **Backup Management** or an instance's **Backups & Restorations** page. The backup status is **Backing up**. The time it takes to complete the backup depends on the size of the job.
   -  If the manual backup is successfully created, the backup status is **Completed**. The manual backup type is **Manual**.

Method 3
--------

#. :ref:`Log in to the DDS console. <dds_02_0043>`
#. On the **Instance Management** page, click an available DB instance.
#. In the navigation pane on the left, click **Backups & Restorations**.
#. On the **Backups & Restorations** page, click **Create Backup**.
#. In the displayed dialog box, specify **Backup Name** and **Description** (optional) and click **OK**.

   -  The manual backup name can be 4 to 64 characters long. It must start with a letter and can contain only uppercase letters, lowercase letters, digits, hyphens (-), and underscores (_).
   -  The description contains a maximum of 256 characters and cannot contain the carriage return character and the following special characters: >!<"&'=

#. Check the result:

   -  During the creation of a manual backup, you can check the backup status on the **Backup Management** or an instance's **Backups & Restorations** page. The backup status is **Backing up**. The time it takes to complete the backup depends on the size of the job.
   -  If the manual backup is successfully created, the backup status is **Completed**. The manual backup type is **Manual**.
