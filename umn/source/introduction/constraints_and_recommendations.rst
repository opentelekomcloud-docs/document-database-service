:original_name: dds_01_0022.html

.. _dds_01_0022:

Constraints and Recommendations
===============================

To improve the stability and security of DB instances, there are some constraints on the use of DDS. For details, see :ref:`Table 1 <dds_01_0022__table60364850123535>`.

.. _dds_01_0022__table60364850123535:

.. table:: **Table 1** Function constraints

   +------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Topic                                    | Constraints                                                                                                                                                                                                                 |
   +==========================================+=============================================================================================================================================================================================================================+
   | Connecting to a DB instance              | -  When connecting to a DB instance over private networks, bind an EIP to the prepared ECS.                                                                                                                                 |
   |                                          | -  By default, DDS is not accessible from ECSs that are not in the same security group. If the ECS is not in the same security group, you need to add an inbound rule to enable access.                                     |
   |                                          | -  The default DDS port is 8635, but this port can be modified if necessary.                                                                                                                                                |
   +------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Deployment                               | ECS instances in which DB instances are deployed are not visible to you. Your applications can access the database only through an IP address and port.                                                                     |
   +------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Obtaining permissions of user **rwuser** | Only the **rwuser** user permissions are provided on the instance creation page.                                                                                                                                            |
   |                                          |                                                                                                                                                                                                                             |
   |                                          | For details about the related commands, see :ref:`Which Commands are Supported or Restricted by DDS? <dds_03_0033>`                                                                                                         |
   +------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Setting database parameters              | Most database parameters in the parameter templates you created can be modified. For details, see section :ref:`Modifying a Parameter Template <en-us_topic_configuration>`.                                                |
   +------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Migrating data                           | You can use multiple tools to migrate your data between databases, such as mongoexport and mongoimport. For details, see section :ref:`Migrating Data <dds_03_0052>`.                                                       |
   +------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Storage engine                           | DDS supports the WiredTiger storage engine.                                                                                                                                                                                 |
   +------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Nodes                                    | Mongos and shard nodes that are successfully added cannot be deleted.                                                                                                                                                       |
   +------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Restarting a DB instance or a node       | DB instances cannot be restarted using commands. They must be restarted on the management console.                                                                                                                          |
   +------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Viewing DDS backup files                 | DDS backups are saved in OBS buckets but these cannot be accessed directly. You can download and view the files on the DDS console. For details, see section :ref:`Downloading Backup Files <en-us_topic_backup_download>`. |
   +------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
