:original_name: dds_api_0038.html

.. _dds_api_0038:

Restoring Data to a New DB Instance
===================================

Function
--------

This API is used to restore a backup to a new DB instance.

Constraints
-----------

-  The database type of the destination DB instance must be the same as that of the source DB instance.
-  Currently, only replica set instances and cluster instances 4.0 can be restored to a new instance and to any point in time.

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

      +-----------------------+-----------------+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name                  | Mandatory       | Type             | Description                                                                                                                                                                                                            |
      +=======================+=================+==================+========================================================================================================================================================================================================================+
      | name                  | Yes             | String           | Specifies the DB instance name. The instance name can be the same as an existing instance name.                                                                                                                        |
      |                       |                 |                  |                                                                                                                                                                                                                        |
      |                       |                 |                  | -  The instance name must contain 4 to 64 characters and must start with a letter. It is case sensitive and can contain letters, digits, hyphens (-), and underscores (_). It cannot contain other special characters. |
      +-----------------------+-----------------+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | availability_zone     | Yes             | String           | Specifies the AZ ID.                                                                                                                                                                                                   |
      |                       |                 |                  |                                                                                                                                                                                                                        |
      |                       |                 |                  | The value cannot be empty. For details about how to obtain this parameter value, see `Regions and Endpoints <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.                                             |
      +-----------------------+-----------------+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | vpc_id                | Yes             | String           | Specifies the VPC ID.                                                                                                                                                                                                  |
      |                       |                 |                  |                                                                                                                                                                                                                        |
      |                       |                 |                  | For details about how to obtain this parameter value, see section "Virtual Private Cloud" in the *Virtual Private Cloud API Reference*.                                                                                |
      |                       |                 |                  |                                                                                                                                                                                                                        |
      |                       |                 |                  | The value cannot be empty. The string length and whether the string complying with UUID regular expression rules are verified.                                                                                         |
      +-----------------------+-----------------+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | subnet_id             | Yes             | String           | Specifies the subnet ID.                                                                                                                                                                                               |
      |                       |                 |                  |                                                                                                                                                                                                                        |
      |                       |                 |                  | For details about how to obtain this parameter value, see section "Subnet" in the *Virtual Private Cloud API Reference*.                                                                                               |
      +-----------------------+-----------------+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | security_group_id     | Yes             | String           | Specifies the ID of the security group where a specified DB instance belongs to.                                                                                                                                       |
      |                       |                 |                  |                                                                                                                                                                                                                        |
      |                       |                 |                  | For details about how to obtain this parameter value, see section "Security Group" in the *Virtual Private Cloud API Reference*.                                                                                       |
      +-----------------------+-----------------+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | password              | No              | String           | Specifies the database password.                                                                                                                                                                                       |
      |                       |                 |                  |                                                                                                                                                                                                                        |
      |                       |                 |                  | The value must be 8 to 32 characters in length and contain uppercase letters (A to Z), lowercase letters (a to z), digits (0 to 9), and special characters, such as ``~!@#%^*-_=+?``                                   |
      |                       |                 |                  |                                                                                                                                                                                                                        |
      |                       |                 |                  | Enter a strong password to improve security, preventing security risks such as brute force cracking.                                                                                                                   |
      +-----------------------+-----------------+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | disk_encryption_id    | No              | String           | The key ID used for disk encryption. The string must comply with UUID regular expression rules.                                                                                                                        |
      |                       |                 |                  |                                                                                                                                                                                                                        |
      |                       |                 |                  | If this parameter is not transferred, disk encryption is not performed.                                                                                                                                                |
      +-----------------------+-----------------+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | flavor                | Yes             | Array of objects | Specifies the instance specifications. For more information, see :ref:`Table 4 <dds_api_0038__table206664717143>`.                                                                                                     |
      |                       |                 |                  |                                                                                                                                                                                                                        |
      |                       |                 |                  | For details about how to obtain the value, see the parameter value in :ref:`Querying Database Specifications <dds_instance_specification>`.                                                                            |
      +-----------------------+-----------------+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | restore_point         | Yes             | Object           | Specifies the details about the backup to be restored to a new DB instance. For more information, see :ref:`Table 3 <dds_api_0038__table663124711145>`.                                                                |
      +-----------------------+-----------------+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | backup_strategy       | No              | Object           | Specifies the advanced backup policy. For more information, see :ref:`Table 5 <dds_api_0038__table289547161412>`.                                                                                                      |
      +-----------------------+-----------------+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | enterprise_project_id | No              | String           | Specifies the enterprise project ID.                                                                                                                                                                                   |
      |                       |                 |                  |                                                                                                                                                                                                                        |
      |                       |                 |                  | -  This parameter is not transferred for users who have not enabled the enterprise multi-project service.                                                                                                              |
      |                       |                 |                  | -  If this parameter is not transferred for a user who has enabled the enterprise multi-project service, the value is the default enterprise project.                                                                  |
      +-----------------------+-----------------+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | ssl_option            | No              | String           | Specifies whether to enable or disable SSL.                                                                                                                                                                            |
      |                       |                 |                  |                                                                                                                                                                                                                        |
      |                       |                 |                  | Valid value:                                                                                                                                                                                                           |
      |                       |                 |                  |                                                                                                                                                                                                                        |
      |                       |                 |                  | -  The value **0** indicates that SSL is disabled by default.                                                                                                                                                          |
      |                       |                 |                  | -  The value **1** indicates that SSL is enabled by default.                                                                                                                                                           |
      |                       |                 |                  |                                                                                                                                                                                                                        |
      |                       |                 |                  | If this parameter is not transferred, SSL is enabled by default.                                                                                                                                                       |
      +-----------------------+-----------------+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. _dds_api_0038__table663124711145:

   .. table:: **Table 3** restore_point field data structure description

      +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name            | Mandatory       | Type            | Description                                                                                                                                                                     |
      +=================+=================+=================+=================================================================================================================================================================================+
      | instance_id     | No              | String          | Specifies the instance ID, which can be obtained by calling the API for querying instances. If you do not have an instance, you can call the API used for creating an instance. |
      |                 |                 |                 |                                                                                                                                                                                 |
      |                 |                 |                 | -  This parameter is optional when **type** is set to **backup**.                                                                                                               |
      |                 |                 |                 | -  This parameter is mandatory when **type** is set to **timestamp**.                                                                                                           |
      +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | type            | No              | String          | Specifies the recovery mode. The enumerated values are as follows:                                                                                                              |
      |                 |                 |                 |                                                                                                                                                                                 |
      |                 |                 |                 | -  **backup**: indicates restoration from backup files. In this mode, **backup_id** is mandatory when **type** is optional.                                                     |
      |                 |                 |                 | -  **timestamp**: indicates point-in-time restoration. In this mode, **restore_time** is mandatory when **type** is mandatory.                                                  |
      +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | backup_id       | No              | String          | Specifies the ID of the backup to be restored. This parameter must be specified when the backup file is used for restoration.                                                   |
      |                 |                 |                 |                                                                                                                                                                                 |
      |                 |                 |                 | .. note::                                                                                                                                                                       |
      |                 |                 |                 |                                                                                                                                                                                 |
      |                 |                 |                 |    When **type** is not mandatory, **backup_id** is mandatory.                                                                                                                  |
      +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | restore_time    | No              | Integer         | Specifies the time point of data restoration in the UNIX timestamp. The unit is millisecond and the time zone is UTC.                                                           |
      |                 |                 |                 |                                                                                                                                                                                 |
      |                 |                 |                 | .. note::                                                                                                                                                                       |
      |                 |                 |                 |                                                                                                                                                                                 |
      |                 |                 |                 |    When **type** is mandatory, **restore_time** is mandatory.                                                                                                                   |
      +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. _dds_api_0038__table206664717143:

   .. table:: **Table 4** flavor field data structure description

      +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name            | Mandatory       | Type            | Description                                                                                                                                                                                                                                                                                                 |
      +=================+=================+=================+=============================================================================================================================================================================================================================================================================================================+
      | type            | Yes             | String          | Specifies the node type.                                                                                                                                                                                                                                                                                    |
      |                 |                 |                 |                                                                                                                                                                                                                                                                                                             |
      |                 |                 |                 | Valid value:                                                                                                                                                                                                                                                                                                |
      |                 |                 |                 |                                                                                                                                                                                                                                                                                                             |
      |                 |                 |                 | -  For a cluster instance, the value can be **mongos**, **shard**, or **config**.                                                                                                                                                                                                                           |
      |                 |                 |                 | -  For a replica set instance, the value is **replica**.                                                                                                                                                                                                                                                    |
      |                 |                 |                 | -  For a single node instance, the value is **single**.                                                                                                                                                                                                                                                     |
      +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | num             | Yes             | Integer         | Specifies node quantity.                                                                                                                                                                                                                                                                                    |
      |                 |                 |                 |                                                                                                                                                                                                                                                                                                             |
      |                 |                 |                 | Valid value:                                                                                                                                                                                                                                                                                                |
      |                 |                 |                 |                                                                                                                                                                                                                                                                                                             |
      |                 |                 |                 | -  This parameter is not transferred for shard nodes.                                                                                                                                                                                                                                                       |
      |                 |                 |                 | -  mongos: The value ranges from 2 to 32.                                                                                                                                                                                                                                                                   |
      |                 |                 |                 | -  config: The value is **1**.                                                                                                                                                                                                                                                                              |
      |                 |                 |                 | -  replica: The value is **1**.                                                                                                                                                                                                                                                                             |
      |                 |                 |                 | -  single: The value is **1**.                                                                                                                                                                                                                                                                              |
      +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | size            | No              | String          | Specifies the disk size.                                                                                                                                                                                                                                                                                    |
      |                 |                 |                 |                                                                                                                                                                                                                                                                                                             |
      |                 |                 |                 | The value must be a multiple of 10. The unit is GB.                                                                                                                                                                                                                                                         |
      |                 |                 |                 |                                                                                                                                                                                                                                                                                                             |
      |                 |                 |                 | -  In a cluster instance, the shard size ranges from 10 GB to 2000 GB and must be greater than or equal to the disk size of the original instance. The config size can only be 20 GB. This parameter is invalid for mongos nodes. Therefore, you do not need to specify the storage space for mongos nodes. |
      |                 |                 |                 | -  In a replica set instance, the disk size ranges from 10 GB to 2000 GB and must be greater than or equal to the disk size of the original instance.                                                                                                                                                       |
      |                 |                 |                 | -  In a single node instance, the disk size ranges from 10 GB to 1000 GB and must be greater than or equal to the disk size of the original instance.                                                                                                                                                       |
      +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | spec_code       | Yes             | String          | Specifies the resource specification code. For details about how to obtain the value, see the parameter value in :ref:`Querying Database Specifications <dds_instance_specification>`.                                                                                                                      |
      +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. _dds_api_0038__table289547161412:

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

   .. note::

      The values of **region** and **availability_zone** are used as examples.

-  Request example

   POST https://dds.eu-de.otc.t-systems.com/v3/97b026aa9cc4417888c14c84a1ad9860/instances

   Restoring a backup to a new cluster instance:

   .. code-block:: text

      {
        "name": "test-cluster-01",
        "availability_zone": "bbb",
        "vpc_id": "674e9b42-cd8d-4d25-a2e6-5abcc565b961",
        "subnet_id": "f1df08c5-71d1-406a-aff0-de435a51007b",
        "security_group_id": "7aa51dbf-5b63-40db-9724-dad3c4828b58",
        "password": "Test#%0_",
        "restore_point": {
          "backup_id": "8f643d252d834a4c916b2db4322f99552734"
        },
        "flavor": [{
            "type": "mongos",
            "num": 2,
            "spec_code": "dds.mongodb.c3.medium.4.mongos"
          },
          {
            "type": "shard",
            "size": "40",
            "spec_code": "dds.mongodb.c3.medium.4.shard"
          },
          {
            "type": "config",
            "num": 1,
            "size": "20",
            "spec_code": "dds.mongodb.c3.large.2.config"
          }
        ],
        "backup_strategy": {
          "start_time": "23:00-00:00",
          "keep_days": "8"
        }
      }

   Restoring a backup to a new replica set instance:

   .. code-block:: text

      {
        "name": "test-replicaset",
        "availability_zone": "bbb",
        "vpc_id": "674e9b42-cd8d-4d25-a2e6-5abcc565b961",
        "subnet_id": "f1df08c5-71d1-406a-aff0-de435a51007b",
        "security_group_id": "7aa51dbf-5b63-40db-9724-dad3c4828b58",
        "password": "Test#%0_",
      "restore_point": {
          "backup_id": "8f643d252d834a4c916b2db4322f99552734"
      },
        "flavor": [
          {
            "type": "replica",
            "num": 1,
            "spec_code": "dds.mongodb.s2.medium.4.repset"
          }
        ],
        "backup_strategy": {
          "start_time": "23:00-00:00",
          "keep_days": "8"
        }
      }

   Restoring a backup to a new single node instance:

   .. code-block:: text

      {
        "name": "test-singlenode",
        "availability_zone": "bbb",
        "vpc_id": "674e9b42-cd8d-4d25-a2e6-5abcc565b961",
        "subnet_id": "f1df08c5-71d1-406a-aff0-de435a51007b",
        "security_group_id": "7aa51dbf-5b63-40db-9724-dad3c4828b58",
        "password": "Test#%0_",
        "restore_point": {
          "backup_id": "8f643d252d834a4c916b2db4322f99552734"
        },
        "flavor": [
          {
            "type": "single",
            "num": 1,
            "spec_code": "dds.mongodb.c3.medium.4.single"
          }
        ],
        "backup_strategy": {
          "start_time": "23:00-00:00",
          "keep_days": "8"
        }
      }

   Restoring a backup to a new replica set instance at a point in time:

   .. code-block:: text

      {
        "name": "replica-liuyunj1",
        "availability_zone": "az1xahz",
        "vpc_id": "dcdadabc-efed-4518-8b34-4af66fcd97e7",
        "subnet_id": "4a9348f2-f232-4700-a440-2f1641d80960",
        "security_group_id": "c57b9db2-cccb-4c0d-b058-7ea51dda0c99",
        "flavor": [
          {
            "type": "replica",
            "num": 1,
            "size": "100",
            "spec_code": "dds.mongodb.c3.large.2.repset"
          }
        ],
        "backup_strategy": {
          "start_time": "08:00-09:00",
          "keep_days": "8"
        },
        "restore_point": {
          "instance_id": "d5833c2854a4486cb7960f829269e211in02",
          "type": "timestamp",
          "restore_time": 1607689584000
        },
        "ssl_option": "1"
      }

Responses
---------

-  Parameter description

   .. table:: **Table 6** Parameter description

      +-----------------------+------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name                  | Type             | Description                                                                                                                                                   |
      +=======================+==================+===============================================================================================================================================================+
      | id                    | String           | Indicates the DB instance ID,                                                                                                                                 |
      +-----------------------+------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | name                  | String           | which is the same as the request parameter.                                                                                                                   |
      +-----------------------+------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | datastore             | Object           | Indicates the database information, which is the same as the request parameter. For more information, see :ref:`Table 7 <dds_api_0038__table228903751753>`.   |
      +-----------------------+------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | created               | String           | Indicates the creation time in the following format: yyyy-mm-dd hh:mm:ss.                                                                                     |
      +-----------------------+------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | status                | String           | Indicates the DB instance status. The value is **creating**.                                                                                                  |
      +-----------------------+------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | region                | String           | Indicates the region ID, which is the same as the request parameter.                                                                                          |
      +-----------------------+------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | availability_zone     | String           | Indicates the AZ ID, which is the same as the request parameter.                                                                                              |
      +-----------------------+------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | vpc_id                | String           | Indicates the VPC ID, which is the same as the request parameter.                                                                                             |
      +-----------------------+------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | subnet_id             | String           | Indicates the subnet ID, which is the same as the request parameter.                                                                                          |
      +-----------------------+------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | security_group_id     | String           | Indicates the ID of the security group to which the instance belongs, which is the same as the request parameter.                                             |
      +-----------------------+------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | disk_encryption_id    | String           | Indicates the ID of the disk encryption key, which is the same as the request parameter.                                                                      |
      +-----------------------+------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | mode                  | String           | Indicates the instance type, which is the same as the request parameter.                                                                                      |
      +-----------------------+------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | flavor                | Array of objects | Indicates the instance specification, which is the same as the request parameter. For more information, see :ref:`Table 8 <dds_api_0038__table119482048538>`. |
      +-----------------------+------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | backup_strategy       | Object           | Indicates the advanced backup policy, which is the same as the request parameter. For more information, see :ref:`Table 9 <dds_api_0038__table59521648930>`.  |
      +-----------------------+------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | enterprise_project_id | String           | Indicates the enterprise project ID. If the value is **0**, the resource belongs to the default enterprise project.                                           |
      +-----------------------+------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | job_id                | String           | Indicates the ID of the workflow for creating a DB instance.                                                                                                  |
      +-----------------------+------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | ssl_option            | String           | Indicates whether to enable SSL, which functions the same as the request parameter.                                                                           |
      +-----------------------+------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. _dds_api_0038__table228903751753:

   .. table:: **Table 7** datastore field data structure description

      +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------+
      | Name            | Mandatory       | Type            | Description                                                                                                              |
      +=================+=================+=================+==========================================================================================================================+
      | type            | Yes             | String          | Specifies the database type. The value is **DDS-Community**.                                                             |
      +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------+
      | version         | Yes             | String          | Specifies the database version. Versions 5.0, 4.4, 4.2 and 4.0 are supported. The value can be **5.0, 4.4, 4.2 or 4.0**. |
      +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------+
      | storage_engine  | Yes             | String          | Specifies the storage engine. DDS supports the WiredTiger and RocksDB storage engines.                                   |
      |                 |                 |                 |                                                                                                                          |
      |                 |                 |                 | -  If the database version is 4.2 or later, the storage engine is **rocksDB**.                                           |
      |                 |                 |                 | -  If the database version is 4.0, the storage engine is **wiredTiger**.                                                 |
      +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------+

   .. _dds_api_0038__table119482048538:

   .. table:: **Table 8** flavor field data structure description

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

   .. _dds_api_0038__table59521648930:

   .. table:: **Table 9** backup_strategy field data structure description

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
          "disk_encryption_id": "2gfdsh-844a-4023-a776-fc5c5fb71fb4",
          "mode": "Sharding",
          "flavor": [
              {
                  "type": "mongos",
                  "num": "2",
                  "spec_code": "dds.mongodb.c3.medium.4.mongos"
              },
              {
                  "type": "shard",
                  "num": "2",
                  "spec_code": "dds.mongodb.c3.medium.4.shard",
                  "size": "20"
              },
              {
                  "type": "config",
                  "num": "1",
                  "spec_code": "dds.mongodb.c3.large.2.config",
                  "size": "20"
              }
          ],
          "backup_strategy": {
              "start_time": "23:00-00:00",
              "keep_days": "8"
          },
          "enterprise_project_id": "",
          "ssl_option":"1",
          "job_id": "c010abd0-48cf-4fa8-8cbc-090f093eaa2f"
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
          "disk_encryption_id": "2gfdsh-844a-4023-a776-fc5c5fb71fb4",
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
          "job_id": "2408417d-fd4b-40ae-bec6-e09ce594eb5f"
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
          "disk_encryption_id": "2gfdsh-844a-4023-a776-fc5c5fb71fb4",
          "mode": "Single",
          "flavor": [
              {
                  "type": "single",
                  "num": "1",
                  "spec_code": "dds.mongodb.c3.medium.4.single",
                  "size": "30"
              }
          ],
          "backup_strategy": {
              "start_time": "23:00-00:00",
              "keep_days": "7"
          },
          "enterprise_project_id": "",
          "ssl_option":"1",
          "job_id": "46b65a13-3d52-4c58-a29b-4085d563dc9b"
      }

Status Code
-----------

Status Code:202.

For more information, see :ref:`Status Code <dds_status_code>`.

Error Code
----------

For more information, see :ref:`Error Code <dds_error_code>`.
