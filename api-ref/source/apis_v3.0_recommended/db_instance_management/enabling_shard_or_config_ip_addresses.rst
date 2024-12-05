:original_name: dds_api_0120.html

.. _dds_api_0120:

Enabling Shard or Config IP Addresses
=====================================

Function
--------

This API is used to enable the IP addresses of shard or config nodes.

Constraints
-----------

-  Frozen instances do not support this operation.
-  DB instances associated with the IPv6 subnet do not support this operation.
-  If the IP address is enabled, restart the nodes for the setting to take effect.
-  Cluster instances of Community Edition 3.4, 4.0, 4.2 and 4.4 are supported.
-  This function cannot be disabled after being enabled.

URI
---

-  URI format

   POST https://{Endpoint}/v3/{project_id}/instances/{instance_id}/create-ip

-  Parameter description

   .. table:: **Table 1** Parameter description

      +-------------+-----------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name        | Mandatory | Description                                                                                                                                                                     |
      +=============+===========+=================================================================================================================================================================================+
      | project_id  | Yes       | Specifies the project ID of a tenant in a region.                                                                                                                               |
      +-------------+-----------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | instance_id | Yes       | Specifies the instance ID, which can be obtained by calling the API for querying instances. If you do not have an instance, you can call the API used for creating an instance. |
      +-------------+-----------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Requests
--------

-  Parameter description

   .. table:: **Table 2** Parameter description

      +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name            | Type            | Mandatory       | Description                                                                                                                                                                                                                                                                                                                                          |
      +=================+=================+=================+======================================================================================================================================================================================================================================================================================================================================================+
      | type            | String          | Yes             | Cluster instance type.                                                                                                                                                                                                                                                                                                                               |
      |                 |                 |                 |                                                                                                                                                                                                                                                                                                                                                      |
      |                 |                 |                 | -  When applying for a shard IP address, set the value to **shard**. A read-only user **sharduser** is automatically created for the shard group. (Each shard group has a read-only user with the same name.)                                                                                                                                        |
      |                 |                 |                 |                                                                                                                                                                                                                                                                                                                                                      |
      |                 |                 |                 | -  When applying for a config IP address, set the value to **config**. A read-only user **csuser** is automatically created for the config group.                                                                                                                                                                                                    |
      +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | target_id       | String          | No              | Shard group ID.                                                                                                                                                                                                                                                                                                                                      |
      |                 |                 |                 |                                                                                                                                                                                                                                                                                                                                                      |
      |                 |                 |                 | .. caution::                                                                                                                                                                                                                                                                                                                                         |
      |                 |                 |                 |                                                                                                                                                                                                                                                                                                                                                      |
      |                 |                 |                 |    CAUTION:                                                                                                                                                                                                                                                                                                                                          |
      |                 |                 |                 |                                                                                                                                                                                                                                                                                                                                                      |
      |                 |                 |                 |    -  If you apply for a shard or config IP address for the first time, this parameter is not specified. You can apply for an IP address for all shard groups using the same password and create a read-only user **sharduser**.                                                                                                                     |
      |                 |                 |                 |    -  In node scale-out scenarios, the system does not automatically apply for an IP address and read-only user **sharduser** for the new shard group because there is no **sharduser** user and password of other shard groups. If you need to apply for an IP address for the new shard group, call this API and specify **target_id** (group ID). |
      |                 |                 |                 |    -  If this API is called for multiple times for the same DB instance, the values for the **password** field can be different. (Each shard group has a read-only user with the same name.)                                                                                                                                                         |
      +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | password        | String          | Yes             | The password for enabling this function for a cluster.                                                                                                                                                                                                                                                                                               |
      |                 |                 |                 |                                                                                                                                                                                                                                                                                                                                                      |
      |                 |                 |                 | -  The value must be 8 to 32 characters in length and contain uppercase letters (A to Z), lowercase letters (a to z), digits (0 to 9), and special characters, such as ``~!@#%^*-_=+?()$``                                                                                                                                                           |
      |                 |                 |                 | -  Enter a strong password to improve security, preventing security risks such as brute force cracking.                                                                                                                                                                                                                                              |
      |                 |                 |                 |                                                                                                                                                                                                                                                                                                                                                      |
      |                 |                 |                 | .. caution::                                                                                                                                                                                                                                                                                                                                         |
      |                 |                 |                 |                                                                                                                                                                                                                                                                                                                                                      |
      |                 |                 |                 |    CAUTION:                                                                                                                                                                                                                                                                                                                                          |
      |                 |                 |                 |    The password can be changed by calling the API for changing a database user password. After the API for changing a database user password is called, the passwords of the read-only user **sharduser** of all shard groups are the same when **target_id** is specified.                                                                          |
      +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Request example

   POST https://dds.eu-de.otc.t-systems.com/v3/0549b4a43100d4f32f51c01c2fe4acdb/instances/9136fd2a9fcd405ea4674276ce36dae8in02/create-ip

   .. code-block:: text

      {
          "type": "shard",
          "target_id": "91bac9f23ead42e19013333e05f44829gr02",
          "password": "******"
      }

Responses
---------

-  Response example

   .. code-block:: text

      {}

Status Code
-----------

Status Code:200.

For more information, see :ref:`Status Code <dds_status_code>`.

Error Code
----------

For more information, see :ref:`Error Code <dds_error_code>`.
