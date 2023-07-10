:original_name: en-us_topic_backup_restore.html

.. _en-us_topic_backup_restore:

Setting Automated Backup Policy
===============================

DDS backs up data automatically based on the automated backup policy you set. You are advised to regularly back up data in your database. If the database becomes faulty or data is damaged, you can restore it with the backup.

The automated backup policy for DDS is enabled by default. After an instance is created, you can :ref:`modify <en-us_topic_backup_restore__section553508110238>` or :ref:`disable <en-us_topic_backup_restore__section5411044193812>` the automated backup policy as required.

The default automated backup policy is as follows:

-  Retention period: 7 days
-  Time window: The default time window is a one hour time interval within 24 hours, for example, 01:00-02:00. The backup time is in UTC format.
-  Backup cycle: Each day of the week.

Once the automated backup policy is enabled, a full backup is triggered immediately. After that, full backups will be created based on the backup window and backup cycle you specify. When an instance is being backed up, data is copied and then compressed and uploaded to OBS. The length of time the backup data is kept for depends on the backup retention period you configure. The backup duration depends on the amount of data, and the average backup speed is 60 MB/s. After the automated backup policy is enabled, an incremental backup is automatically performed every 5 minutes to ensure data reliability.

Precautions
-----------

-  The backup process does not affect services.
-  DDS checks existing automated backup files. If the retention period of a file exceeds the backup retention period you set, DDS will delete the file.
-  After the backup policy is modified, an automated backup will be triggered based on the new backup policy. The retention period of the previously generated automated backups remains unchanged.

.. _en-us_topic_backup_restore__section553508110238:

Enabling or Modifying an Automated Backup Policy
------------------------------------------------

#. :ref:`Log in to the DDS console. <dds_02_0043>`

#. On the **Instance Management** page, click the target DB instance.

#. In the navigation pane on the left, click **Backups & Restorations**.

#. On the **Backups & Restorations** page, click **Modify Backup Policy**. If you want to enable the automated backup policy, click |image1|.

   **Retention Period** refers to the number of days that data is kept. You can increase the retention period to improve data reliability.

   The backup retention period can range from 1 to 732 days, with a time window of one hour. The backup cycle varies according to the retention period you have set.

   -  If you set the retention period to 1 to 6 days, data is automatically backed up each day of the week.
   -  If you set the retention period to 7 to 732 days, you must select at least one day of the week for the backup cycle.

#. Click **OK** to save the modification.

#. View the backup result.

   -  If the automated backup policy is enabled, an automated full backup is immediately triggered. The time it takes to complete the backup depends on the size of the job.
   -  If the automated backup policy is modified, an automated full backup is randomly triggered during the time window you set. The time it takes to complete the backup depends on the size of the job.
   -  During the creation of an automated backup, you can check the backup status on the **Backup Management** page or the **Backups & Restorations** tab. The backup status is **Backing up**.
   -  In the upper right corner of the backup list, click |image2| to refresh the list. The backup status changes to **Completed**. The backup type is **Automated**.

.. _en-us_topic_backup_restore__section5411044193812:

Disabling an Automated Backup Policy
------------------------------------

#. :ref:`Log in to the DDS console. <dds_02_0043>`

#. On the **Instance Management** page, click the target DB instance.

#. In the navigation pane on the left, click **Backups & Restorations**.

#. On the **Backups & Restorations** page, click **Modify Backup Policy**. On the displayed dialog box, click |image3| to disable the automated backup policy.

   You can determine whether to delete all automated backup files:

   -  If you do not select **Delete automated backups**, all backup files within the retention period will be retained. You can manually delete them. For details, see section :ref:`Deleting an Automated Backup <dds_03_0009>`.
   -  If you select **Delete automated backups**, all backup files within the retention period will be deleted.

#. Click **OK**.

.. |image1| image:: /_static/images/en-us_image_0000001142893879.png
.. |image2| image:: /_static/images/en-us_image_0000001096133892.png
.. |image3| image:: /_static/images/en-us_image_0000001096453870.png
