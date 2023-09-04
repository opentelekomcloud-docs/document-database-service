:original_name: en-us_topic_backup_download.html

.. _en-us_topic_backup_download:

Downloading Backup Files
========================

**Scenarios**
-------------

This section describes how to download manual or automated backup files for local data backup or restoration.

Procedure
---------

#. :ref:`Log in to the DDS console. <dds_02_0043>`

#. In the navigation pane on the left, click **Backup Management**.

#. On the **Backup Management** page, click the **Clusters**, **Replica Sets**, or **Single Nodes** tab, locate the target backup you want to download and click **Download** in the **Operation** column.

#. Download `OBS Browser <https://obs.otc.t-systems.com/obsbrowser/OBSBrowser.zip>`__ and install it.

#. Log in to the OBS Browser.

   For details on how to log in to OBS Browser, see section `Logging In to OBS Browser <https://docs.otc.t-systems.com/en-us/usermanual/obs/en-us_topic_0045853477.html>`__ in the *Object Storage Service User Guide*.

#. Disable certificate verification on OBS Browser.

   For details on how to configure OBS Browser, see section `Configuring the System <https://docs.otc.t-systems.com/en-us/usermanual/obs/en-us_topic_0045853630.html>`__ in the *Object Storage Service User Guide*.

   .. note::

      The OBS bucket names displayed on the **Download Backup File** page on the DDS console do not support certificate verification. Therefore, you need to disable OBS Browser certificate verification before adding external buckets and enable it after the backup files are downloaded.

#. Add an external bucket.

   In the **Create Bucket** dialog box of OBS Browser, select **Add external bucket** and enter the bucket name displayed on **Download Backup File** of the DDS console.

   For details about how to add external buckets, see section `Adding External Buckets <https://docs.otc.t-systems.com/en-us/usermanual/obs/en-us_topic_0045853737.html>`__ in the *Object Storage Service User Guide*.

#. Download the backup files.

   In the search box on the right of OBS Browser, enter the backup file name displayed on **Download Backup File** of the DDS console.

#. Enable OBS Browser certificate verification after the backup files are downloaded.
