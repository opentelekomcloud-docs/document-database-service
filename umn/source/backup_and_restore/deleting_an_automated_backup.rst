:original_name: dds_03_0009.html

.. _dds_03_0009:

Deleting an Automated Backup
============================

**Scenarios**
-------------

This section describes how to delete an automated backup. If the automated backup policy is disabled, DDS allows you to delete stored automated backups to release storage space.

If the automated backup policy is enabled, DDS will delete automated backups as they expire. You cannot delete them manually.

.. important::

   The deletion operation is irreversible. Exercise caution when performing this operation.

Method 1
--------

#. :ref:`Log in to the DDS console. <dds_02_0043>`

#. On the **Instance Management** page, click the target DB instance.

#. In the navigation pane on the left, click **Backups & Restorations**.

#. On the **Backups & Restorations** tab, locate the automated backup to be deleted and click **Delete**.

   Backups being used to recover instances cannot be deleted.

#. In the displayed dialog box, click **Yes**.

Method 2
--------

#. :ref:`Log in to the DDS console. <dds_02_0043>`

#. In the navigation pane on the left, click **Backup Management**.

#. On the **Backup Management** page, click the **Clusters**, **Replica Sets**, or **Single Nodes** tab, locate the automated backup to be deleted, and click **Delete** in the **Operation** column.

   Backups being used to recover instances cannot be deleted.

#. In the displayed dialog box, click **Yes**.
