:original_name: dds_api_0057.html

.. _dds_api_0057:

Unbinding an EIP
================

Function
--------

This API is used to unbind an EIP from a node in a DB instance.

Constraints
-----------

-  Frozen instances do not support this operation.
-  This operation can be performed only on a node with an EIP assigned.

URI
---

-  URI format

   POST https://{Endpoint}/v3/{project_id}/nodes/{node_id}/unbind-eip

-  Parameter description

   .. table:: **Table 1** Parameter description

      +------------+-----------+-------------------------------------------------------------------+
      | Name       | Mandatory | Description                                                       |
      +============+===========+===================================================================+
      | project_id | Yes       | Specifies the project ID of a tenant in a region.                 |
      +------------+-----------+-------------------------------------------------------------------+
      | node_id    | Yes       | Specifies the ID of the node from which the EIP is to be unbound. |
      +------------+-----------+-------------------------------------------------------------------+

Requests
--------

-  Example request

   POST https://dds.eu-de.otc.t-systems.com/v3/0549b4a43100d4f32f51c01c2fe4acdb/nodes/4709a6332ce348718b5675aadb5e2bccno02/unbind-eip

Responses
---------

-  Parameter description

   .. table:: **Table 2** Parameter description

      ========= ====== ==========================
      Name      Type   Description
      ========= ====== ==========================
      job_id    String Indicates the workflow ID.
      node_name String Indicates the node name.
      node_id   String Indicates the node ID.
      ========= ====== ==========================

-  Response example

   .. code-block:: text

      {
          "job_id": "3711e2ad-5787-49bc-a47f-3f0b066af9f5",
          "node_id": "52a4c096bb1f455d8d866956a959519eno02",
          "node_name": "mongodb-8977_mongos_node_1"
       }

Status Code
-----------

Status Code:200.

For more information, see :ref:`Status Code <dds_status_code>`.

Error Code
----------

For more information, see :ref:`Error Code <dds_error_code>`.
