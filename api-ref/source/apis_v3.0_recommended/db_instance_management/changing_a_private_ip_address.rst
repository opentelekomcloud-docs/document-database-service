:original_name: dds_api_0058.html

.. _dds_api_0058:

Changing a Private IP Address
=============================

Function
--------

This API is used to change the private IP address of a DB instance.

Constraints
-----------

-  This operation cannot be performed on frozen or abnormal instances.
-  An in-use IP address cannot be used as the new private IP address of a DB instance.
-  Changing the private IP address will cause the original database connection address to become invalid. If an EIP has been bound to the DB instance, do not unbind the EIP when the private IP address is being changed.
-  This operation is not allowed if connection address switchover is enabled.
-  Currently, only the IPv4 address is supported.

URI
---

-  URI format

   POST https://{Endpoint}/v3/{project_id}/instances/{instance_id}/modify-internal-ip

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

      +---------+-----------+--------+-----------------------------------------------------------------------------------------------------+
      | Name    | Mandatory | Type   | Description                                                                                         |
      +=========+===========+========+=====================================================================================================+
      | new_ip  | Yes       | String | Specifies the new IP address, which must be in an available VPC CIDR block. Only IPv4 is supported. |
      +---------+-----------+--------+-----------------------------------------------------------------------------------------------------+
      | node_id | Yes       | String | Specifies the node ID.                                                                              |
      +---------+-----------+--------+-----------------------------------------------------------------------------------------------------+

-  Example request

   POST https://dds.eu-de.otc.t-systems.com/v3/0549b4a43100d4f32f51c01c2fe4acdb/instances/9136fd2a9fcd405ea4674276ce36dae8in02/modify-internal-ip

   .. code-block:: text

      {
          "node_id": "52a4c096bb1f455d8d866956a959519eno02",
          "new_ip": "192.168.0.133"
      }

Responses
---------

-  Parameter description

   .. table:: **Table 3** Parameter description

      ======= ====== =====================================
      Name    Type   Description
      ======= ====== =====================================
      job_id  String Indicates the workflow ID.
      node_id String Indicates the node ID.
      new_ip  String Indicates the new private IP address.
      ======= ====== =====================================

-  Response example

   .. code-block:: text

      {
           "job_id":"3711e2ad-5787-49bc-a47f-3f0b066af9f5",
           "node_id":"52a4c096bb1f455d8d866956a959519eno02",
           "new_ip":"192.168.0.133"
       }

Status Code
-----------

Status Code:200.

For more information, see :ref:`Status Code <dds_status_code>`.

Error Code
----------

For more information, see :ref:`Error Code <dds_error_code>`.
