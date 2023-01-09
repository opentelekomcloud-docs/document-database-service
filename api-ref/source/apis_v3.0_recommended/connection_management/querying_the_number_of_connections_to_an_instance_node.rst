:original_name: dds_connect_0004.html

.. _dds_connect_0004:

Querying the Number of Connections to an Instance Node
======================================================

Function
--------

This API is used to query the number of connections from each client to DDS DB instances.

Constraints
-----------

Frozen instances do not support this operation.

URI
---

-  URI format

   GET https://{Endpoint}/v3/{project_id}/instances/{instance_id}/conn-statistics?node_id={node_id}

-  Parameter description

   .. table:: **Table 1** Path parameters

      +-------------+-----------+--------+---------------------------------------------------+
      | Parameter   | Mandatory | Type   | Description                                       |
      +=============+===========+========+===================================================+
      | project_id  | Yes       | String | Specifies the project ID of a tenant in a region. |
      +-------------+-----------+--------+---------------------------------------------------+
      | instance_id | Yes       | String | Specifies the DB instance ID.                     |
      +-------------+-----------+--------+---------------------------------------------------+

   .. table:: **Table 2** Query parameters

      +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------+
      | Parameter       | Mandatory       | Type            | Description                                                                                                               |
      +=================+=================+=================+===========================================================================================================================+
      | node_id         | No              | String          | Specifies the node ID.                                                                                                    |
      |                 |                 |                 |                                                                                                                           |
      |                 |                 |                 | If this parameter is left blank, the number of connections of all nodes that can be connected in the instance is queried. |
      +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------+

Requests
--------

-  Example request

   GET https://dds.eu-de.otc.t-systems.com/v3/0549b4a43100d4f32f51c01c2fe4acdb/instances/cc6345c64cec47499182467ea0dd432ain02/conn-statistics?node_id=51a90da2cfc846688abcdd23861077b5no02

Responses
---------

-  Response parameters

   .. table:: **Table 3** Response body parameters

      +-------------------------+------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter               | Type             | Description                                                                                                                                                 |
      +=========================+==================+=============================================================================================================================================================+
      | total_connections       | Integer          | Indicates the total number of connections, including internal and external connections.                                                                     |
      +-------------------------+------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | total_inner_connections | Integer          | Indicates the total number of internal connections.                                                                                                         |
      +-------------------------+------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | total_outer_connections | Integer          | Indicates the total number of external connections.                                                                                                         |
      +-------------------------+------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | inner_connections       | Array of objects | Indicates the internal connection statistics array. Up to 200 records are supported. For details, see :ref:`Table 4 <dds_connect_0004__table599818593239>`. |
      +-------------------------+------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | outer_connections       | Array of objects | Indicates the external connection statistics array. Up to 200 records are supported. For details, see :ref:`Table 4 <dds_connect_0004__table599818593239>`. |
      +-------------------------+------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. _dds_connect_0004__table599818593239:

   .. table:: **Table 4** QueryConnectionsResponse

      +-----------+---------+---------------------------------------------------------------------------+
      | Parameter | Type    | Description                                                               |
      +===========+=========+===========================================================================+
      | client_ip | String  | Indicates the IP address of the client connected to the instance or node. |
      +-----------+---------+---------------------------------------------------------------------------+
      | count     | Integer | Indicates the number of connections corresponding to the IP address.      |
      +-----------+---------+---------------------------------------------------------------------------+

-  Response example

   .. code-block:: text

      {
          "total_connections": 75,
          "total_inner_connections": 50,
          "total_outer_connections": 25,
          "inner_connections": [
              {"client_ip": "10.10.10.24", "count": 19},
              {"client_ip": "9.3.185.42", "count": 6},
              {"client_ip": "10.10.4.156", "count": 3}
          ],
          "outer_connections": [
              {"client_ip": "10.10.10.25", "count": 11},
              {"client_ip": "9.3.185.46", "count": 8},
              {"client_ip": "10.10.4.157", "count": 4}
          ]
      }

Status Code
-----------

Status Code:200.

For more information, see :ref:`Status Code <dds_status_code>`.

Error Code
----------

For more information, see :ref:`Error Code <dds_error_code>`.
