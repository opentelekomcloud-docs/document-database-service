:original_name: en-us_topic_backup_restore.html

.. _en-us_topic_backup_restore:

Setting Automated Backup Policy
===============================

**Scenarios**
-------------

DDS backs up data automatically based on the automated backup policy you set. You are advised to regularly back up data in your database. If the database becomes faulty or data is damaged, you can restore it with the backup, ensuring data reliability.

.. important::

   -  DDS checks existing automated backup files. If the retention period of a file exceeds the backup retention period you set, DDS will delete the file.
   -  After the backup policy is modified, an automated backup will be triggered based on the new backup policy. The retention period of the previously generated automated backups remains unchanged.

-  Backup files are stored in OBS buckets.
-  When a DB instance is created, DDS enables the automated backup policy by default. The default settings of the parameters are as follows. You can modify them after a DB instance is created.

   -  Backups are retained for 7 days by default.
   -  The time window is in UTC by default.
   -  Data is backed up every day by default.

Enabling or Modifying an Automated Backup Policy
------------------------------------------------

#. :ref:`Log in to the DDS console. <dds_02_0043>`

#. On the **Instance Management** page, click the target DB instance.

#. In the navigation pane on the left, click **Backups & Restorations**.

#. On the **Backups & Restorations** page, click **Modify Backup Policy**. If you want to enable the automated backup policy, click |image1|.

   Retention period refers to the number of days that data is kept. You can increase the retention period to improve data reliability.

   The backup retention period can range from 1 to 732 days, with a time window of one hour. The backup cycle varies according to the retention period you have set.

   -  If you set the retention period to 1 to 6 days, data is automatically backed up each day of the week.
   -  If you set the retention period to 7 to 732 days, you must select at least one day of the week for the backup cycle.

#. Click **OK** to save the modification.

#. View the backup result.

   -  If the automated backup policy is enabled, an automated full backup is immediately triggered. The time it takes to complete the backup depends on the size of the job.
   -  If the automated backup policy is modified, an automated full backup is randomly triggered during the time window you set. The time it takes to complete the backup depends on the size of the job.
   -  During the creation of an automated backup, you can query the backup status on the **Backup Management** page or the **Backups & Restorations** tab. The backup status is **Backing up**.
   -  In the upper right corner of the backup list, click |image2| to refresh the list. The backup status changes to **Complete**. The backup type is **Automated** and the backup method is **Physical**.

Disabling an Automated Backup Policy
------------------------------------

.. important::

   Observe the following constraints when disabling the automated backup policy:

   -  Your data cannot be backed up.
   -  If you choose to delete all the existing automated backup when disabling the automated backup policy, related restoration or download operations will fail.

#. :ref:`Log in to the DDS console. <dds_02_0043>`

#. On the **Instance Management** page, click the target DB instance.

#. In the navigation pane on the left, click **Backups & Restorations**.

#. On the **Backups & Restorations** page, click **Modify Backup Policy**. On the displayed page, click |image3| to disable the automated backup policy.

   You can determine whether to delete all automated backup files:

   -  If you do not select **Delete automated backups**, all backup files within the retention period will be retained. You can manually delete them. For details, see section :ref:`Deleting an Automated Backup <dds_03_0009>`.
   -  If you select **Delete automated backups**, all backup files within the retention period will be deleted.

#. Click **OK**.

.. |image1| image:: /_static/images/en-us_image_0284275158.png
.. |image2| image:: /_static/images/en-us_image_0284275185.png
.. |image3| image:: /_static/images/en-us_image_0284274973.png
