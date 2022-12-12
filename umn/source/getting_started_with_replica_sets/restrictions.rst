:original_name: dds_02_0011.html

.. _dds_02_0011:

Restrictions
============

To improve the stability and security of DB instances, there are some restrictions on the use of DDS. For details, see :ref:`Table 1 <dds_02_0011__en-us_topic_0105284934_table60364850123535>`.

.. _dds_02_0011__en-us_topic_0105284934_table60364850123535:

.. table:: **Table 1** Function restrictions

   +----------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Operation                                    | Restrictions                                                                                                                                                         |
   +==============================================+======================================================================================================================================================================+
   | Connecting to a DB instance through a client | -  To access a DDS DB instance which is not publicly accessible from an ECS, the instance must be in the same VPC subnet as the ECS.                                 |
   |                                              | -  By default, DDS cannot be accessed through an ECS in a different security group. You need to add an inbound rule to the DDS security group.                       |
   |                                              | -  The default DDS port number is 8635. You can change it if you want to access DDS through another port.                                                            |
   +----------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Deployment                                   | ECSs in which DB instances are deployed are not visible to you. Your applications can access the database only through an IP address and port.                       |
   +----------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Obtaining permissions of user **rwuser**     | Only the **rwuser** user permissions are provided on the instance creation page.                                                                                     |
   |                                              |                                                                                                                                                                      |
   |                                              | For details about the related commands, see :ref:`Which Commands are Supported or Restricted by DDS? <dds_faq_0033>`                                                 |
   +----------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Setting database parameters                  | Most database parameters in the parameter groups you created can be modified. For details, see section :ref:`Editing a Parameter Group <en-us_topic_configuration>`. |
   +----------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Migrating data                               | You can use command line tools, including mongoexport and mongoimport, to migrate data. For details, see section :ref:`Migrating Data <dds_03_0052>`.                |
   +----------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Storage engine                               | Currently, DDS supports the WiredTiger storage engine only.                                                                                                          |
   +----------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Restarting a DB instance or a node           | A DDS DB instance must be restarted on the DDS console.                                                                                                              |
   +----------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Viewing DDS backup files                     | You can download and view the backup files on the DDS console. For details, see section :ref:`Downloading Backup Files <en-us_topic_backup_download>`.               |
   +----------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
