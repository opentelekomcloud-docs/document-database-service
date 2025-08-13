:original_name: dds_connect_0002.html

.. _dds_connect_0002:

Querying Sessions of an Instance Node
=====================================

Function
--------

This API is used to query sessions of instance nodes.

Constraints
-----------

Community Edition 4.0, 4.2, 4.4, and 5.0 instances are supported.

URI
---

-  URI format

   GET https://{Endpoint}/v3/{project_id}/nodes/{node_id}/sessions?offset={offset}&limit={limit}&plan_summary={plan_summary}&type={type}&namespace={namespace}&cost_time={cost_time}

-  Parameter description

   .. table:: **Table 1** Path parameters

      +------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter  | Mandatory | Type   | Description                                                                                                                                         |
      +============+===========+========+=====================================================================================================================================================+
      | project_id | Yes       | String | Specifies the project ID of a tenant in a region.                                                                                                   |
      +------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
      | node_id    | Yes       | String | Specifies the node ID. The following nodes can be queried: mongos nodes in the cluster, and all nodes in the replica set and single node instances. |
      +------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------------------------------+

   .. table:: **Table 2** Query parameters

      +--------------+-----------+---------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter    | Mandatory | Type    | Description                                                                                                                                                                                                                                                                                                     |
      +==============+===========+=========+=================================================================================================================================================================================================================================================================================================================+
      | offset       | No        | Integer | Specifies the index position. If **offset** is set to *N*, the resource query starts from the N+1 piece of data. The value is **0** by default, indicating that the query starts from the first piece of data. The value cannot be a negative number.                                                           |
      +--------------+-----------+---------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | limit        | No        | Integer | Specifies the number of records to be queried. The value range is [1, 20]. The default value is **10**, indicating that 10 records are returned.                                                                                                                                                                |
      +--------------+-----------+---------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | plan_summary | No        | String  | Specifies the execution plan description. If this parameter is left empty, sessions in which **plan_summary** is empty are queried. You can also specify an execution plan, for example, **COLLSCAN IXSCAN FETCH SORT LIMIT SKIP COUNT COUNT_SCAN TEXT PROJECTION**                                             |
      +--------------+-----------+---------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | type         | No        | String  | Specifies the operation type. If this parameter is left empty, sessions in which **type** is empty are queried. You can also specify an operation type, for example, none update insert query command getmore remove killcursors.                                                                               |
      +--------------+-----------+---------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | namespace    | No        | String  | Specifies the namespace. If this parameter is left blank, the sessions in which **namespace** is empty are queried. You can also specify the value based on the service requirements.                                                                                                                           |
      +--------------+-----------+---------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | cost_time    | No        | Integer | Specifies the duration. The unit is us. If this parameter is left empty, the sessions in which **cost_time** is empty are queried. You can also set this parameter based on the service requirements, indicating that the sessions in which the value of **cost_time** exceeds the specified value are queried. |
      +--------------+-----------+---------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

-  Example request

   GET https://dds.eu-de.otc.t-systems.com/v3/054e292c9880d4992f02c0196d3ea468/nodes/520c58ba00a3497e97ce0b9604874dd6no02/sessions

Response Parameters
-------------------

-  Parameter description

   .. table:: **Table 3** Response body parameters

      +-------------+------------------+-------------------------------------------------------------------------------------------------------------------------------+
      | Parameter   | Type             | Description                                                                                                                   |
      +=============+==================+===============================================================================================================================+
      | total_count | Integer          | Indicates the total number of records.                                                                                        |
      +-------------+------------------+-------------------------------------------------------------------------------------------------------------------------------+
      | sessions    | Array of objects | Indicates detailed information. For details, see the :ref:`QuerySessionResponse <dds_connect_0002__table599818593239>` table. |
      +-------------+------------------+-------------------------------------------------------------------------------------------------------------------------------+

   .. _dds_connect_0002__table599818593239:

   .. table:: **Table 4** QuerySessionResponse

      +--------------+---------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter    | Type    | Description                                                                                                                                                    |
      +==============+=========+================================================================================================================================================================+
      | id           | String  | Indicates the session ID.                                                                                                                                      |
      +--------------+---------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | active       | Boolean | Indicates that whether the current session is active. If the value is **"true"**, the session is active. If the value is **"false"**, the session is inactive. |
      +--------------+---------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | operation    | String  | Indicates the operation.                                                                                                                                       |
      +--------------+---------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | type         | String  | Indicates the operation type.                                                                                                                                  |
      +--------------+---------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | cost_time    | String  | Specifies the duration. The unit is us.                                                                                                                        |
      +--------------+---------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | plan_summary | String  | Indicates the execution plan description.                                                                                                                      |
      +--------------+---------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | host         | String  | Indicates the host.                                                                                                                                            |
      +--------------+---------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | client       | String  | Indicates the client address.                                                                                                                                  |
      +--------------+---------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | description  | String  | Indicates the connection description.                                                                                                                          |
      +--------------+---------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | namespace    | String  | Indicates the namespace.                                                                                                                                       |
      +--------------+---------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Response example

   .. code-block:: text

      {
        "total_count" : 1,
        "sessions" : [ {
          "id" : "shard_1:7201646",
          "active" : true,
          "operation" : "{\"getMore\":4.9473050217983027E18,\"collection\":\"$cmd.aggregate\",\"batchSize\":101.0,\"lsid\":{\"id\":{\"$binary\":{\"base64\":\"9FhcBFVeTzafCH8BUZrLjQ\\=\\=\",\"subType\":\"03\"}},\"uid\":{\"$binary\":{\"base64\":\"O0CMtIVItQN4IsEOsJdrPL8s7jv5xwh5a/A5Qfvs2A8\\=\",\"subType\":\"00\"}}},\"$clusterTime\":{\"clusterTime\":{\"$timestamp\":{\"t\":1.614047961E9,\"i\":1.0}},\"signature\":{\"hash\":{\"$binary\":{\"base64\":\"HxUWu68VyfvQFivWjHQDdJj/3YQ\\=\",\"subType\":\"00\"}},\"keyId\":6.9312672235666801E18}},\"$client\":{\"driver\":{\"name\":\"PyMongo\",\"version\":\"3.6.1\"},\"os\":{\"type\":\"Linux\",\"name\":\"Linux\",\"architecture\":\"x86_64\",\"version\":\"4.18.0-147.5.1.0.h269.eulerosv2r9.x86_64\"},\"platform\":\"CPython 3.7.4.final.0\",\"mongos\":{\"host\":\"host-172-16-61-110:8635\",\"client\":\"127.0.0.1:33420\",\"version\":\"4.0.3\"}},\"$configServerState\":{\"opTime\":{\"ts\":{\"$timestamp\":{\"t\":1.614047961E9,\"i\":1.0}},\"t\":2.0}},\"$db\":\"admin\"}",
          "type" : "getmore",
          "cost_time" : "25",
          "plan_summary" : "COLLSCAN",
          "host" : "host-172-16-27-182:8635",
          "client" : "172.16.41.233:50700",
          "description" : "conn20",
          "namespace" : "admin.$cmd.aggregate"
        } ]
      }

Status Code
-----------

Status Code:200.

For more information, see :ref:`Status Code <dds_status_code>`.

Error Code
----------

For more information, see :ref:`Error Code <dds_error_code>`.
