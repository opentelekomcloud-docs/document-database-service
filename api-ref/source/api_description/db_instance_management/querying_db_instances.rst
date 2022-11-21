:original_name: dds_api_0023.html

.. _dds_api_0023:

Querying DB Instances
=====================

Function
--------

This API is used to query DB instances based on specified conditions.

URI
---

-  URI format

   GET /v3/{project_id}/instances?id={id}&name={name}&mode={mode}&datastore_type={datastore_type}&vpc_id={vpc_id}&subnet_id={subnet_id}&offset={offset}&limit={limit}

-  Parameter description

   .. table:: **Table 1** Parameter description

      +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name            | Mandatory       | Type            | Description                                                                                                                                                                                                          |
      +=================+=================+=================+======================================================================================================================================================================================================================+
      | project_id      | Yes             | String          | Specifies the project ID of a tenant in a region.                                                                                                                                                                    |
      +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | id              | No              | String          | Specifies the DB instance ID.                                                                                                                                                                                        |
      +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | name            | No              | String          | Specifies the DB instance name.                                                                                                                                                                                      |
      |                 |                 |                 |                                                                                                                                                                                                                      |
      |                 |                 |                 | If you use asterisk (*) at the beginning of the name, fuzzy search results are returned. Otherwise, the exact results are returned.                                                                                  |
      |                 |                 |                 |                                                                                                                                                                                                                      |
      |                 |                 |                 | .. note::                                                                                                                                                                                                            |
      |                 |                 |                 |                                                                                                                                                                                                                      |
      |                 |                 |                 |    The asterisk (*) is a reserved character in the system and cannot be used alone.                                                                                                                                  |
      +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | mode            | No              | String          | Specifies the instance type.                                                                                                                                                                                         |
      |                 |                 |                 |                                                                                                                                                                                                                      |
      |                 |                 |                 | -  **Sharding** indicates the cluster instance.                                                                                                                                                                      |
      |                 |                 |                 | -  **ReplicaSet** indicate the replica set instance.                                                                                                                                                                 |
      +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | datastore_type  | No              | String          | Specifies the database type. The value is **DDS-Community**.                                                                                                                                                         |
      +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | vpc_id          | No              | String          | Specifies the VPC ID. You can log in to the VPC console and obtain the ID of the VPC where the DDS instance is located.                                                                                              |
      +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | subnet_id       | No              | String          | Specifies the network ID of the subnet. You can log in to the VPC console and obtain the network ID of the subnet in the VPC where the DDS instance is located.                                                      |
      +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | offset          | No              | Integer         | Specifies the index position. The query starts from the next instance creation time indexed by this parameter under a specified project. If offset is set to N, the resource query starts from the N+1 piece of data |
      |                 |                 |                 |                                                                                                                                                                                                                      |
      |                 |                 |                 | The value must be greater than or equal to **0**. If this parameter is not transferred, offset is set to **0** by default, indicating that the query starts from the latest created DB instance.                     |
      +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | limit           | No              | Integer         | Specifies the maximum allowed number of DB instances.                                                                                                                                                                |
      |                 |                 |                 |                                                                                                                                                                                                                      |
      |                 |                 |                 | The value ranges from 1 to 100. If this parameter is not transferred, the first 100 DB instances are queried by default.                                                                                             |
      +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Requests
--------

-  Request header

   Query all DB instances.

   .. code-block:: text

      GET https://DDS endpoint/v3/0483b6b16e954cb88930a360d2c4e663/instances

   Query DB instances based on specified conditions.

   .. code-block:: text

      GET https://DDS endpoint/v3/0483b6b16e954cb88930a360d2c4e663/instances?offset=0&limit=10&id=ed7cc6166ec24360a5ed5c5c9c2ed726in02&name=hy&mode=ReplicaSet&datastore_type=DDS-Community&vpc_id=19e5d45d-70fd-4a91-87e9-b27e71c9891f&subnet_id=bd51fb45-2dcb-4296-8783-8623bfe89bb7

-  Request body

   N/A

Responses
---------

-  Parameter description

   .. table:: **Table 2** Parameter description

      +-------------+------------------+---------------------------------------------------------------------------------------------------------------------+
      | Name        | Type             | Description                                                                                                         |
      +=============+==================+=====================================================================================================================+
      | instances   | Array of objects | Indicates the DB instance information. For more information, see :ref:`Table 3 <dds_api_0023__table4062895917262>`. |
      +-------------+------------------+---------------------------------------------------------------------------------------------------------------------+
      | total_count | Integer          | Indicates the total number of queried records.                                                                      |
      +-------------+------------------+---------------------------------------------------------------------------------------------------------------------+

   .. _dds_api_0023__table4062895917262:

   .. table:: **Table 3** instances field data structure description

      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------+
      | Name                  | Type                  | Description                                                                                                      |
      +=======================+=======================+==================================================================================================================+
      | id                    | String                | Indicates the DB instance ID.                                                                                    |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------+
      | name                  | String                | Indicates the DB instance name.                                                                                  |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------+
      | status                | String                | Indicates the DB instance status.                                                                                |
      |                       |                       |                                                                                                                  |
      |                       |                       | Valid value:                                                                                                     |
      |                       |                       |                                                                                                                  |
      |                       |                       | -  **normal**: indicates that the instance is running properly.                                                  |
      |                       |                       | -  **abnormal**: indicates that the instance is abnormal.                                                        |
      |                       |                       | -  **creating**: indicates that the instance is being created.                                                   |
      |                       |                       | -  **data_disk_full**: indicates that the instance disk is full.                                                 |
      |                       |                       | -  **createfail**: indicates that the instance failed to be created.                                             |
      |                       |                       | -  **enlargefail**: indicates that nodes failed to be added to the instance.                                     |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------+
      | port                  | Integer               | Indicates the database port number. The port range is 2100 to 9500.                                              |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------+
      | mode                  | String                | Indicates the instance type, which is the same as the request parameter.                                         |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------+
      | region                | String                | Indicates the region where the DB instance is deployed.                                                          |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------+
      | datastore             | Object                | Indicates the database information. For more information, see :ref:`Table 4 <dds_api_0023__table5636104310403>`. |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------+
      | engine                | String                | Indicates the storage engine. The value is **wiredTiger**.                                                       |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------+
      | created               | String                | Indicates the DB instance creation time.                                                                         |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------+
      | updated               | String                | Indicates the time when a DB instance is updated.                                                                |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------+
      | db_user_name          | String                | Indicates the default username. The value is **rwuser**.                                                         |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------+
      | ssl                   | Integer               | Indicates that SSL is enabled or not.                                                                            |
      |                       |                       |                                                                                                                  |
      |                       |                       | -  **1**: indicate that SSL is enabled.                                                                          |
      |                       |                       | -  **0**: indicate that SSL is disabled.                                                                         |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------+
      | vpc_id                | String                | Indicates the VPC ID.                                                                                            |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------+
      | subnet_id             | String                | Indicates the subnet ID.                                                                                         |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------+
      | security_group_id     | String                | Indicates the security group ID.                                                                                 |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------+
      | backup_strategy       | Object                | Indicates the backup policy. For more information, see :ref:`Table 5 <dds_api_0023__table50876711173859>`.       |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------+
      | pay_mode              | String                | Indicates the billing mode. **0**: indicates the pay-per-use billing mode.                                       |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------+
      | maintenance_window    | String                | Indicates the maintenance time window.                                                                           |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------+
      | groups                | Array of objects      | Indicates group information. For more information, see :ref:`Table 6 <dds_api_0023__table0581104824211>`.        |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------+
      | disk_encryption_id    | String                | Indicates the disk encryption key ID. This parameter is returned only when the instance disk is encrypted.       |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------+
      | time_zone             | String                | Indicates the time zone.                                                                                         |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------+
      | actions               | Array of strings      | Indicates the operation that is executed on the DB instance.                                                     |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------+

   .. _dds_api_0023__table5636104310403:

   .. table:: **Table 4** datastore field data structure description

      ======= ====== ===============================
      Name    Type   Description
      ======= ====== ===============================
      type    String Indicates the DB engine.
      version String Indicates the database version.
      ======= ====== ===============================

   .. _dds_api_0023__table50876711173859:

   .. table:: **Table 5** backup_strategy field data structure description

      +------------+---------+----------------------------------------------------------------------------------------------------------------------------------------+
      | Name       | Type    | Description                                                                                                                            |
      +============+=========+========================================================================================================================================+
      | start_time | String  | Indicates the backup time window. Automated backups will be triggered during the backup time window. The current time is the UTC time. |
      +------------+---------+----------------------------------------------------------------------------------------------------------------------------------------+
      | keep_days  | Integer | Indicates the number of days to retain the generated backup files. The value range is from 0 to 732.                                   |
      +------------+---------+----------------------------------------------------------------------------------------------------------------------------------------+

   .. _dds_api_0023__table0581104824211:

   .. table:: **Table 6** groups field data structure description

      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name                  | Type                  | Description                                                                                                                                                                               |
      +=======================+=======================+===========================================================================================================================================================================================+
      | type                  | String                | Indicates the node type.                                                                                                                                                                  |
      |                       |                       |                                                                                                                                                                                           |
      |                       |                       | Valid value:                                                                                                                                                                              |
      |                       |                       |                                                                                                                                                                                           |
      |                       |                       | -  shard                                                                                                                                                                                  |
      |                       |                       | -  config                                                                                                                                                                                 |
      |                       |                       | -  mongos                                                                                                                                                                                 |
      |                       |                       | -  replica                                                                                                                                                                                |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | id                    | String                | Indicates the group ID. This parameter is valid only when the node type is shard or config.                                                                                               |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | name                  | String                | Indicates the group name. This parameter is valid only when the node type is shard or config.                                                                                             |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | status                | String                | Indicates the group status. This parameter is valid only when the node type is shard or config.                                                                                           |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | volume                | Object                | Indicates the volume information. For more information, see :ref:`Table 7 <dds_api_0023__table1149918231246>`. This parameter is valid only when the node type is shard, config, replica. |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | nodes                 | Array of objects      | Indicates node information. For more information, see :ref:`Table 8 <dds_api_0023__table3426155424213>`.                                                                                  |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. _dds_api_0023__table1149918231246:

   .. table:: **Table 7** volume field data structure description

      ==== ====== ==================================
      Name Type   Description
      ==== ====== ==================================
      size String Indicates the disk size. Unit: GB
      used String Indicates the disk usage. Unit: GB
      ==== ====== ==================================

   .. _dds_api_0023__table3426155424213:

   .. table:: **Table 8** nodes field data structure description

      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name                  | Type                  | Description                                                                                                                                                                                                                     |
      +=======================+=======================+=================================================================================================================================================================================================================================+
      | id                    | String                | Indicates the node ID.                                                                                                                                                                                                          |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | name                  | String                | Indicates the node name.                                                                                                                                                                                                        |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | status                | String                | Indicates the node status.                                                                                                                                                                                                      |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | role                  | String                | Indicates the node role.                                                                                                                                                                                                        |
      |                       |                       |                                                                                                                                                                                                                                 |
      |                       |                       | Valid value:                                                                                                                                                                                                                    |
      |                       |                       |                                                                                                                                                                                                                                 |
      |                       |                       | -  **master**: This value is returned for the mongos node.                                                                                                                                                                      |
      |                       |                       | -  **Primary**: This value is returned for the primary node of shards, primary node of configs, primary node of a replica set.                                                                                                  |
      |                       |                       | -  **Secondary**: This value is returned for the secondary node of shards, secondary node of configs, and secondary node of a replica set.                                                                                      |
      |                       |                       | -  **Hidden**: This value is returned for the hidden node of shards, hidden node of configs, and hidden node of a replica set.                                                                                                  |
      |                       |                       | -  **unknown**. This value is returned when the node is abnormal.                                                                                                                                                               |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | private_ip            | String                | Indicates the private IP address of a node. This parameter is valid only for mongos nodes, replica set instances. The value exists only after ECSs are created successfully. Otherwise, the value is **""**.                    |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | public_ip             | String                | Indicates the EIP that has been bound. This parameter is valid only for mongos nodes of cluster instances, primary nodes and secondary nodes of replica set instances.                                                          |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | spec_code             | String                | Indicates the resource specifications code. For details about the instance specifications, see the value of the **flavors.spec_code** parameter in :ref:`Querying All DB Instance Specifications <dds_instance_specification>`. |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | availability_zone     | String                | Indicates the AZ.                                                                                                                                                                                                               |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. note::

      The values of **region** and **availability_zone** are used as examples.

-  Response example

   Query all DB instances.

   .. code-block:: text

      {
          "instances": [
              {
                  "id": "8436a91546294036b75931e879882200in02",
                  "name": "dds-efa6",
                  "status": "normal",
                  "port": "8635",
                  "mode": "ReplicaSet",
                  "region": "aaa",
                  "datastore": {
                      "type": "DDS-Community",
                      "version": "3.4"
                  },
                  "engine": "wiredTiger",
                  "created": "2019-01-17T07:05:52",
                  "updated": "2019-01-17T07:05:47",
                  "db_user_name": "rwuser",
                  "ssl": "1",
                  "vpc_id": "674e9b42-cd8d-4d25-a2e6-5abcc565b961",
                  "subnet_id": "f1df08c5-71d1-406a-aff0-de435a51007b",
                  "security_group_id": "7aa51dbf-5b63-40db-9724-dad3c4828b58",
                  "backup_strategy": {
                      "start_time": "16:00-17:00",
                      "keep_days": 7
                  },
                  "pay_mode": "0",
                  "maintenance_window": "02:00-06:00",
                  "groups": [
                      {
                          "type": "replica",
                          "volume": {
                              "size": "10",
                              "used": "0.33"
                          },
                          "nodes": [
                              {
                                  "id": "233eaac9c6f245c0bb9c2d21eea12d1bno02",
                                  "name": "dds-efa6_replica_node_2",
                                  "status": "normal",
                                  "role": "Primary",
                                  "private_ip": "192.168.0.174",
                                  "public_ip": "",
                                  "spec_code": "dds.mongodb.s2.medium.4.repset",
                                  "availability_zone": "bbb"
                              },
                              {
                                  "id": "d57d76d6320a4a7b86db82c317550c4ano02",
                                  "name": "dds-efa6_replica_node_1",
                                  "status": "normal",
                                  "role": "Hidden",
                                  "private_ip": "192.168.0.39",
                                  "public_ip": "",
                                  "spec_code": "dds.mongodb.s2.medium.4.repset",
                                  "availability_zone": "bbb"
                              },
                              {
                                  "id": "f46b0a1cf4d9400e9fd7af17f8742d37no02",
                                  "name": "dds-efa6_replica_node_3",
                                  "status": "normal",
                                  "role": "Secondary",
                                  "private_ip": "192.168.0.176",
                                  "public_ip": "",
                                  "spec_code": "dds.mongodb.s2.medium.4.repset",
                                  "availability_zone": "bbb"
                              }
                          ]
                      }
                  ],
                  "time_zone": "",
                  "actions": [
                    "CREATE"
                   ]
              },
              {
                  "id": "9136fd2a9fcd405ea4674276ce36dae8in02",
                  "name": "dds-32f4",
                  "status": "normal",
                  "port": "8635",
                  "mode": "Sharding",
                  "region": "aaa",
                  "datastore": {
                      "type": "DDS-Community",
                      "version": "3.4"
                  },
                  "engine": "wiredTiger",
                  "created": "2019-01-17T07:04:37",
                  "updated": "2019-01-17T07:04:31",
                  "db_user_name": "rwuser",
                  "ssl": "1",
                  "vpc_id": "674e9b42-cd8d-4d25-a2e6-5abcc565b961",
                  "subnet_id": "f1df08c5-71d1-406a-aff0-de435a51007b",
                  "security_group_id": "7aa51dbf-5b63-40db-9724-dad3c4828b58",
                  "backup_strategy": {
                      "start_time": "19:00-20:00",
                      "keep_days": 7
                  },
                  "pay_mode": "0",
                  "maintenance_window": "02:00-06:00",
                  "groups": [
                      {
                          "type": "mongos",
                          "nodes": [
                              {
                                  "id": "a742c13a284949adad177672e8a0f01cno02",
                                  "name": "dds-32f4_mongos_node_1",
                                  "status": "normal",
                                  "role": "master",
                                  "private_ip": "192.168.0.56",
                                  "public_ip": "",
                                  "spec_code": "dds.mongodb.s2.medium.4.mongos",
                                  "availability_zone": "bbb"
                              },
                              {
                                  "id": "d4f66666b1d64ab28719da0526341c7eno02",
                                  "name": "dds-32f4_mongos_node_2",
                                  "status": "normal",
                                  "role": "master",
                                  "private_ip": "192.168.0.185",
                                  "public_ip": "",
                                  "spec_code": "dds.mongodb.s2.medium.4.mongos",
                                  "availability_zone": "bbb"
                              }
                          ]
                      },
                      {
                          "type": "shard",
                          "id": "d1b92d2cbd544e85ac7ce6a7f33ba205gr02",
                          "name": "shard_2",
                          "status": "normal",
                          "volume": {
                              "size": "10",
                              "used": "0.33"
                          },
                          "nodes": [
                              {
                                  "id": "0e9abaebe5974b63a5b221de6ee34cfeno02",
                                  "name": "dds-32f4_shard_2_node_3",
                                  "status": "normal",
                                  "role": "Primary",
                                  "spec_code": "dds.mongodb.s2.medium.4.shard",
                                  "availability_zone": "bbb"
                              },
                              {
                                  "id": "1d7f4c5476c04cc187f920925c2b601fno02",
                                  "name": "dds-32f4_shard_2_node_2",
                                  "status": "normal",
                                  "role": "Hidden",
                                  "spec_code": "dds.mongodb.s2.medium.4.shard",
                                  "availability_zone": "bbb"
                              },
                              {
                                  "id": "3dd2cce03da54fc08f10651cbfea778dno02",
                                  "name": "dds-32f4_shard_2_node_1",
                                  "status": "normal",
                                  "role": "Secondary",
                                  "spec_code": "dds.mongodb.s2.medium.4.shard",
                                  "availability_zone": "bbb"
                              }
                          ]
                      },
                      {
                          "type": "shard",
                          "id": "06439baa35c146d3a8965af59d370908gr02",
                          "name": "shard_1",
                          "status": "normal",
                          "volume": {
                              "size": "10",
                              "used": "0.33"
                          },
                          "nodes": [
                              {
                                  "id": "0f6744d7e29f42ff80fc1a36cc145042no02",
                                  "name": "dds-32f4_shard_1_node_1",
                                  "status": "normal",
                                  "role": "Primary",
                                  "spec_code": "dds.mongodb.s2.medium.4.shard",
                                  "availability_zone": "bbb"
                              },
                              {
                                  "id": "3abcb399113b4512bd5a906da54e8753no02",
                                  "name": "dds-32f4_shard_1_node_3",
                                  "status": "normal",
                                  "role": "Hidden",
                                  "spec_code": "dds.mongodb.s2.medium.4.shard",
                                  "availability_zone": "bbb"
                              },
                              {
                                  "id": "c149f70563494501b5706cad225a8ebdno02",
                                  "name": "dds-32f4_shard_1_node_2",
                                  "status": "normal",
                                  "role": "Secondary",
                                  "spec_code": "dds.mongodb.s2.medium.4.shard",
                                  "availability_zone": "bbb"
                              }
                          ]
                      },
                      {
                          "type": "config",
                          "id": "84e7c96b82aa4fedb3b00f98edd71ba4gr02",
                          "name": "config",
                          "status": "normal",
                          "volume": {
                              "size": "20",
                              "used": "0.33"
                          },
                          "nodes": [
                              {
                                  "id": "7422f7331b714ac39aa647a1ec968d33no02",
                                  "name": "dds-32f4_config_node_2",
                                  "status": "normal",
                                  "role": "Primary",
                                  "spec_code": "dds.mongodb.s2.large.2.config",
                                  "availability_zone": "bbb"
                              },
                              {
                                  "id": "9e3b343151044eda91ddb8a42ae5cbefno02",
                                  "name": "dds-32f4_config_node_3",
                                  "status": "normal",
                                  "role": "Hidden",
                                  "spec_code": "dds.mongodb.s2.large.2.config",
                                  "availability_zone": "bbb"
                              },
                              {
                                  "id": "c0053ca460ac4889841ffb14a886ec54no02",
                                  "name": "dds-32f4_config_node_1",
                                  "status": "normal",
                                  "role": "Secondary",
                                  "spec_code": "dds.mongodb.s2.large.2.config",
                                  "availability_zone": "bbb"
                              }
                          ]
                      }
                  ],
                  "time_zone": "",
                  "actions": [
                    "CREATE"
                   ]
              }
          ],
          "total_count": 2
      }

**Status Code**
---------------

For more information, see :ref:`Status Code <dds_status_code>`.

Error Code
----------

For more information, see :ref:`Error Code <dds_error_code>`.
