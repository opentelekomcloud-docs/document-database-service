:original_name: dds_connect_0003.html

.. _dds_connect_0003:

Killing Sessions of an Instance Node
====================================

Function
--------

This API is used to kill sessions of an instance node.

Constraints
-----------

-  Community Edition 4.0, 4.2, 4.4, and 5.0 instances are supported.
-  Inactive sessions cannot be terminated.

URI
---

-  URI format

   POST https://{Endpoint}/v3/{project_id}/nodes/{node_id}/session

-  Parameter description

   .. table:: **Table 1** Path parameters

      +------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter  | Mandatory | Type   | Description                                                                                                                                         |
      +============+===========+========+=====================================================================================================================================================+
      | project_id | Yes       | String | Specifies the project ID of a tenant in a region.                                                                                                   |
      +------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
      | node_id    | Yes       | String | Specifies the node ID. The following nodes can be queried: mongos nodes in the cluster, and all nodes in the replica set and single node instances. |
      +------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------------------------------+

Requests
--------

-  Parameter description

   .. table:: **Table 2** Request body parameters

      +-----------------+-----------------+------------------+---------------------------------------------------------------------------------------------------+
      | Parameter       | Mandatory       | Type             | Description                                                                                       |
      +=================+=================+==================+===================================================================================================+
      | sessions        | Yes             | Array of strings | Specifies the IDs of sessions to be terminated.                                                   |
      |                 |                 |                  |                                                                                                   |
      |                 |                 |                  | For details, see the session ID returned in :ref:`Table 4 <dds_connect_0002__table599818593239>`. |
      +-----------------+-----------------+------------------+---------------------------------------------------------------------------------------------------+

-  Request example

   .. code-block:: text

      POST https://dds.eu-de.otc.t-systems.com/v3/619d3e78f61b4be68bc5aa0b59edcf7b/nodes/520c58ba00a3497e97ce0b9604874dd6no02/session
      {
        "sessions" : [ "34631", "34703" ]
      }

-  Example request

   .. code-block:: text

      POST https://dds.eu-de.otc.t-systems.com/v3/619d3e78f61b4be68bc5aa0b59edcf7b/nodes/520c58ba00a3497e97ce0b9604874dd6no02/session
      {
        "sessions" : [ "34631", "34703" ]
      }

Responses
---------

{}

Status Code
-----------

Status Code:200.

For more information, see :ref:`Status Code <dds_status_code>`.

Error Code
----------

For more information, see :ref:`Error Code <dds_error_code>`.
