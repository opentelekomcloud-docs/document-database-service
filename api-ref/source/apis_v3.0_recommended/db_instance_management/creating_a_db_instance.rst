:original_name: dds_api_0020.html

.. _dds_api_0020:

Creating a DB Instance
======================

Function
--------

This API is used to create cluster, replica set, and single node instances.

URI
---

-  URI format

   POST https://{Endpoint}/v3/{project_id}/instances

-  Parameter description

   .. table:: **Table 1** Parameter description

      ========== ========= =================================================
      Name       Mandatory Description
      ========== ========= =================================================
      project_id Yes       Specifies the project ID of a tenant in a region.
      ========== ========= =================================================

Requests
--------

-  Parameter description

   .. table:: **Table 2** Parameter description

      +-----------------------+-----------------+------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name                  | Mandatory       | Type             | Description                                                                                                                                                                                                                               |
      +=======================+=================+==================+===========================================================================================================================================================================================================================================+
      | name                  | Yes             | String           | Specifies the DB instance name. Instance name, which can be the same as an existing name.                                                                                                                                                 |
      |                       |                 |                  |                                                                                                                                                                                                                                           |
      |                       |                 |                  | -  The instance name must contain 4 to 64 characters and must start with a letter. It is case sensitive and can contain letters, digits, hyphens (-), and underscores (_). It cannot contain other special characters.                    |
      +-----------------------+-----------------+------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | datastore             | Yes             | Object           | Specifies the database information. For more information, see :ref:`Table 3 <dds_api_0020__table228903751753>`.                                                                                                                           |
      +-----------------------+-----------------+------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | region                | Yes             | String           | Specifies the region ID.                                                                                                                                                                                                                  |
      |                       |                 |                  |                                                                                                                                                                                                                                           |
      |                       |                 |                  | The value cannot be empty. For details about how to obtain this parameter value, see `Regions and Endpoints <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.                                                                |
      +-----------------------+-----------------+------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | availability_zone     | Yes             | String           | Specifies the AZ ID. You can select multiple AZs to create a cross-AZ cluster based on **az_status** returned by the API described in :ref:`Querying Database Specifications <dds_instance_specification>`.                               |
      |                       |                 |                  |                                                                                                                                                                                                                                           |
      |                       |                 |                  | The value cannot be empty. For details about how to obtain this parameter value, see `Regions and Endpoints <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.                                                                |
      +-----------------------+-----------------+------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | vpc_id                | Yes             | String           | Specifies the VPC ID. To obtain this parameter value, use either of the following methods:                                                                                                                                                |
      |                       |                 |                  |                                                                                                                                                                                                                                           |
      |                       |                 |                  | -  Method 1: Log in to VPC console and view the VPC ID on the VPC details page.                                                                                                                                                           |
      |                       |                 |                  | -  Method 2: See the "Querying VPCs" section in the *Virtual Private Cloud API Reference*.                                                                                                                                                |
      +-----------------------+-----------------+------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | subnet_id             | Yes             | String           | Specifies the network ID of the subnet. To obtain this parameter value, use either of the following methods:                                                                                                                              |
      |                       |                 |                  |                                                                                                                                                                                                                                           |
      |                       |                 |                  | -  Method 1: Log in to VPC console and click the target subnet on the **Subnets** page. You can view the network ID on the displayed page.                                                                                                |
      |                       |                 |                  | -  Method 2: See the "Querying Subnets" section in the *Virtual Private Cloud API Reference*.                                                                                                                                             |
      +-----------------------+-----------------+------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | security_group_id     | Yes             | String           | Specifies the security group ID. To obtain the security group ID, perform either of the following methods:                                                                                                                                |
      |                       |                 |                  |                                                                                                                                                                                                                                           |
      |                       |                 |                  | -  Method 1: Log in to VPC console. Choose **Access Control** > **Security Groups** in the navigation pane on the left. On the displayed page, click the target security group. You can view the security group ID on the displayed page. |
      |                       |                 |                  | -  Method 2: See the "Querying Security Groups" section in the *Virtual Private Cloud API Reference*.                                                                                                                                     |
      +-----------------------+-----------------+------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | port                  | No              | String           | Database access port                                                                                                                                                                                                                      |
      |                       |                 |                  |                                                                                                                                                                                                                                           |
      |                       |                 |                  | Value range: 2100-9500, 27017, 27018, and 27019.                                                                                                                                                                                          |
      |                       |                 |                  |                                                                                                                                                                                                                                           |
      |                       |                 |                  | If this parameter is not transferred, the port of the created DB instance is 8635 by default.                                                                                                                                             |
      +-----------------------+-----------------+------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | password              | No              | String           | Specifies the database password.                                                                                                                                                                                                          |
      |                       |                 |                  |                                                                                                                                                                                                                                           |
      |                       |                 |                  | The value must be 8 to 32 characters in length and contain uppercase letters (A to Z), lowercase letters (a to z), digits (0 to 9), and special characters, such as ``~!@#%^*-_=+?``                                                      |
      |                       |                 |                  |                                                                                                                                                                                                                                           |
      |                       |                 |                  | Enter a strong password to improve security, preventing security risks such as brute force cracking.                                                                                                                                      |
      +-----------------------+-----------------+------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | disk_encryption_id    | No              | String           | Specifies the key ID used for disk encryption. The string must comply with UUID regular expression rules.                                                                                                                                 |
      |                       |                 |                  |                                                                                                                                                                                                                                           |
      |                       |                 |                  | If this parameter is not transferred, disk encryption is not performed.                                                                                                                                                                   |
      +-----------------------+-----------------+------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | mode                  | Yes             | String           | Specifies the instance type. Cluster, replica set, and single node instances are supported.                                                                                                                                               |
      |                       |                 |                  |                                                                                                                                                                                                                                           |
      |                       |                 |                  | Valid value:                                                                                                                                                                                                                              |
      |                       |                 |                  |                                                                                                                                                                                                                                           |
      |                       |                 |                  | -  Sharding                                                                                                                                                                                                                               |
      |                       |                 |                  | -  ReplicaSet                                                                                                                                                                                                                             |
      |                       |                 |                  | -  Single                                                                                                                                                                                                                                 |
      +-----------------------+-----------------+------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | flavor                | Yes             | Array of objects | Specifies the instance specifications. For more information, see :ref:`Table 4 <dds_api_0020__table94791241013>`.                                                                                                                         |
      |                       |                 |                  |                                                                                                                                                                                                                                           |
      |                       |                 |                  | For details about how to obtain the value, see the response values of **flavor** in :ref:`Querying Database Specifications <dds_instance_specification>`.                                                                                 |
      +-----------------------+-----------------+------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | backup_strategy       | No              | Object           | Specifies the advanced backup policy. For more information, see :ref:`Table 5 <dds_api_0020__table15990419397>`.                                                                                                                          |
      +-----------------------+-----------------+------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | enterprise_project_id | No              | String           | Specifies the enterprise project ID.                                                                                                                                                                                                      |
      |                       |                 |                  |                                                                                                                                                                                                                                           |
      |                       |                 |                  | -  This parameter is not transferred for users who have not enabled the enterprise multi-project service.                                                                                                                                 |
      |                       |                 |                  | -  If this parameter is not transferred for a user who has enabled the enterprise multi-project service, the value is the default enterprise project.                                                                                     |
      |                       |                 |                  |                                                                                                                                                                                                                                           |
      |                       |                 |                  | To obtain the enterprise project ID, see the **id** value in the **enterprise_project field data structure** table in section "Querying the Enterprise Project List" of the *Enterprise Management API Reference*.                        |
      +-----------------------+-----------------+------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | ssl_option            | No              | String           | Specifies whether to enable or disable SSL.                                                                                                                                                                                               |
      |                       |                 |                  |                                                                                                                                                                                                                                           |
      |                       |                 |                  | Valid value:                                                                                                                                                                                                                              |
      |                       |                 |                  |                                                                                                                                                                                                                                           |
      |                       |                 |                  | -  The value **0** indicates that SSL is disabled by default.                                                                                                                                                                             |
      |                       |                 |                  | -  The value **1** indicates that SSL is enabled by default.                                                                                                                                                                              |
      |                       |                 |                  | -  If this parameter is not transferred, SSL is enabled by default.                                                                                                                                                                       |
      +-----------------------+-----------------+------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | tags                  | No              | Array of objects | Tag list                                                                                                                                                                                                                                  |
      |                       |                 |                  |                                                                                                                                                                                                                                           |
      |                       |                 |                  | A maximum of 20 tags can be added for each instance. For details, see :ref:`Table 6 <dds_api_0020__table1030225523118>`.                                                                                                                  |
      +-----------------------+-----------------+------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. _dds_api_0020__table228903751753:

   .. table:: **Table 3** datastore field data structure description

      +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------+
      | Name            | Mandatory       | Type            | Description                                                                                                                                |
      +=================+=================+=================+============================================================================================================================================+
      | type            | Yes             | String          | Specifies the database type. The value is **DDS-Community**.                                                                               |
      +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------+
      | version         | Yes             | String          | Specifies the database version. Versions 4.4, 4.2, 4.0, 3.4 and 3.2 are supported. The value can be **4.4, 4.2, 4.0,** **3.4** or **3.2**. |
      +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------+
      | storage_engine  | Yes             | String          | Specifies the storage engine. DDS supports the WiredTiger and RocksDB storage engines.                                                     |
      |                 |                 |                 |                                                                                                                                            |
      |                 |                 |                 | -  If the database version is 4.4 or 4.2 and the storage engine is RocksDB, the value is **rocksDB**.                                      |
      |                 |                 |                 | -  If the database version is 4.0, 3.4 or 3.2 and the storage engine is WiredTiger, the value is **wiredTiger**.                           |
      +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------+

   .. _dds_api_0020__table94791241013:

   .. table:: **Table 4** flavor field data structure description

      +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name            | Mandatory       | Type            | Description                                                                                                                                                                                                                                           |
      +=================+=================+=================+=======================================================================================================================================================================================================================================================+
      | type            | Yes             | String          | Specifies the node type.                                                                                                                                                                                                                              |
      |                 |                 |                 |                                                                                                                                                                                                                                                       |
      |                 |                 |                 | Valid value:                                                                                                                                                                                                                                          |
      |                 |                 |                 |                                                                                                                                                                                                                                                       |
      |                 |                 |                 | -  For a cluster instance, the value can be **mongos**, **shard**, or **config**.                                                                                                                                                                     |
      |                 |                 |                 | -  For a replica set instance, the value is **replica**.                                                                                                                                                                                              |
      |                 |                 |                 | -  For a single node instance, the value is **single**.                                                                                                                                                                                               |
      +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | num             | Yes             | Integer         | Specifies node quantity.                                                                                                                                                                                                                              |
      |                 |                 |                 |                                                                                                                                                                                                                                                       |
      |                 |                 |                 | Valid value:                                                                                                                                                                                                                                          |
      |                 |                 |                 |                                                                                                                                                                                                                                                       |
      |                 |                 |                 | -  mongos: The value ranges from 2 to 32.                                                                                                                                                                                                             |
      |                 |                 |                 | -  mongos: The value ranges from 2 to 32.                                                                                                                                                                                                             |
      |                 |                 |                 | -  config: The value is **1**.                                                                                                                                                                                                                        |
      |                 |                 |                 | -  replica: The number of nodes can be 3, 5, or 7.                                                                                                                                                                                                    |
      |                 |                 |                 | -  single: The value is **1**.                                                                                                                                                                                                                        |
      +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | storage         | No              | String          | Specifies the disk type.                                                                                                                                                                                                                              |
      |                 |                 |                 |                                                                                                                                                                                                                                                       |
      |                 |                 |                 | Valid value: ULTRAHIGH, which indicates the type SSD.                                                                                                                                                                                                 |
      |                 |                 |                 |                                                                                                                                                                                                                                                       |
      |                 |                 |                 | This parameter is valid for the shard and config nodes of a cluster instance, replica set instances, and single node instances. This parameter is invalid for mongos nodes. Therefore, you do not need to specify the storage space for mongos nodes. |
      +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | size            | No              | String          | Specifies the disk size.                                                                                                                                                                                                                              |
      |                 |                 |                 |                                                                                                                                                                                                                                                       |
      |                 |                 |                 | This parameter is mandatory for all nodes except mongos. This parameter is invalid for the mongos nodes.                                                                                                                                              |
      |                 |                 |                 |                                                                                                                                                                                                                                                       |
      |                 |                 |                 | The value must be a multiple of 10. The unit is GB.                                                                                                                                                                                                   |
      |                 |                 |                 |                                                                                                                                                                                                                                                       |
      |                 |                 |                 | -  For a cluster instance, the storage space of a shard node can be 10 to 2000 GB, and the config storage space is 20 GB. This parameter is invalid for mongos nodes. Therefore, you do not need to specify the storage space for mongos nodes.       |
      |                 |                 |                 | -  For a replica set instance, the value ranges from 10 to 2000.                                                                                                                                                                                      |
      |                 |                 |                 | -  For a single node instance, the value ranges from 10 to 1000.                                                                                                                                                                                      |
      +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | spec_code       | Yes             | String          | Specifies the resource specification code. For details about how to obtain the value, see the response values of **spec_code** in :ref:`Querying Database Specifications <dds_instance_specification>`.                                               |
      |                 |                 |                 |                                                                                                                                                                                                                                                       |
      |                 |                 |                 | In a cluster instance, multiple specifications need to be specified. All specifications must be of the same series, that is, general-purpose (s6), enhanced (c3), or enhanced II (c6).                                                                |
      +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. _dds_api_0020__table15990419397:

   .. table:: **Table 5** backup_strategy field data structure description

      +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name            | Mandatory       | Type            | Description                                                                                                                                    |
      +=================+=================+=================+================================================================================================================================================+
      | start_time      | Yes             | String          | Specifies the backup time window. Automated backups will be triggered during the backup time window.                                           |
      |                 |                 |                 |                                                                                                                                                |
      |                 |                 |                 | The value cannot be empty. It must be a valid value in the "hh:mm-HH:MM" format. The current time is in the UTC format.                        |
      |                 |                 |                 |                                                                                                                                                |
      |                 |                 |                 | -  The **HH** value must be 1 greater than the **hh** value.                                                                                   |
      |                 |                 |                 | -  The values of **mm** and **MM** must be the same and must be set to **00**.                                                                 |
      |                 |                 |                 | -  If this parameter is not transferred, the default backup time window is set to **00:00-01:00**.                                             |
      |                 |                 |                 |                                                                                                                                                |
      |                 |                 |                 | Example value:                                                                                                                                 |
      |                 |                 |                 |                                                                                                                                                |
      |                 |                 |                 | 23:00-00:00                                                                                                                                    |
      +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------+
      | keep_days       | No              | String          | Specifies the number of days to retain the generated backup files.                                                                             |
      |                 |                 |                 |                                                                                                                                                |
      |                 |                 |                 | The value range is from 0 to 732.                                                                                                              |
      |                 |                 |                 |                                                                                                                                                |
      |                 |                 |                 | -  If this parameter is set to **0**, the automated backup policy is not set.                                                                  |
      |                 |                 |                 | -  If this parameter is not transferred, the automated backup policy is enabled by default. Backup files are stored for seven days by default. |
      +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------+

   .. _dds_api_0020__table1030225523118:

   .. table:: **Table 6** tags field data structure description

      +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------+
      | Name            | Mandatory       | Type            | Description                                                                                                             |
      +=================+=================+=================+=========================================================================================================================+
      | key             | Yes             | String          | Tag key. The value can contain a maximum of 36 unicode characters.                                                      |
      |                 |                 |                 |                                                                                                                         |
      |                 |                 |                 | The key cannot be left blank or an empty string.                                                                        |
      |                 |                 |                 |                                                                                                                         |
      |                 |                 |                 | The character set is as follows: A-Z, a-z, 0-9, hyphens (-), underscores (_), and Unicode characters (\\u4E00-\\u9FFF). |
      +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------+
      | value           | Yes             | String          | Tag value. It contains a maximum of 43 Unicode characters. The value can be an empty string.                            |
      |                 |                 |                 |                                                                                                                         |
      |                 |                 |                 | The character set is as follows: A-Z, a-z, 0-9, hyphens (-), underscores (_), and Unicode characters (\\u4E00-\\u9FFF). |
      +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------+

.. note::

   The values of **region** and **availability_zone** are used as examples.

-  Example request

   POST https://dds.eu-de.otc.t-systems.com/v3/0549b4a43100d4f32f51c01c2fe4acdb/instances

   Create a cluster instance:

   .. code-block:: text

      {
        "name": "test-cluster-01",
        "datastore": {
          "type": "DDS-Community",
          "version": "4.0",
          "storage_engine": "wiredTiger"
        },
        "region": "aaa",
        "availability_zone": "bbb",
        "vpc_id": "674e9b42-cd8d-4d25-a2e6-5abcc565b961",
        "subnet_id": "f1df08c5-71d1-406a-aff0-de435a51007b",
        "security_group_id": "7aa51dbf-5b63-40db-9724-dad3c4828b58",
        "password": "******",
        "mode": "Sharding",
        "flavor": [
          {
            "type": "mongos",
            "num": 2,
            "spec_code": "dds.mongodb.s2.medium.4.mongos"
          },
          {
            "type": "shard",
            "num": 2,
            "storage": "ULTRAHIGH",
            "size": "20",
            "spec_code": "dds.mongodb.s2.medium.4.shard"
          },
          {
            "type": "config",
            "num": 1,
            "storage": "ULTRAHIGH",
            "size": "20",
            "spec_code": "dds.mongodb.s2.large.2.config"
          }
        ],
        "backup_strategy": {
          "start_time": "23:00-00:00",
          "keep_days": "8"
        },
        "ssl_option":"1",
        "tags" : [{
          "key" : "dds001",
          "value" : "dds001"
        }]
      }
      Create a cluster instance:
      {
        "name": "test-cluster-01",
        "datastore": {
          "type": "DDS-Community",
          "version": "4.0",
          "storage_engine": "wiredTiger"
        },
        "region": "aaa",
        "availability_zone": "bbb",
        "vpc_id": "674e9b42-cd8d-4d25-a2e6-5abcc565b961",
        "subnet_id": "f1df08c5-71d1-406a-aff0-de435a51007b",
        "security_group_id": "7aa51dbf-5b63-40db-9724-dad3c4828b58",
        "mode": "Sharding",
        "flavor": [
          {
            "type": "mongos",
            "num": 2,
            "spec_code": "dds.mongodb.s2.medium.4.mongos"
          },
          {
            "type": "shard",
            "num": 2,
            "storage": "ULTRAHIGH",
            "size": "20",
            "spec_code": "dds.mongodb.s2.medium.4.shard"
          },
          {
            "type": "config",
            "num": 1,
            "storage": "ULTRAHIGH",
            "size": "20",
            "spec_code": "dds.mongodb.s2.large.2.config"
          }
        ]
            "tags" : [{
              "key" : "dds001",
              "value" : "dds001"
           }]
      }

   Create a replica set instance.

   .. code-block:: text

      {
        "name": "test-replicaset",
        "datastore": {
          "type": "DDS-Community",
          "version": "4.0",
          "storage_engine": "wiredTiger"
        },
        "region": "aaa",
        "availability_zone": "bbb",
        "vpc_id": "674e9b42-cd8d-4d25-a2e6-5abcc565b961",
        "subnet_id": "f1df08c5-71d1-406a-aff0-de435a51007b",
        "security_group_id": "7aa51dbf-5b63-40db-9724-dad3c4828b58",
        "password": "******",
        "mode": "ReplicaSet",
        "flavor": [
          {
            "type": "replica",
            "num": 1,
            "storage": "ULTRAHIGH",
            "size": "30",
            "spec_code": "dds.mongodb.s2.medium.4.repset"
          }
        ],
        "backup_strategy": {
          "start_time": "23:00-00:00",
          "keep_days": "8"
        },
        "ssl_option":"1",
        "tags" : [{
          "key" : "dds001",
          "value" : "dds001"
        }]
      }

   Create a single node instance.

   .. code-block:: text

      {
        "name": "test-singlenode",
        "datastore": {
          "type": "DDS-Community",
          "version": "4.0",
          "storage_engine": "wiredTiger"
        },
        "region": "aaa",
        "availability_zone": "bbb",
        "vpc_id": "674e9b42-cd8d-4d25-a2e6-5abcc565b961",
        "subnet_id": "f1df08c5-71d1-406a-aff0-de435a51007b",
        "security_group_id": "7aa51dbf-5b63-40db-9724-dad3c4828b58",
        "password": "******",
        "mode": "Single",
        "flavor": [
          {
            "type": "single",
            "num": 1,
            "storage": "ULTRAHIGH",
            "size": "30",
            "spec_code": "dds.mongodb.s2.medium.4.single"
          }
        ],
        "backup_strategy": {
          "start_time": "23:00-00:00",
          "keep_days": "8"
        },
        "ssl_option":"1",
        "tags" : [{
          "key" : "dds001",
          "value" : "dds001"
        }]
      }

Responses
---------

-  Parameter description

   .. table:: **Table 7** Parameter description

      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name                  | Type                  | Description                                                                                                                                                   |
      +=======================+=======================+===============================================================================================================================================================+
      | id                    | String                | Indicates the DB instance ID.                                                                                                                                 |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | name                  | String                | Same as the request parameter.                                                                                                                                |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | datastore             | Object                | Indicates the database information, which is the same as the request parameter. For more information, see :ref:`Table 8 <dds_api_0020__table149461548134>`.   |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | created               | String                | Indicates the creation time in the following format: yyyy-mm-dd hh:mm:ss.                                                                                     |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | status                | String                | Indicates the DB instance status. The value is **creating**.                                                                                                  |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | region                | String                | Indicates the region ID, which is the same as the request parameter.                                                                                          |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | availability_zone     | String                | Indicates the AZ ID, which is the same as the request parameter.                                                                                              |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | vpc_id                | String                | Indicates the VPC ID, which is the same as the request parameter.                                                                                             |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | subnet_id             | String                | Indicates the network ID of the subnet, which is the same as the request parameter.                                                                           |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | security_group_id     | String                | Indicates the security group ID, which is the same as the request parameter.                                                                                  |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | port                  | Integer               | Indicates the database port.                                                                                                                                  |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | disk_encryption_id    | String                | Indicates the ID of the disk encryption key, which is the same as the request parameter.                                                                      |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | mode                  | String                | Indicates the instance type, which is the same as the request parameter.                                                                                      |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | flavor                | Array of objects      | Indicates the instance specification, which is the same as the request parameter. For more information, see :ref:`Table 9 <dds_api_0020__table119482048538>`. |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | backup_strategy       | Object                | Indicates the advanced backup policy, which is the same as the request parameter. For more information, see :ref:`Table 10 <dds_api_0020__table59521648930>`. |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | enterprise_project_id | String                | Indicates the enterprise project ID. If the value is **0**, the resource belongs to the default enterprise project.                                           |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | ssl_option            | String                | Indicates whether to enable SSL, which functions the same as the request parameter.                                                                           |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | job_id                | String                | Indicates the ID of the workflow for creating a DB instance.                                                                                                  |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | tags                  | Array of objects      | Tag list, which is the same as the request parameter.                                                                                                         |
      |                       |                       |                                                                                                                                                               |
      |                       |                       | For details, see :ref:`Table 11 <dds_api_0020__table1695414482318>`.                                                                                          |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. _dds_api_0020__table149461548134:

   .. table:: **Table 8** datastore field data structure description

      +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------+
      | Name            | Mandatory       | Type            | Description                                                                                                                                |
      +=================+=================+=================+============================================================================================================================================+
      | type            | Yes             | String          | Specifies the database type. The value is **DDS-Community**.                                                                               |
      +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------+
      | version         | Yes             | String          | Specifies the database version. Versions 4.4, 4.2, 4.0, 3.4 and 3.2 are supported. The value can be **4.4, 4.2, 4.0,** **3.4** or **3.2**. |
      +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------+
      | storage_engine  | Yes             | String          | Specifies the storage engine. DDS supports the WiredTiger and RocksDB storage engines.                                                     |
      |                 |                 |                 |                                                                                                                                            |
      |                 |                 |                 | -  If the database version is 4.4 or 4.2 and the storage engine is RocksDB, the value is **rocksDB**.                                      |
      |                 |                 |                 | -  If the database version is 4.0, 3.4 or 3.2 and the storage engine is WiredTiger, the value is **wiredTiger**.                           |
      +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------+

   .. _dds_api_0020__table119482048538:

   .. table:: **Table 9** flavor field data structure description

      +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name            | Mandatory       | Type            | Description                                                                                                                                                                                                                                           |
      +=================+=================+=================+=======================================================================================================================================================================================================================================================+
      | type            | Yes             | String          | Specifies the node type.                                                                                                                                                                                                                              |
      |                 |                 |                 |                                                                                                                                                                                                                                                       |
      |                 |                 |                 | Valid value:                                                                                                                                                                                                                                          |
      |                 |                 |                 |                                                                                                                                                                                                                                                       |
      |                 |                 |                 | -  For a cluster instance, the value can be **mongos**, **shard**, or **config**.                                                                                                                                                                     |
      |                 |                 |                 | -  For a replica set instance, the value is **replica**.                                                                                                                                                                                              |
      |                 |                 |                 | -  For a single node instance, the value is **single**.                                                                                                                                                                                               |
      +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | num             | Yes             | String          | Specifies node quantity.                                                                                                                                                                                                                              |
      |                 |                 |                 |                                                                                                                                                                                                                                                       |
      |                 |                 |                 | Valid value:                                                                                                                                                                                                                                          |
      |                 |                 |                 |                                                                                                                                                                                                                                                       |
      |                 |                 |                 | -  mongos: The value ranges from 2 to 32.                                                                                                                                                                                                             |
      |                 |                 |                 | -  mongos: The value ranges from 2 to 32.                                                                                                                                                                                                             |
      |                 |                 |                 | -  config: The value is **1**.                                                                                                                                                                                                                        |
      |                 |                 |                 | -  replica: The number of nodes can be 3, 5, or 7.                                                                                                                                                                                                    |
      |                 |                 |                 | -  single: The value is **1**.                                                                                                                                                                                                                        |
      +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | storage         | No              | String          | Specifies the disk type.                                                                                                                                                                                                                              |
      |                 |                 |                 |                                                                                                                                                                                                                                                       |
      |                 |                 |                 | Valid value: ULTRAHIGH, which indicates the type SSD.                                                                                                                                                                                                 |
      |                 |                 |                 |                                                                                                                                                                                                                                                       |
      |                 |                 |                 | This parameter is valid for the shard and config nodes of a cluster instance, replica set instances, and single node instances. This parameter is invalid for mongos nodes. Therefore, you do not need to specify the storage space for mongos nodes. |
      +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | size            | No              | String          | Specifies the disk size.                                                                                                                                                                                                                              |
      |                 |                 |                 |                                                                                                                                                                                                                                                       |
      |                 |                 |                 | This parameter is mandatory for all nodes except mongos. This parameter is invalid for the mongos nodes.                                                                                                                                              |
      |                 |                 |                 |                                                                                                                                                                                                                                                       |
      |                 |                 |                 | The value must be a multiple of 10. The unit is GB.                                                                                                                                                                                                   |
      |                 |                 |                 |                                                                                                                                                                                                                                                       |
      |                 |                 |                 | -  For a cluster instance, the storage space of a shard node can be 10 to 2000 GB, and the config storage space is 20 GB. This parameter is invalid for mongos nodes. Therefore, you do not need to specify the storage space for mongos nodes.       |
      |                 |                 |                 | -  For a replica set instance, the value ranges from 10 to 2000.                                                                                                                                                                                      |
      |                 |                 |                 | -  For a single node instance, the value ranges from 10 to 1000.                                                                                                                                                                                      |
      +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | spec_code       | Yes             | String          | Specifies the resource specification code. For details about how to obtain the value, see the response values of **spec_code** in :ref:`Querying Database Specifications <dds_instance_specification>`.                                               |
      |                 |                 |                 |                                                                                                                                                                                                                                                       |
      |                 |                 |                 | In a cluster instance, multiple specifications need to be specified. All specifications must be of the same series, that is, general-purpose (s6), enhanced (c3), or enhanced II (c6).                                                                |
      +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. _dds_api_0020__table59521648930:

   .. table:: **Table 10** backup_strategy field data structure description

      +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name            | Mandatory       | Type            | Description                                                                                                                                    |
      +=================+=================+=================+================================================================================================================================================+
      | start_time      | Yes             | String          | Specifies the backup time window. Automated backups will be triggered during the backup time window.                                           |
      |                 |                 |                 |                                                                                                                                                |
      |                 |                 |                 | The value cannot be empty. It must be a valid value in the "hh:mm-HH:MM" format. The current time is in the UTC format.                        |
      |                 |                 |                 |                                                                                                                                                |
      |                 |                 |                 | -  The **HH** value must be 1 greater than the **hh** value.                                                                                   |
      |                 |                 |                 | -  The values of **mm** and **MM** must be the same and must be set to **00**.                                                                 |
      |                 |                 |                 | -  If this parameter is not transferred, the default backup time window is set to **00:00-01:00**.                                             |
      |                 |                 |                 |                                                                                                                                                |
      |                 |                 |                 | Example value:                                                                                                                                 |
      |                 |                 |                 |                                                                                                                                                |
      |                 |                 |                 | 23:00-00:00                                                                                                                                    |
      +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------+
      | keep_days       | No              | String          | Specifies the number of days to retain the generated backup files.                                                                             |
      |                 |                 |                 |                                                                                                                                                |
      |                 |                 |                 | The value range is from 0 to 732.                                                                                                              |
      |                 |                 |                 |                                                                                                                                                |
      |                 |                 |                 | -  If this parameter is set to **0**, the automated backup policy is not set.                                                                  |
      |                 |                 |                 | -  If this parameter is not transferred, the automated backup policy is enabled by default. Backup files are stored for seven days by default. |
      +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------+

   .. _dds_api_0020__table1695414482318:

   .. table:: **Table 11** tags field data structure description

      +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------+
      | Name            | Mandatory       | Type            | Description                                                                                                             |
      +=================+=================+=================+=========================================================================================================================+
      | key             | Yes             | String          | Tag key. The value can contain a maximum of 36 unicode characters.                                                      |
      |                 |                 |                 |                                                                                                                         |
      |                 |                 |                 | The key cannot be left blank or an empty string.                                                                        |
      |                 |                 |                 |                                                                                                                         |
      |                 |                 |                 | The character set is as follows: A-Z, a-z, 0-9, hyphens (-), underscores (_), and Unicode characters (\\u4E00-\\u9FFF). |
      +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------+
      | value           | Yes             | String          | Tag value. It contains a maximum of 43 Unicode characters. The value can be an empty string.                            |
      |                 |                 |                 |                                                                                                                         |
      |                 |                 |                 | The character set is as follows: A-Z, a-z, 0-9, hyphens (-), underscores (_), and Unicode characters (\\u4E00-\\u9FFF). |
      +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------+

.. note::

   The values of **region** and **availability_zone** are used as examples.

-  Response example

   Cluster instance:

   .. code-block:: text

      {
          "id": "39b6a1a278844ac48119d86512e0000bin02",
          "name": "test-cluster-01",
          "datastore": {
              "type": "DDS-Community",
              "version": "4.0",
              "storage_engine": "wiredTiger"
          },
          "created": "2019-01-16 09:34:36",
          "status": "creating",
          "region": "aaa",
          "availability_zone": "bbb",
          "vpc_id": "674e9b42-cd8d-4d25-a2e6-5abcc565b961",
          "subnet_id": "f1df08c5-71d1-406a-aff0-de435a51007b",
          "security_group_id": "7aa51dbf-5b63-40db-9724-dad3c4828b58",
          "port": 8365,
          "disk_encryption_id": "",
          "mode": "Sharding",
          "flavor": [
              {
                  "type": "mongos",
                  "num": "2",
                  "spec_code": "dds.mongodb.s2.medium.4.mongos"
              },
              {
                  "type": "shard",
                  "num": "2",
                  "spec_code": "dds.mongodb.s2.medium.4.shard",
                  "size": "20"
              },
              {
                  "type": "config",
                  "num": "1",
                  "spec_code": "dds.mongodb.s2.large.2.config",
                  "size": "20"
              }
          ],
          "backup_strategy": {
              "start_time": "23:00-00:00",
              "keep_days": "8"
          },
          "enterprise_project_id": "",
          "ssl_option":"1",
          "job_id": "c010abd0-48cf-4fa8-8cbc-090f093eaa2f",
          "tags" : [{
            "key" : "dds001",
            "value" : "dds001"
          }]
      }

   Replica set instance:

   .. code-block:: text

      {
          "id": "46dfadfd2b674585a430217f23606cd7in02",
          "name": "test-replicaset",
          "datastore": {
              "type": "DDS-Community",
              "version": "4.0",
              "storage_engine": "wiredTiger"
          },
          "created": "2019-01-16 09:33:08",
          "status": "creating",
          "region": "aaa",
          "availability_zone": "bbb",
          "vpc_id": "674e9b42-cd8d-4d25-a2e6-5abcc565b961",
          "subnet_id": "f1df08c5-71d1-406a-aff0-de435a51007b",
          "security_group_id": "7aa51dbf-5b63-40db-9724-dad3c4828b58",
          "port": 8365,
          "disk_encryption_id": "",
          "mode": "ReplicaSet",
          "flavor": [
              {
                  "type": "replica",
                  "num": "1",
                  "spec_code": "dds.mongodb.s2.medium.4.repset",
                  "size": "30"
              }
          ],
          "backup_strategy": {
              "start_time": "23:00-00:00",
              "keep_days": "7"
          },
          "enterprise_project_id": "",
          "ssl_option":"1",
          "job_id": "2408417d-fd4b-40ae-bec6-e09ce594eb5f",
          "tags" : [{
            "key" : "dds001",
            "value" : "dds001"
          }]
      }

   Single node instance:

   .. code-block:: text

      {
          "id": "520c58ba00a3497e97ce0b9604874dd6in02",
          "name": "test-singlenode",
          "datastore": {
              "type": "DDS-Community",
              "version": "4.0",
              "storage_engine": "wiredTiger"
          },
          "created": "2019-01-15 12:08:11",
          "status": "creating",
          "region": "aaa",
          "availability_zone": "bbb",
          "vpc_id": "674e9b42-cd8d-4d25-a2e6-5abcc565b961",
          "subnet_id": "f1df08c5-71d1-406a-aff0-de435a51007b",
          "security_group_id": "7aa51dbf-5b63-40db-9724-dad3c4828b58",
          "port": 8365,
          "disk_encryption_id": "",
          "mode": "Single",
          "flavor": [
              {
                  "type": "single",
                  "num": "1",
                  "spec_code": "dds.mongodb.s2.medium.4.single",
                  "size": "30"
              }
          ],
          "backup_strategy": {
              "start_time": "23:00-00:00",
              "keep_days": "7"
          },
          "enterprise_project_id": "",
          "ssl_option":"1",
          "job_id": "46b65a13-3d52-4c58-a29b-4085d563dc9b",
          "tags" : [{
            "key" : "dds001",
            "value" : "dds001"
          }]
      }

Status Code
-----------

Status Code:202.

For more information, see :ref:`Status Code <dds_status_code>`.

Error Code
----------

For more information, see :ref:`Error Code <dds_error_code>`.
