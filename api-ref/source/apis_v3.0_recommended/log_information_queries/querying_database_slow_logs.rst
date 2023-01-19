:original_name: dds_api_0093.html

.. _dds_api_0093:

Querying Database Slow Logs
===========================

Function
--------

This API is used to query database slow logs.

Constraints
-----------

A maximum of 2000 records can be queried within the period specified by **start_date** and **end_date**.

URI
---

-  URI format

   GET https://{Endpoint}/v3/{project_id}/instances/{instance_id}/slowlog?offset={offset}&limit={limit}&start_date={start_date}&end_date={end_date}&type={type}&node_id={node_id}

-  Parameter description

   .. table:: **Table 1** Parameter description

      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name                  | Mandatory             | Description                                                                                                                                                                                                             |
      +=======================+=======================+=========================================================================================================================================================================================================================+
      | project_id            | Yes                   | Specifies the project ID of a tenant in a region.                                                                                                                                                                       |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | instance_id           | Yes                   | Specifies the instance ID, which can be obtained by calling the API for querying instances. If you do not have an instance, you can call the API used for creating an instance.                                         |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | start_date            | Yes                   | Specifies the start time in the "yyyy-mm-ddThh:mm:ssZ" format.                                                                                                                                                          |
      |                       |                       |                                                                                                                                                                                                                         |
      |                       |                       | **T** is the separator between the calendar and the hourly notation of time. **Z** indicates the time zone offset.                                                                                                      |
      |                       |                       |                                                                                                                                                                                                                         |
      |                       |                       | .. caution::                                                                                                                                                                                                            |
      |                       |                       |                                                                                                                                                                                                                         |
      |                       |                       |    CAUTION:                                                                                                                                                                                                             |
      |                       |                       |    The start time is 31 days earlier than the current time.                                                                                                                                                             |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | end_date              | Yes                   | Specifies the end time in the "yyyy-mm-ddThh:mm:ssZ" format.                                                                                                                                                            |
      |                       |                       |                                                                                                                                                                                                                         |
      |                       |                       | **T** is the separator between the calendar and the hourly notation of time. **Z** indicates the time zone offset.                                                                                                      |
      |                       |                       |                                                                                                                                                                                                                         |
      |                       |                       | Only slow query logs generated within the last month can be queried.                                                                                                                                                    |
      |                       |                       |                                                                                                                                                                                                                         |
      |                       |                       | .. note::                                                                                                                                                                                                               |
      |                       |                       |                                                                                                                                                                                                                         |
      |                       |                       |    The end time cannot be later than the current time.                                                                                                                                                                  |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | node_id               | No                    | Specifies the node ID. For details, see :ref:`Table 8 <dds_api_0023__table3426155424213>`.                                                                                                                              |
      |                       |                       |                                                                                                                                                                                                                         |
      |                       |                       | If this parameter is left blank, all nodes in the instance can be queried.                                                                                                                                              |
      |                       |                       |                                                                                                                                                                                                                         |
      |                       |                       | Nodes that can be queried:                                                                                                                                                                                              |
      |                       |                       |                                                                                                                                                                                                                         |
      |                       |                       | Shard nodes in a cluster instance.                                                                                                                                                                                      |
      |                       |                       |                                                                                                                                                                                                                         |
      |                       |                       | All nodes in a replica set or single node instance.                                                                                                                                                                     |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | type                  | No                    | Specifies the statement type. If it is left blank, all statement types are queried. Valid value:                                                                                                                        |
      |                       |                       |                                                                                                                                                                                                                         |
      |                       |                       | -  INSERT                                                                                                                                                                                                               |
      |                       |                       | -  QUERY                                                                                                                                                                                                                |
      |                       |                       | -  UPDATE                                                                                                                                                                                                               |
      |                       |                       | -  REMOVE                                                                                                                                                                                                               |
      |                       |                       | -  GETMORE                                                                                                                                                                                                              |
      |                       |                       | -  COMMAND                                                                                                                                                                                                              |
      |                       |                       | -  KILLCURSORS                                                                                                                                                                                                          |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | offset                | No                    | Specifies the index position. Its value range is **[0, 1999]**.                                                                                                                                                         |
      |                       |                       |                                                                                                                                                                                                                         |
      |                       |                       | If **offset** is set to *N*, the resource query starts from the N+1 piece of data. The value is **0** by default, indicating that the query starts from the first piece of data. The value cannot be a negative number. |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | limit                 | No                    | Specifies the number of resources to be queried. The value ranges from 1 to 100. The default value is **10**, indicating that 10 records are returned by default.                                                       |
      |                       |                       |                                                                                                                                                                                                                         |
      |                       |                       | .. note::                                                                                                                                                                                                               |
      |                       |                       |                                                                                                                                                                                                                         |
      |                       |                       |    The sum of **limit** and **offset** values must be less than or equal to 2000.                                                                                                                                       |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Requests
--------

-  Example request

   GET https://dds.eu-de.otc.t-systems.com/v3/0483b6b16e954cb88930a360d2c4e663/instances/6ade8143870047b8999aba8f1891b48ein02/slowlog?start_date=2018-08-06T10:41:14+0800&end_date=2018-08-07T10:41:14+0800

Responses
---------

-  Parameter description

   .. table:: **Table 2** Parameter description

      +-----------------------+-----------------------+---------------------------------------------------------------------+
      | Name                  | Type                  | Description                                                         |
      +=======================+=======================+=====================================================================+
      | slow_log_list         | Array of objects      | Indicates detailed information.                                     |
      |                       |                       |                                                                     |
      |                       |                       | For details, see :ref:`Table 3 <dds_api_0093__table1246710557414>`. |
      +-----------------------+-----------------------+---------------------------------------------------------------------+
      | total_record          | Integer               | Indicates the total number of records.                              |
      +-----------------------+-----------------------+---------------------------------------------------------------------+

   .. _dds_api_0093__table1246710557414:

   .. table:: **Table 3** slow_log_list field data structure description

      +---------------+--------+-------------------------------------------------------+
      | Name          | Type   | Description                                           |
      +===============+========+=======================================================+
      | node_name     | String | Indicates the node name.                              |
      +---------------+--------+-------------------------------------------------------+
      | query_sample  | String | Indicates the execution syntax.                       |
      +---------------+--------+-------------------------------------------------------+
      | type          | String | Indicates the statement type.                         |
      +---------------+--------+-------------------------------------------------------+
      | time          | String | Indicates the execution time.                         |
      +---------------+--------+-------------------------------------------------------+
      | lock_time     | String | Indicates the lock wait time.                         |
      +---------------+--------+-------------------------------------------------------+
      | rows_sent     | String | Indicates the number of sent rows.                    |
      +---------------+--------+-------------------------------------------------------+
      | rows_examined | String | Indicates the number of scanned rows.                 |
      +---------------+--------+-------------------------------------------------------+
      | database      | String | Indicates the database which the slow log belongs to. |
      +---------------+--------+-------------------------------------------------------+
      | start_time    | String | Indicates the time in the UTC format.                 |
      +---------------+--------+-------------------------------------------------------+

-  Response example

   .. code-block:: text

      {
        "slow_log_list": [
          {
            "node_name": "Test_replica_node_2",
            "query_sample": "{\"responseLength\": 230, \"ts\": {\"$date\": 1605480486800}, \"ninserted\": 1, \"locks\": {\"oplog\": {\"acquireCount\": {\"w\": 1}}, \"Global\": {\"acquireCount\": {\"r\": 3, \"w\": 2}}, \"Collection\": {\"acquireCount\": {\"w\": 2}}, \"Database\": {\"acquireCount\": {\"w\": 3}}}, \"numYield\": 0, \"ns\": \"geographySpace.tiles\"}",
            "type": "REMOVE",
            "time": "101 ms",
            "lock_time": "10 us",
            "rows_sent": "0",
            "rows_examined": "0",
            "database": "geography",
            "start_time": "2020-11-15T22:49:38.643000Z"
          }
        ],
        "total_record": 1
      }

Status Code
-----------

Status Code:200.

For more information, see :ref:`Status Code <dds_status_code>`.

Error Code
----------

For more information, see :ref:`Error Code <dds_error_code>`.
