:original_name: dds_api_0020.html

.. _dds_api_0020:

Creating a DB Instance
======================

Function
--------

This API is used to create cluster, replica set instances.

URI
---

-  URI format

   POST /v3/{project_id}/instances

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

      +--------------------+-----------------+------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name               | Mandatory       | Type             | Description                                                                                                                                                                                                     |
      +====================+=================+==================+=================================================================================================================================================================================================================+
      | name               | Yes             | String           | Specifies the DB instance name. The DB instance name of the same DB engine is unique for the same tenant.                                                                                                       |
      |                    |                 |                  |                                                                                                                                                                                                                 |
      |                    |                 |                  | The value must be 4 to 64 characters in length and start with a letter (from A to Z or from a to z). It is case-sensitive and can contain only letters, digits (from 0 to 9), hyphens (-), and underscores (_). |
      +--------------------+-----------------+------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | datastore          | Yes             | Object           | Specifies the database information. For more information, see :ref:`Table 3 <dds_api_0020__table228903751753>`.                                                                                                 |
      +--------------------+-----------------+------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | region             | Yes             | String           | Specifies the region ID.                                                                                                                                                                                        |
      |                    |                 |                  |                                                                                                                                                                                                                 |
      |                    |                 |                  | The value cannot be empty. For details about how to obtain this parameter value, see `Regions and Endpoints <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.                                      |
      +--------------------+-----------------+------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | availability_zone  | Yes             | String           | Specifies the AZ ID.                                                                                                                                                                                            |
      |                    |                 |                  |                                                                                                                                                                                                                 |
      |                    |                 |                  | The value cannot be empty. For details about how to obtain this parameter value, see `Regions and Endpoints <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.                                      |
      +--------------------+-----------------+------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | vpc_id             | Yes             | String           | Specifies the VPC ID. For details about how to obtain this parameter value, see section "Virtual Private Cloud" in the *Virtual Private Cloud API Reference*.                                                   |
      |                    |                 |                  |                                                                                                                                                                                                                 |
      |                    |                 |                  | The value cannot be empty. The string length and whether the string complying with UUID regular expression rules are verified.                                                                                  |
      +--------------------+-----------------+------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | subnet_id          | Yes             | String           | Specifies the subnet ID. For details about how to obtain this parameter value, see section "Subnet" in the *Virtual Private Cloud API Reference*.                                                               |
      +--------------------+-----------------+------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | security_group_id  | Yes             | String           | Specifies the ID of the security group where a specified DB instance belongs to.                                                                                                                                |
      |                    |                 |                  |                                                                                                                                                                                                                 |
      |                    |                 |                  | For details about how to obtain this parameter value, see section "Security Group" in the *Virtual Private Cloud API Reference*.                                                                                |
      +--------------------+-----------------+------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | password           | Yes             | String           | Specifies the database password.                                                                                                                                                                                |
      |                    |                 |                  |                                                                                                                                                                                                                 |
      |                    |                 |                  | The value must be 8 to 32 characters in length and contain uppercase letters (A to Z), lowercase letters (a to z), digits (0 to 9), and special characters, such as ``~!@#%^*-_=+?``                            |
      |                    |                 |                  |                                                                                                                                                                                                                 |
      |                    |                 |                  | You are advised to enter a strong password to improve security, preventing security risks such as brute force cracking.                                                                                         |
      +--------------------+-----------------+------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | disk_encryption_id | No              | String           | Specifies the key ID used for disk encryption. The string must comply with UUID regular expression rules.                                                                                                       |
      |                    |                 |                  |                                                                                                                                                                                                                 |
      |                    |                 |                  | If this parameter is not transferred, disk encryption is not performed.                                                                                                                                         |
      +--------------------+-----------------+------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | mode               | Yes             | String           | Specifies the instance type. Cluster, replica set instances are supported.                                                                                                                                      |
      |                    |                 |                  |                                                                                                                                                                                                                 |
      |                    |                 |                  | Valid value:                                                                                                                                                                                                    |
      |                    |                 |                  |                                                                                                                                                                                                                 |
      |                    |                 |                  | -  Sharding                                                                                                                                                                                                     |
      |                    |                 |                  | -  ReplicaSet                                                                                                                                                                                                   |
      +--------------------+-----------------+------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | flavor             | Yes             | Array of objects | Specifies the instance specifications. For more information, see :ref:`Table 4 <dds_api_0020__table94791241013>`.                                                                                               |
      |                    |                 |                  |                                                                                                                                                                                                                 |
      |                    |                 |                  | For details about how to obtain the value, see the response values of **flavor** in :ref:`Querying All DB Instance Specifications <dds_instance_specification>`.                                                |
      +--------------------+-----------------+------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | backup_strategy    | No              | Object           | Specifies the advanced backup policy. For more information, see :ref:`Table 5 <dds_api_0020__table15990419397>`.                                                                                                |
      +--------------------+-----------------+------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | ssl_option         | No              | String           | Specifies whether to enable SSL.                                                                                                                                                                                |
      |                    |                 |                  |                                                                                                                                                                                                                 |
      |                    |                 |                  | Valid value:                                                                                                                                                                                                    |
      |                    |                 |                  |                                                                                                                                                                                                                 |
      |                    |                 |                  | -  The value **0** indicates that SSL is disabled by default.                                                                                                                                                   |
      |                    |                 |                  | -  The value **1** indicates that SSL is enabled by default.                                                                                                                                                    |
      |                    |                 |                  | -  If this parameter is not transferred, SSL is enabled by default.                                                                                                                                             |
      +--------------------+-----------------+------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. _dds_api_0020__table228903751753:

   .. table:: **Table 3** datastore field data structure description

      +----------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------+
      | Name           | Mandatory | Type   | Description                                                                                                       |
      +================+===========+========+===================================================================================================================+
      | type           | Yes       | String | Specifies the database type. DDS Community Edition is supported. The value is **DDS-Community**.                  |
      +----------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------+
      | version        | Yes       | String | Specifies the database version. The value is **3.2** or **3.4**.                                                  |
      +----------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------+
      | storage_engine | Yes       | String | Specifies the storage engine. Currently, DDS supports the WiredTiger storage engine. The value is **wiredTiger**. |
      +----------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------+

   .. _dds_api_0020__table94791241013:

   .. table:: **Table 4** flavor field data structure description

      +-----------------+----------------------------------------------------------------------------------------------------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name            | Mandatory                                                                                                | Type            | Description                                                                                                                                                                                                                                     |
      +=================+==========================================================================================================+=================+=================================================================================================================================================================================================================================================+
      | type            | Yes                                                                                                      | String          | Specifies the node type.                                                                                                                                                                                                                        |
      |                 |                                                                                                          |                 |                                                                                                                                                                                                                                                 |
      |                 |                                                                                                          |                 | Valid value:                                                                                                                                                                                                                                    |
      |                 |                                                                                                          |                 |                                                                                                                                                                                                                                                 |
      |                 |                                                                                                          |                 | -  For a cluster instance, the value can be **mongos**, **shard**, or **config**.                                                                                                                                                               |
      |                 |                                                                                                          |                 | -  For a replica set instance, the value is **replica**.                                                                                                                                                                                        |
      +-----------------+----------------------------------------------------------------------------------------------------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | num             | Yes                                                                                                      | Integer         | Specifies node quantity.                                                                                                                                                                                                                        |
      |                 |                                                                                                          |                 |                                                                                                                                                                                                                                                 |
      |                 |                                                                                                          |                 | Valid value:                                                                                                                                                                                                                                    |
      |                 |                                                                                                          |                 |                                                                                                                                                                                                                                                 |
      |                 |                                                                                                          |                 | -  mongos: The value ranges from 2 to 16.                                                                                                                                                                                                       |
      |                 |                                                                                                          |                 | -  shard: The value ranges from 2 to 16.                                                                                                                                                                                                        |
      |                 |                                                                                                          |                 | -  config: The value is **1**.                                                                                                                                                                                                                  |
      |                 |                                                                                                          |                 | -  replica: The value is **1**.                                                                                                                                                                                                                 |
      +-----------------+----------------------------------------------------------------------------------------------------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | storage         | This parameter is optional for all nodes except mongos. This parameter is invalid for the mongos nodes.  | String          | Specifies the disk type.                                                                                                                                                                                                                        |
      |                 |                                                                                                          |                 |                                                                                                                                                                                                                                                 |
      |                 |                                                                                                          |                 | Valid value: ULTRAHIGH, which indicates the type SSD.                                                                                                                                                                                           |
      |                 |                                                                                                          |                 |                                                                                                                                                                                                                                                 |
      |                 |                                                                                                          |                 | This parameter is valid for the shard and config nodes of a community edition cluster instance, replica set instances. This parameter is invalid for mongos nodes. Therefore, you do not need to specify the storage space for mongos nodes.    |
      +-----------------+----------------------------------------------------------------------------------------------------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | size            | This parameter is mandatory for all nodes except mongos. This parameter is invalid for the mongos nodes. | Integer         | Specifies the disk size.                                                                                                                                                                                                                        |
      |                 |                                                                                                          |                 |                                                                                                                                                                                                                                                 |
      |                 |                                                                                                          |                 | The value must be a multiple of 10. The unit is GB.                                                                                                                                                                                             |
      |                 |                                                                                                          |                 |                                                                                                                                                                                                                                                 |
      |                 |                                                                                                          |                 | -  For a cluster instance, the storage space of a shard node can be 10 to 1000 GB, and the config storage space is 20 GB. This parameter is invalid for mongos nodes. Therefore, you do not need to specify the storage space for mongos nodes. |
      |                 |                                                                                                          |                 | -  For a replica set instance, the value ranges from 10 to 2000.                                                                                                                                                                                |
      +-----------------+----------------------------------------------------------------------------------------------------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | spec_code       | Yes                                                                                                      | String          | Specifies the resource specification code. For details about how to obtain the value, see the response values of **spec_code** in :ref:`Querying All DB Instance Specifications <dds_instance_specification>`.                                  |
      +-----------------+----------------------------------------------------------------------------------------------------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

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
      |                 |                 |                 | -  The values of **mm** and **MM** must be the same and must be set to any of the following: **00**, **15**, **30**, or **45**.                |
      |                 |                 |                 |                                                                                                                                                |
      |                 |                 |                 | Example value:                                                                                                                                 |
      |                 |                 |                 |                                                                                                                                                |
      |                 |                 |                 | -  08:15-09:15                                                                                                                                 |
      |                 |                 |                 | -  23:00-00:00                                                                                                                                 |
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

-  Request header

   .. code-block:: text

      POST https://DDS endpoint/v3/{project_id}/instances.

-  Example request

   Create a cluster instance.

   .. code-block:: text

      {
        "name": "test-cluster-01",
        "datastore": {
          "type": "DDS-Community",
          "version": "3.4",
          "storage_engine": "wiredTiger"
        },
        "region": "aaa",
        "availability_zone": "bbb",
        "vpc_id": "674e9b42-cd8d-4d25-a2e6-5abcc565b961",
        "subnet_id": "f1df08c5-71d1-406a-aff0-de435a51007b",
        "security_group_id": "7aa51dbf-5b63-40db-9724-dad3c4828b58",
        "password": "Test@123",
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
            "size": 20,
            "spec_code": "dds.mongodb.s2.medium.4.shard"
          },
          {
            "type": "config",
            "num": 1,
            "storage": "ULTRAHIGH",
            "size": 20,
            "spec_code": "dds.mongodb.s2.large.2.config"
          }
        ],
        "backup_strategy": {
          "start_time": "08:15-09:15",
          "keep_days": "8"
        },
        "ssl_option":"1"
      }

   Create a replica set instance.

   .. code-block:: text

      {
        "name": "test-replicaset",
        "datastore": {
          "type": "DDS-Community",
          "version": "3.4",
          "storage_engine": "wiredTiger"
        },
        "region": "aaa",
        "availability_zone": "bbb",
        "vpc_id": "674e9b42-cd8d-4d25-a2e6-5abcc565b961",
        "subnet_id": "f1df08c5-71d1-406a-aff0-de435a51007b",
        "security_group_id": "7aa51dbf-5b63-40db-9724-dad3c4828b58",
        "password": "Test@123",
        "mode": "ReplicaSet",
        "flavor": [
          {
            "type": "replica",
            "num": 1,
            "storage": "ULTRAHIGH",
            "size": 30,
            "spec_code": "dds.mongodb.s2.medium.4.repset"
          }
        ],
        "backup_strategy": {
          "start_time": "08:15-09:15",
          "keep_days": "8"
        },
        "ssl_option":"1"
      }

Responses
---------

-  Parameter description

   .. table:: **Table 6** Parameter description

      +--------------------+------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name               | Type             | Description                                                                                                                                                  |
      +====================+==================+==============================================================================================================================================================+
      | id                 | String           | Indicates the DB instance ID.                                                                                                                                |
      +--------------------+------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | name               | String           | Same as the request parameter.                                                                                                                               |
      +--------------------+------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | datastore          | Object           | Indicates the database information, which is the same as the request parameter. For more information, see :ref:`Table 3 <dds_api_0020__table228903751753>`.  |
      +--------------------+------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | created            | String           | Indicates the creation time in the following format: yyyy-mm-dd hh:mm:ss.                                                                                    |
      +--------------------+------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | status             | String           | Indicates the DB instance status. The value is **creating**.                                                                                                 |
      +--------------------+------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | region             | String           | Indicates the region ID, which is the same as the request parameter.                                                                                         |
      +--------------------+------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | availability_zone  | String           | Indicates the AZ ID, which is the same as the request parameter.                                                                                             |
      +--------------------+------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | vpc_id             | String           | Indicates the VPC ID, which is the same as the request parameter.                                                                                            |
      +--------------------+------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | subnet_id          | String           | Indicates the subnet ID, which is the same as the request parameter.                                                                                         |
      +--------------------+------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | security_group_id  | String           | Indicates the ID of the security group to which the instance belongs, which is the same as the request parameter.                                            |
      +--------------------+------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | disk_encryption_id | String           | Indicates the ID of the disk encryption key, which is the same as the request parameter.                                                                     |
      +--------------------+------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | mode               | String           | Indicates the instance type, which is the same as the request parameter.                                                                                     |
      +--------------------+------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | flavor             | Array of objects | Indicates the instance specification, which is the same as the request parameter. For more information, see :ref:`Table 4 <dds_api_0020__table94791241013>`. |
      +--------------------+------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | backup_strategy    | Object           | Indicates the advanced backup policy, which is the same as the request parameter. For more information, see :ref:`Table 5 <dds_api_0020__table15990419397>`. |
      +--------------------+------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | ssl_option         | String           | Indicates whether to enable SSL, which functions the same as the request parameter.                                                                          |
      +--------------------+------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | job_id             | String           | Indicates the ID of the workflow for creating a DB instance.                                                                                                 |
      +--------------------+------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+

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
              "version": "3.4",
              "storage_engine": "wiredTiger"
          },
          "created": "2019-01-16 09:34:36",
          "status": "creating",
          "region": "aaa",
          "availability_zone": "bbb",
          "vpc_id": "674e9b42-cd8d-4d25-a2e6-5abcc565b961",
          "subnet_id": "f1df08c5-71d1-406a-aff0-de435a51007b",
          "security_group_id": "7aa51dbf-5b63-40db-9724-dad3c4828b58",
          "disk_encryption_id": "",
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
                  "spec_code": "dds.mongodb.s2.medium.4.shard",
                  "size": 20
              },
              {
                  "type": "config",
                  "num": 1,
                  "spec_code": "dds.mongodb.s2.large.2.config",
                  "size": 20
              }
          ],
          "backup_strategy": {
              "start_time": "08:15-09:15",
              "keep_days": "8"
          },
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
              "version": "3.4",
              "storage_engine": "wiredTiger"
          },
          "created": "2019-01-16 09:33:08",
          "status": "creating",
          "region": "aaa",
          "availability_zone": "bbb",
          "vpc_id": "674e9b42-cd8d-4d25-a2e6-5abcc565b961",
          "subnet_id": "f1df08c5-71d1-406a-aff0-de435a51007b",
          "security_group_id": "7aa51dbf-5b63-40db-9724-dad3c4828b58",
          "disk_encryption_id": "",
          "mode": "ReplicaSet",
          "flavor": [
              {
                  "type": "replica",
                  "num": 1,
                  "spec_code": "dds.mongodb.s2.medium.4.repset",
                  "size": 30
              }
          ],
          "backup_strategy": {
              "start_time": "08:15-09:15",
              "keep_days": "7"
          },
          "ssl_option":"1",
          "job_id": "2408417d-fd4b-40ae-bec6-e09ce594eb5f"
      }

**Status Code**
---------------

For more information, see :ref:`Status Code <dds_status_code>`.

Error Code
----------

For more information, see :ref:`Error Code <dds_error_code>`.
