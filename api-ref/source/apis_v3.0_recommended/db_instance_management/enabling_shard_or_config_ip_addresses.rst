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
-  Cluster instances of Community Edition 3.4 and 4.0 are supported.
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

      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name            | Mandatory       | Type            | Description                                                                                                                                                                             |
      +=================+=================+=================+=========================================================================================================================================================================================+
      | type            | Yes             | String          | Specifies the type of the object for which the IP address is to be enabled.                                                                                                             |
      |                 |                 |                 |                                                                                                                                                                                         |
      |                 |                 |                 | -  To enable IP addresses for shard nodes, set the value to **shard**.                                                                                                                  |
      |                 |                 |                 | -  To enable IP addresses for config nodes, set the value to **config**.                                                                                                                |
      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | target_id       | No              | String          | Specifies the ID of the group whose IP addresses are to be enabled.                                                                                                                     |
      |                 |                 |                 |                                                                                                                                                                                         |
      |                 |                 |                 | -  For shard nodes, the value is the shard ID.                                                                                                                                          |
      |                 |                 |                 | -  For config nodes, the value is the config ID.                                                                                                                                        |
      |                 |                 |                 | -  If this parameter is left blank, enable all IP addresses of the same node type in the instance.                                                                                      |
      |                 |                 |                 |                                                                                                                                                                                         |
      |                 |                 |                 | .. caution::                                                                                                                                                                            |
      |                 |                 |                 |                                                                                                                                                                                         |
      |                 |                 |                 |    CAUTION:                                                                                                                                                                             |
      |                 |                 |                 |                                                                                                                                                                                         |
      |                 |                 |                 |    -  If the IP address is enabled for the first time, leave this parameter empty.                                                                                                      |
      |                 |                 |                 |    -  If the IP address is enabled, this parameter cannot be delivered repeatedly.                                                                                                      |
      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | password        | Yes             | String          | Specifies the password for enabling this function for a cluster.                                                                                                                        |
      |                 |                 |                 |                                                                                                                                                                                         |
      |                 |                 |                 | -  The value must be 8 to 32 characters in length and contain uppercase letters (A to Z), lowercase letters (a to z), digits (0 to 9), and special characters, such as ``~!@#%^*-_=+?`` |
      |                 |                 |                 | -  Enter a strong password to improve security, preventing security risks such as brute force cracking.                                                                                 |
      |                 |                 |                 |                                                                                                                                                                                         |
      |                 |                 |                 | .. caution::                                                                                                                                                                            |
      |                 |                 |                 |                                                                                                                                                                                         |
      |                 |                 |                 |    CAUTION:                                                                                                                                                                             |
      |                 |                 |                 |    This password cannot be changed. Exercise caution when performing this operation.                                                                                                    |
      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

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
