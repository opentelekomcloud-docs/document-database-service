:original_name: dds_03_0029.html

.. _dds_03_0029:

Key Operations Recorded by CTS
==============================

With CTS, you can record operations associated with DDS for later query, audit, and backtrack operations.

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
   | Applying a parameter group           | parameterGroup | ddsApplyConfigurations   |
   +--------------------------------------+----------------+--------------------------+
   | Replicating a parameter group        | parameterGroup | ddsCopyConfigurations    |
   +--------------------------------------+----------------+--------------------------+
   | Resetting a parameter group          | parameterGroup | ddsResetConfigurations   |
   +--------------------------------------+----------------+--------------------------+
   | Creating a parameter group           | parameterGroup | ddsCreateConfigurations  |
   +--------------------------------------+----------------+--------------------------+
   | Deleting a parameter group           | parameterGroup | ddsDeleteConfigurations  |
   +--------------------------------------+----------------+--------------------------+
   | Updating a parameter group           | parameterGroup | ddsUpdateConfigurations  |
   +--------------------------------------+----------------+--------------------------+
   | Binding an EIP                       | instance       | ddsBindIP                |
   +--------------------------------------+----------------+--------------------------+
   | Unbinding an EIP                     | instance       | ddsUnbindIP              |
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
