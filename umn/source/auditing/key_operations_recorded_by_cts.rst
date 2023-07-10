:original_name: dds_03_0029.html

.. _dds_03_0029:

Key Operations Recorded by CTS
==============================

With Cloud Trace Service (CTS), you can record operations associated with DDS for later query, audit, and backtrack operations.

.. table:: **Table 1** Key operations on DDS

   +--------------------------------------+----------------+--------------------------+
   | Operation                            | Resource       | Trace Name               |
   +======================================+================+==========================+
   | Restoring data to a new DB instance  | instance       | ddsRestoreToNewInstance  |
   +--------------------------------------+----------------+--------------------------+
   | Creating a DB instance               | instance       | ddsCreateInstance        |
   +--------------------------------------+----------------+--------------------------+
   | Deleting a DB instance               | instance       | ddsDeleteInstance        |
   +--------------------------------------+----------------+--------------------------+
   | Restarting a DB instance             | instance       | ddsRestartInstance       |
   +--------------------------------------+----------------+--------------------------+
   | Scaling up a DB instance             | instance       | ddsGrowInstance          |
   +--------------------------------------+----------------+--------------------------+
   | Scaling up storage space             | instance       | ddsExtendInstanceVolume  |
   +--------------------------------------+----------------+--------------------------+
   | Resetting the database password      | instance       | ddsResetPassword         |
   +--------------------------------------+----------------+--------------------------+
   | Renaming a DB instance               | instance       | ddsRenameInstance        |
   +--------------------------------------+----------------+--------------------------+
   | Switching SSL                        | instance       | ddsSwitchSsl             |
   +--------------------------------------+----------------+--------------------------+
   | Modifying a DB instance port         | instance       | ddsModifyInstancePort    |
   +--------------------------------------+----------------+--------------------------+
   | Creating a backup                    | backup         | ddsCreateBackup          |
   +--------------------------------------+----------------+--------------------------+
   | Deleting a backup                    | backup         | ddsDeleteBackup          |
   +--------------------------------------+----------------+--------------------------+
   | Setting a backup policy              | backup         | ddsSetBackupPolicy       |
   +--------------------------------------+----------------+--------------------------+
   | Applying a parameter template        | parameterGroup | ddsApplyConfigurations   |
   +--------------------------------------+----------------+--------------------------+
   | Replicating a parameter template     | parameterGroup | ddsCopyConfigurations    |
   +--------------------------------------+----------------+--------------------------+
   | Resetting a parameter template       | parameterGroup | ddsResetConfigurations   |
   +--------------------------------------+----------------+--------------------------+
   | Creating a parameter template        | parameterGroup | ddsCreateConfigurations  |
   +--------------------------------------+----------------+--------------------------+
   | Deleting a parameter template        | parameterGroup | ddsDeleteConfigurations  |
   +--------------------------------------+----------------+--------------------------+
   | Updating a parameter template        | parameterGroup | ddsUpdateConfigurations  |
   +--------------------------------------+----------------+--------------------------+
   | Binding an EIP                       | instance       | ddsBindEIP               |
   +--------------------------------------+----------------+--------------------------+
   | Unbinding an EIP                     | instance       | ddsUnBindEIP             |
   +--------------------------------------+----------------+--------------------------+
   | Adding a tag                         | tag            | ddsAddTag                |
   +--------------------------------------+----------------+--------------------------+
   | Deleting a tag                       | tag            | ddsDeleteTag             |
   +--------------------------------------+----------------+--------------------------+
   | Editing a tag                        | tag            | ddsModifyTag             |
   +--------------------------------------+----------------+--------------------------+
   | Deleting an instance tag             | tag            | ddsDeleteInstanceTag     |
   +--------------------------------------+----------------+--------------------------+
   | Adding an instance tag               | tag            | ddsAddInstanceTag        |
   +--------------------------------------+----------------+--------------------------+
   | Rolling back upon scaling-up failure | instance       | ddsDeleteExtendedDdsNode |
   +--------------------------------------+----------------+--------------------------+
   | Changing DB instance classes         | instance       | ddsResizeInstance        |
   +--------------------------------------+----------------+--------------------------+

.. note::

   ddsAddTag and ddsDeleteTag are respectively used to add and delete tags for all resources. ddsAddInstanceTag and ddsDeleteInstanceTag are respectively used to add and delete tags for a single instance.
