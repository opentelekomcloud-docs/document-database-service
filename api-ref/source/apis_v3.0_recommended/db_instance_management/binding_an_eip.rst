:original_name: dds_api_0056.html

.. _dds_api_0056:

Binding an EIP
==============

Function
--------

This API is used to bind an EIP to a node in a DB instance.

Constraints
-----------

-  This operation cannot be performed on frozen or abnormal instances.
-  Hidden nodes do not support this operation.
-  Multiple EIPs cannot be bound to the same node.

URI
---

-  URI format

   POST https://{Endpoint}/v3/{project_id}/nodes/{node_id}/bind-eip

-  Parameter description

   .. table:: **Table 1** Parameter description

      +-----------------------+-----------------------+--------------------------------------------------------------------+
      | Name                  | Mandatory             | Description                                                        |
      +=======================+=======================+====================================================================+
      | project_id            | Yes                   | Specifies the project ID of a tenant in a region.                  |
      +-----------------------+-----------------------+--------------------------------------------------------------------+
      | node_id               | Yes                   | Specifies the ID of the node to which the EIP is to be bound.      |
      |                       |                       |                                                                    |
      |                       |                       | -  Select the mongos node in a cluster instance                    |
      |                       |                       | -  Select the primary or secondary node in a replica set instance. |
      |                       |                       | -  Select the primary node in a single node instance               |
      +-----------------------+-----------------------+--------------------------------------------------------------------+

Requests
--------

-  Parameter description

   .. table:: **Table 2** Parameter description

      ============ ========= ====== ============================
      Name         Mandatory Type   Description
      ============ ========= ====== ============================
      public_ip_id Yes       String Specifies the ID of the EIP.
      public_ip    Yes       String Specifies the EIP.
      ============ ========= ====== ============================

-  Example request

   POST https://dds.eu-de.otc.t-systems.com/v3/0549b4a43100d4f32f51c01c2fe4acdb/nodes/4709a6332ce348718b5675aadb5e2bccno02/bind-eip

   .. code-block:: text

      {
          "public_ip": "10.145.51.128",
          "public_ip_id": "45da4782-e0c8-4aa4-a290-b8740014f710"
      }

Responses
---------

-  Parameter description

   .. table:: **Table 3** Parameter description

      ============ ====== ============================
      Name         Type   Description
      ============ ====== ============================
      job_id       String Indicates the workflow ID.
      node_name    String Indicates the node name.
      node_id      String Indicates the node ID.
      public_ip_id String Indicates the ID of the EIP.
      public_ip    String Indicates the EIP.
      ============ ====== ============================

-  Response example

   .. code-block:: text

      {
          "job_id":"3711e2ad-5787-49bc-a47f-3f0b066af9f5",
          "node_id":"52a4c096bb1f455d8d866956a959519eno02",
          "node_name":"mongodb-8977_mongos_node_1",
          "public_ip":"10.145.51.128",
          "public_ip_id":"45da4782-e0c8-4aa4-a290-b8740014f710"
      }

Status Code
-----------

Status Code:200.

For more information, see :ref:`Status Code <dds_status_code>`.

Error Code
----------

For more information, see :ref:`Error Code <dds_error_code>`.
