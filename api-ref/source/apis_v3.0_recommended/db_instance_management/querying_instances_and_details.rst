:original_name: dds_api_0023.html

.. _dds_api_0023:

Querying Instances and Details
==============================

Function
--------

This API is used to query instances and details based on specified conditions.

URI
---

-  URI format

   GET https://{Endpoint}/v3/{project_id}/instances?id={id}&name={name}&mode={mode}&datastore_type={datastore_type}&vpc_id={vpc_id}&subnet_id={subnet_id}&offset={offset}&limit={limit}&tags={key}={value},{key}={value}

-  Parameter description

   .. table:: **Table 1** Parameter description

      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name            | Mandatory       | Type            | Description                                                                                                                                                                                                           |
      +=================+=================+=================+=======================================================================================================================================================================================================================+
      | project_id      | Yes             | String          | Specifies the project ID of a tenant in a region.                                                                                                                                                                     |
      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | id              | No              | String          | Specifies the instance ID, which can be obtained by calling the API for querying instances and details. If you do not have an instance, you can call the API used for creating an instance.                           |
      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | name            | No              | String          | Specifies the DB instance name.                                                                                                                                                                                       |
      |                 |                 |                 |                                                                                                                                                                                                                       |
      |                 |                 |                 | If you use asterisk (``*``) at the beginning of the name, fuzzy search results are returned. Otherwise, the exact results are returned.                                                                               |
      |                 |                 |                 |                                                                                                                                                                                                                       |
      |                 |                 |                 | .. note::                                                                                                                                                                                                             |
      |                 |                 |                 |                                                                                                                                                                                                                       |
      |                 |                 |                 |    The asterisk (``*``) is a reserved character in the system and cannot be used alone.                                                                                                                               |
      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | mode            | No              | String          | Specifies the instance type.                                                                                                                                                                                          |
      |                 |                 |                 |                                                                                                                                                                                                                       |
      |                 |                 |                 | -  **Sharding** indicates the cluster instance.                                                                                                                                                                       |
      |                 |                 |                 | -  **ReplicaSet** indicate the replica set instance.                                                                                                                                                                  |
      |                 |                 |                 | -  **Single** indicates the single node instance.                                                                                                                                                                     |
      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | datastore_type  | No              | String          | Specifies the database type. The value is **DDS-Community**.                                                                                                                                                          |
      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | vpc_id          | No              | String          | Specifies the VPC ID. To obtain this parameter value, use either of the following methods:                                                                                                                            |
      |                 |                 |                 |                                                                                                                                                                                                                       |
      |                 |                 |                 | -  Method 1: Log in to VPC console and view the VPC ID on the VPC details page.                                                                                                                                       |
      |                 |                 |                 | -  Method 2: See the "Querying VPCs" section in the *Virtual Private Cloud API Reference*.                                                                                                                            |
      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | subnet_id       | No              | String          | Specifies the network ID of the subnet. To obtain this parameter value, use either of the following methods:                                                                                                          |
      |                 |                 |                 |                                                                                                                                                                                                                       |
      |                 |                 |                 | -  Method 1: Log in to VPC console and click the target subnet on the **Subnets** page. You can view the network ID on the displayed page.                                                                            |
      |                 |                 |                 | -  Method 2: See the "Querying Subnets" section in the *Virtual Private Cloud API Reference*.                                                                                                                         |
      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | offset          | No              | Integer         | Specifies the index position. The query starts from the next instance creation time indexed by this parameter under a specified project. If offset is set to N, the resource query starts from the N+1 piece of data. |
      |                 |                 |                 |                                                                                                                                                                                                                       |
      |                 |                 |                 | The value must be greater than or equal to **0**. If this parameter is not transferred, offset is set to **0** by default, indicating that the query starts from the latest created DB instance.                      |
      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | limit           | No              | Integer         | Specifies the maximum allowed number of DB instances.                                                                                                                                                                 |
      |                 |                 |                 |                                                                                                                                                                                                                       |
      |                 |                 |                 | The value ranges from 1 to 100. If this parameter is not transferred, the first 100 DB instances are queried by default.                                                                                              |
      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | tags            | No              | String          | Query based on the instance tag key and value.                                                                                                                                                                        |
      |                 |                 |                 |                                                                                                                                                                                                                       |
      |                 |                 |                 | {*key*} indicates the tag key, and {*value*} indicates the tag value. A maximum of 20 key-value pairs are supported. The key cannot be empty or duplicate, but the value can be empty.                                |
      |                 |                 |                 |                                                                                                                                                                                                                       |
      |                 |                 |                 | To query instances with multiple tag keys and values, separate key-value pairs with commas (,).                                                                                                                       |
      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Requests
--------

-  Example request

   -  Querying all instances and details

      GET https://dds.eu-de.otc.t-systems.com/v3/0483b6b16e954cb88930a360d2c4e663/instances

   -  Querying instances and details based on search criteria

      GET https://dds.eu-de.otc.t-systems.com/v3/0483b6b16e954cb88930a360d2c4e663/instances?offset=0&limit=10&id=ed7cc6166ec24360a5ed5c5c9c2ed726in02&name=hy&mode=ReplicaSet&datastore_type=DDS-Community&vpc_id=19e5d45d-70fd-4a91-87e9-b27e71c9891f&subnet_id=bd51fb45-2dcb-4296-8783-8623bfe89bb7&tags=key1=value1,key2=value2

Responses
---------

-  Parameter description

   .. table:: **Table 2** Parameter description

      +-----------------------+-----------------------+------------------------------------------------------------------------------+
      | Name                  | Type                  | Description                                                                  |
      +=======================+=======================+==============================================================================+
      | instances             | Array of objects      | Indicates the DB instance information.                                       |
      |                       |                       |                                                                              |
      |                       |                       | For more information, see :ref:`Table 3 <dds_api_0023__table4062895917262>`. |
      +-----------------------+-----------------------+------------------------------------------------------------------------------+
      | total_count           | Integer               | Indicates the total number of queried records.                               |
      +-----------------------+-----------------------+------------------------------------------------------------------------------+

   .. _dds_api_0023__table4062895917262:

   .. table:: **Table 3** instances field data structure description

      +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name                  | Type                  | Description                                                                                                                                                                            |
      +=======================+=======================+========================================================================================================================================================================================+
      | id                    | String                | Indicates the DB instance ID.                                                                                                                                                          |
      +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | name                  | String                | Indicates the DB instance name.                                                                                                                                                        |
      +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | remark                | String                | Instance remarks                                                                                                                                                                       |
      +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | status                | String                | Indicates the DB instance status.                                                                                                                                                      |
      |                       |                       |                                                                                                                                                                                        |
      |                       |                       | Valid value:                                                                                                                                                                           |
      |                       |                       |                                                                                                                                                                                        |
      |                       |                       | -  **normal**: indicates that the instance is running properly.                                                                                                                        |
      |                       |                       | -  **abnormal**: indicates that the instance is abnormal.                                                                                                                              |
      |                       |                       | -  **creating**: indicates that the instance is being created.                                                                                                                         |
      |                       |                       | -  **data_disk_full**: The storage space is full.                                                                                                                                      |
      |                       |                       | -  **createfail**: indicates that the instance failed to be created.                                                                                                                   |
      |                       |                       | -  **enlargefail**: indicates that nodes failed to be added to the instance.                                                                                                           |
      |                       |                       |                                                                                                                                                                                        |
      |                       |                       | .. note::                                                                                                                                                                              |
      |                       |                       |                                                                                                                                                                                        |
      |                       |                       |    Actions that are being executed on an instance, for example, rebooting, which are essentially different from the instance status. For details, see the actions field in this table. |
      +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | port                  | String                | Indicates the database port number. The port range is 2100 to 9500.                                                                                                                    |
      +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | mode                  | String                | Indicates the instance type, which is the same as the request parameter.                                                                                                               |
      +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | region                | String                | Indicates the region where the DB instance is deployed.                                                                                                                                |
      +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | datastore             | Object                | Indicates the database information.                                                                                                                                                    |
      |                       |                       |                                                                                                                                                                                        |
      |                       |                       | For more information, see :ref:`Table 4 <dds_api_0023__table5636104310403>`.                                                                                                           |
      +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | engine                | String                | Indicates the storage engine. The value is **wiredTiger**.                                                                                                                             |
      +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | created               | String                | Indicates the DB instance creation time.                                                                                                                                               |
      +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | updated               | String                | Indicates the time when a DB instance is updated.                                                                                                                                      |
      +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | db_user_name          | String                | Indicates the default username. The value is **rwuser**.                                                                                                                               |
      +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | ssl                   | Integer               | Indicates that SSL is enabled or not.                                                                                                                                                  |
      |                       |                       |                                                                                                                                                                                        |
      |                       |                       | -  **1**: indicate that SSL is enabled.                                                                                                                                                |
      |                       |                       | -  **0**: indicate that SSL is disabled.                                                                                                                                               |
      +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | vpc_id                | String                | Indicates the VPC ID.                                                                                                                                                                  |
      +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | subnet_id             | String                | Indicates the network ID of the subnet.                                                                                                                                                |
      +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | security_group_id     | String                | Indicates the security group ID.                                                                                                                                                       |
      +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | backup_strategy       | Object                | Indicates the backup policy.                                                                                                                                                           |
      |                       |                       |                                                                                                                                                                                        |
      |                       |                       | For more information, see :ref:`Table 5 <dds_api_0023__table50876711173859>`.                                                                                                          |
      +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | pay_mode              | String                | The value is set to **"0"**.                                                                                                                                                           |
      +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | maintenance_window    | String                | Indicates the maintenance time window.                                                                                                                                                 |
      +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | groups                | Array of objects      | Indicates group information.                                                                                                                                                           |
      |                       |                       |                                                                                                                                                                                        |
      |                       |                       | For more information, see :ref:`Table 6 <dds_api_0023__table0581104824211>`.                                                                                                           |
      +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | disk_encryption_id    | String                | The disk encryption key ID. This parameter is returned only when the instance disk is encrypted.                                                                                       |
      +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | enterprise_project_id | String                | Indicates the enterprise project ID.                                                                                                                                                   |
      |                       |                       |                                                                                                                                                                                        |
      |                       |                       | If the value is **0**, the resource belongs to the default enterprise project.                                                                                                         |
      +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | time_zone             | String                | Indicates the time zone.                                                                                                                                                               |
      +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | actions               | Array of strings      | Action that is being executed on an instance.                                                                                                                                          |
      |                       |                       |                                                                                                                                                                                        |
      |                       |                       | Valid value:                                                                                                                                                                           |
      |                       |                       |                                                                                                                                                                                        |
      |                       |                       | -  **RESTARTING**: The instance is being restarted.                                                                                                                                    |
      |                       |                       | -  RESTORE: restoring.                                                                                                                                                                 |
      |                       |                       | -  RESIZE_FLAVOR: The specifications are being changed.                                                                                                                                |
      |                       |                       | -  **RESTORE_TO_NEW_INSTANCE**: The instance is being restored.                                                                                                                        |
      |                       |                       | -  **MODIFY_VPC_PEER**: Cross-subnet access is being configured.                                                                                                                       |
      |                       |                       | -  CREATE: creating                                                                                                                                                                    |
      |                       |                       | -  FROZEN: The account is frozen.                                                                                                                                                      |
      |                       |                       | -  RESIZE_VOLUME: The storage is being scaled up.                                                                                                                                      |
      |                       |                       | -  RESTORE_CHECK: The restoration is being checked.                                                                                                                                    |
      |                       |                       | -  RESTORE_FAILED_HANGUP: The restoration failed.                                                                                                                                      |
      |                       |                       | -  CLOSE_AUDIT_LOG: Disabling audit log.                                                                                                                                               |
      |                       |                       | -  OPEN_AUDIT_LOG: Enabling audit log.                                                                                                                                                 |
      |                       |                       | -  CREATE_IP_SHARD: The shard IP address is being enabled.                                                                                                                             |
      |                       |                       | -  CREATE_IP_CONFIG: The config IP address is being enabled.                                                                                                                           |
      |                       |                       | -  GROWING: The node is being scaled up.                                                                                                                                               |
      |                       |                       | -  **SET_CONFIGURATION**: Parameters are being modified.                                                                                                                               |
      |                       |                       | -  RESTORE_TABLE: The database is being backed up.                                                                                                                                     |
      |                       |                       | -  **MODIFY_SECURITYGROUP**: A security group is being changed.                                                                                                                        |
      |                       |                       | -  BIND_EIP: The EIP is being changed.                                                                                                                                                 |
      |                       |                       | -  UNBIND_EIP: The EIP is being unbound.                                                                                                                                               |
      |                       |                       | -  SWITCH_SSL: The SSL is being switched.                                                                                                                                              |
      |                       |                       | -  SWITCH_PRIMARY: A primary/standby switchover is being performed.                                                                                                                    |
      |                       |                       | -  **CHANGE_DBUSER_PASSWORD**: The password is being changed.                                                                                                                          |
      |                       |                       | -  **MODIFY_PORT**: The port is being changed.                                                                                                                                         |
      |                       |                       | -  MODIFY_IP: The private IP address is being changed.                                                                                                                                 |
      |                       |                       | -  DELETE_INSTANCE: The instance is being deleted.                                                                                                                                     |
      |                       |                       | -  REBOOT: The system is restarting.                                                                                                                                                   |
      |                       |                       | -  BACKUP: The backup is in progress.                                                                                                                                                  |
      |                       |                       | -  MIGRATE_AZ: The AZ is being changed.                                                                                                                                                |
      |                       |                       | -  **RESTORING**: The backup is in progress.                                                                                                                                           |
      |                       |                       | -  **PWD_RESETING**: The password is being reset.                                                                                                                                      |
      |                       |                       | -  **UPGRADE_DATABASE**: The patch is being upgraded.                                                                                                                                  |
      |                       |                       | -  **DATA_MIGRATION**: Data is being migrated.                                                                                                                                         |
      |                       |                       | -  **SHARD_GROWING**: The shard is being scaled out.                                                                                                                                   |
      |                       |                       | -  **APPLY_CONFIGURATION**: A parameter group is being changed.                                                                                                                        |
      |                       |                       | -  **RESET_PASSWORD**: The password is being reset.                                                                                                                                    |
      |                       |                       | -  **GROWING_REVERT**: Nodes are being deleted.                                                                                                                                        |
      |                       |                       | -  **SHARD_GROWING_REVERT**: Shards are being deleted.                                                                                                                                 |
      |                       |                       | -  **LOG_PLAINTEXT_SWITCH**: The slow query log configuration is being modified.                                                                                                       |
      |                       |                       | -  **CREATE_DATABASE_USER**: The database user is being created.                                                                                                                       |
      |                       |                       | -  **CREATE_DATABASE_ROLE**: The database role is being created.                                                                                                                       |
      |                       |                       | -  **MODIFY_NAME**: The name is being changed.                                                                                                                                         |
      |                       |                       | -  **MODIFY_PRIVATE_DNS**: The private zone is being modified.                                                                                                                         |
      |                       |                       | -  **MODIFY_OP_LOG_SIZE**: The oplog size is being changed.                                                                                                                            |
      |                       |                       | -  **ADD_READONLY_NODES**: Read replicas are being scaled up.                                                                                                                          |
      +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | tags                  | Array of objects      | Tag list                                                                                                                                                                               |
      |                       |                       |                                                                                                                                                                                        |
      |                       |                       | For details, see :ref:`Table 9 <dds_api_0023__table155101048155817>`.                                                                                                                  |
      +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

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

      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name                  | Type                  | Description                                                                                                                                                                                          |
      +=======================+=======================+======================================================================================================================================================================================================+
      | type                  | String                | Indicates the node type.                                                                                                                                                                             |
      |                       |                       |                                                                                                                                                                                                      |
      |                       |                       | Valid value:                                                                                                                                                                                         |
      |                       |                       |                                                                                                                                                                                                      |
      |                       |                       | -  shard                                                                                                                                                                                             |
      |                       |                       | -  config                                                                                                                                                                                            |
      |                       |                       | -  mongos                                                                                                                                                                                            |
      |                       |                       | -  replica                                                                                                                                                                                           |
      |                       |                       | -  single                                                                                                                                                                                            |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | volume                | Object                | Indicates the volume information. For more information, see :ref:`Table 7 <dds_api_0023__table1149918231246>`. This parameter is valid only when the node type is shard, config, replica, or single. |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | nodes                 | Array of objects      | Indicates node information. For more information, see :ref:`Table 8 <dds_api_0023__table3426155424213>`.                                                                                             |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

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

      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name                  | Type                  | Description                                                                                                                                                                                                                                         |
      +=======================+=======================+=====================================================================================================================================================================================================================================================+
      | id                    | String                | Indicates the node ID.                                                                                                                                                                                                                              |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | name                  | String                | Indicates the node name.                                                                                                                                                                                                                            |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | status                | String                | Indicates the node status.                                                                                                                                                                                                                          |
      |                       |                       |                                                                                                                                                                                                                                                     |
      |                       |                       | Valid value:                                                                                                                                                                                                                                        |
      |                       |                       |                                                                                                                                                                                                                                                     |
      |                       |                       | -  **normal**: The instance is running properly.                                                                                                                                                                                                    |
      |                       |                       | -  **abnormal**: The instance is abnormal.                                                                                                                                                                                                          |
      |                       |                       | -  **backup**: The instance is being backed up.                                                                                                                                                                                                     |
      |                       |                       | -  **frozen**: The instance has been frozen.                                                                                                                                                                                                        |
      |                       |                       | -  **unfrozen**: The instance is being unfrozen.                                                                                                                                                                                                    |
      |                       |                       | -  **restore_table**: Database- and table-level backup and restoration are being performed for the DB instance.                                                                                                                                     |
      |                       |                       | -  **reboot**: The instance is being restarted.                                                                                                                                                                                                     |
      |                       |                       | -  **upgrade_database**: The instance version is being upgraded.                                                                                                                                                                                    |
      |                       |                       | -  **resize_flavor**: The instance class is being changed.                                                                                                                                                                                          |
      |                       |                       | -  **resize_volume**: The instance storage is being scaled up.                                                                                                                                                                                      |
      |                       |                       | -  **restore**: The instance is being restored.                                                                                                                                                                                                     |
      |                       |                       | -  **bind_eip**: An EIP is being bound to the instance.                                                                                                                                                                                             |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | role                  | String                | Indicates the node role.                                                                                                                                                                                                                            |
      |                       |                       |                                                                                                                                                                                                                                                     |
      |                       |                       | Valid value:                                                                                                                                                                                                                                        |
      |                       |                       |                                                                                                                                                                                                                                                     |
      |                       |                       | -  **master**: This value is returned for the mongos node.                                                                                                                                                                                          |
      |                       |                       | -  **Primary**: This value is returned for the primary shard and config nodes, the primary node of a replica set, and a single node.                                                                                                                |
      |                       |                       | -  **Secondary**: This value is returned for the secondary shard and config nodes, and the secondary node of a replica set.                                                                                                                         |
      |                       |                       | -  **Hidden**: This value is returned for the hidden shard and config nodes, and the hidden node of a replica set.                                                                                                                                  |
      |                       |                       | -  **unknown**. This value is returned when the node is abnormal.                                                                                                                                                                                   |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | private_ip            | String                | Indicates the private IP address of a node. By default, this parameter is valid only for mongos nodes, replica set instances, and single node instances. The value exists only after ECSs are created successfully. Otherwise, the value is **""**. |
      |                       |                       |                                                                                                                                                                                                                                                     |
      |                       |                       | .. caution::                                                                                                                                                                                                                                        |
      |                       |                       |                                                                                                                                                                                                                                                     |
      |                       |                       |    CAUTION:                                                                                                                                                                                                                                         |
      |                       |                       |    After the shard or config IP address is enabled, private IP addresses are assigned to the primary and secondary shard or config nodes of the cluster instance.                                                                                   |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | public_ip             | String                | Indicates the EIP that has been bound. This parameter is valid only for mongos nodes of cluster instances, primary nodes and secondary nodes of replica set instances, and single node instances.                                                   |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | spec_code             | String                | Indicates the resource specification code. For details about the instance specifications, see the value of the **flavors.spec_code** parameter in :ref:`Querying Database Specifications <dds_instance_specification>`.                             |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | availability_zone     | String                | Indicates the AZ.                                                                                                                                                                                                                                   |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. _dds_api_0023__table155101048155817:

   .. table:: **Table 9** Description of the tag field

      ===== ====== ===========
      Name  Type   Description
      ===== ====== ===========
      key   String Tag key
      value String Tag value
      ===== ====== ===========

   .. note::

      The values of **region** and **availability_zone** are used as examples.

-  Response example

   Query all instances and details.

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
                      "version": "4.0"
                  },
                  "engine": "wiredTiger",
                  "created": "2019-01-17T07:05:52",
                  "updated": "2019-01-17T07:05:47",
                  "db_user_name": "rwuser",
                  "ssl": 1,
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
                  "id": "d77905385f114217b75ae7d6ab9a7588in02",
                  "name": "dds-5699",
                  "status": "normal",
                  "port": "8635",
                  "mode": "Single",
                  "region": "aaa",
                  "datastore": {
                      "type": "DDS-Community",
                      "version": "4.0"
                  },
                  "engine": "wiredTiger",
                  "created": "2019-01-17T07:04:39",
                  "updated": "2019-01-17T07:04:33",
                  "db_user_name": "rwuser",
                  "ssl": 1,
                  "vpc_id": "674e9b42-cd8d-4d25-a2e6-5abcc565b961",
                  "subnet_id": "f1df08c5-71d1-406a-aff0-de435a51007b",
                  "security_group_id": "7aa51dbf-5b63-40db-9724-dad3c4828b58",
                  "backup_strategy": {
                      "start_time": "17:00-18:00",
                      "keep_days": 7
                  },
                  "pay_mode": "0",
                  "maintenance_window": "02:00-06:00",
                  "groups": [
                      {
                          "type": "single",
                          "volume": {
                              "size": "10",
                              "used": "0.33"
                          },
                          "nodes": [
                              {
                                  "id": "bd4dccbd53ae48d5bd3046bebf715079no02",
                                  "name": "dds-5699_single_node_1",
                                  "status": "normal",
                                  "role": "Primary",
                                  "private_ip": "192.168.0.9",
                                  "public_ip": "",
                                  "spec_code": "dds.mongodb.s2.medium.4.single",
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
                      "version": "4.0"
                  },
                  "engine": "wiredTiger",
                  "created": "2019-01-17T07:04:37",
                  "updated": "2019-01-17T07:04:31",
                  "db_user_name": "rwuser",
                  "ssl": 1,
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

Status Code
-----------

Status Code:200.

For more information, see :ref:`Status Code <dds_status_code>`.

Error Code
----------

For more information, see :ref:`Error Code <dds_error_code>`.
