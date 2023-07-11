:original_name: dds_api_0104.html

.. _dds_api_0104:

Configuring Cross-CIDR Access for a Replica Set
===============================================

Function
--------

This API is used to configure cross-CIDR access for a replica set instance.

Constraints
-----------

Only replica set instances are supported.

URI
---

-  URI format

   POST https://{Endpoint}/v3/{project_id}/instances/{instance_id}/client-network

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

      +-----------------------+-----------------+------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name                  | Mandatory       | Type             | Description                                                                                                                                                                                                                                                                                                                                                                             |
      +=======================+=================+==================+=========================================================================================================================================================================================================================================================================================================================================================================================+
      | client_network_ranges | Yes             | Array of strings | CIDR block where the client is located                                                                                                                                                                                                                                                                                                                                                  |
      |                       |                 |                  |                                                                                                                                                                                                                                                                                                                                                                                         |
      |                       |                 |                  | .. note::                                                                                                                                                                                                                                                                                                                                                                               |
      |                       |                 |                  |                                                                                                                                                                                                                                                                                                                                                                                         |
      |                       |                 |                  |    -  Cross-CIDR access is required only when the CIDR blocks of the client and the replica set instance are different. For example, if the client CIDR block is 192.168.0.0/16 and the replica set instance's CIDR block is 172.16.0.0/24, add the CIDR block 192.168.0.0/16 so that the client can access the replica set instance. This function is available only for replica sets. |
      |                       |                 |                  |    -  For example, if the source network segment is 192.168.0.0/*xx*, the value of *xx* must range from **8** to **32**.                                                                                                                                                                                                                                                                |
      |                       |                 |                  |    -  To ensure the ECS and the instance can communicate with each other, configure the connection by referring to VPC Peering Connection Overview.                                                                                                                                                                                                                                     |
      +-----------------------+-----------------+------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Request example

   POST https://dds.eu-de.otc.t-systems.com/v3/0549b4a43100d4f32f51c01c2fe4acdb/instances/9136fd2a9fcd405ea4674276ce36dae8in02/client-network

   .. code-block:: text

      {
          "client_network_ranges":["192.168.0.0/16"]
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
