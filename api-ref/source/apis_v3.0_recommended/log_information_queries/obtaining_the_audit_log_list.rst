:original_name: dds_api_0099.html

.. _dds_api_0099:

Obtaining the Audit Log List
============================

Function
--------

This API is used to obtain an audit log list.

URI
---

-  URI format

   GET https://{Endpoint}/v3/{project_id}/instances/{instance_id}/auditlog?start_time={start_time}&end_time={end_time}&offset={offset}&limit={limit}

-  Parameter description

   .. table:: **Table 1** Parameter description

      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name                  | Mandatory             | Description                                                                                                                                                                                                             |
      +=======================+=======================+=========================================================================================================================================================================================================================+
      | project_id            | Yes                   | Specifies the project ID of a tenant in a region.                                                                                                                                                                       |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | instance_id           | Yes                   | Specifies the instance ID, which can be obtained by calling the API for querying instances. If you do not have an instance, you can call the API used for creating an instance.                                         |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | node_id               | No                    | Specifies the ID of the node whose audit logs are to be queried.                                                                                                                                                        |
      |                       |                       |                                                                                                                                                                                                                         |
      |                       |                       | If this parameter is not transferred, the audit logs of all nodes are queried by default. The audit logs of cluster instances are distributed on mongos nodes.                                                          |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | start_time            | Yes                   | Specifies the start time. The format of the start time is "yyyy-mm-ddThh:mm:ssZ".                                                                                                                                       |
      |                       |                       |                                                                                                                                                                                                                         |
      |                       |                       | **T** is the separator between the calendar and the hourly notation of time. **Z** indicates the time zone offset.                                                                                                      |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | end_time              | Yes                   | Specifies the end time. The format of the end time is "yyyy-mm-ddThh:mm:ssZ" and the end time must be later than the start time. The time span cannot be longer than 30 days.                                           |
      |                       |                       |                                                                                                                                                                                                                         |
      |                       |                       | **T** is the separator between the calendar and the hourly notation of time. **Z** indicates the time zone offset.                                                                                                      |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | offset                | No                    | Specifies the index position.                                                                                                                                                                                           |
      |                       |                       |                                                                                                                                                                                                                         |
      |                       |                       | If **offset** is set to *N*, the resource query starts from the N+1 piece of data. The value is **0** by default, indicating that the query starts from the first piece of data. The value cannot be a negative number. |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | limit                 | No                    | Specifies the number of records to be queried.                                                                                                                                                                          |
      |                       |                       |                                                                                                                                                                                                                         |
      |                       |                       | -  The value ranges from 1 to 100.                                                                                                                                                                                      |
      |                       |                       | -  If this parameter is not transferred, the first 100 DB instances are queried by default.                                                                                                                             |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Requests
--------

-  Example request

   GET https://dds.eu-de.otc.t-systems.com/v3/056538411200d4cd2f79c003c7606412/instances/65d3fe0c50984b35bc1a36e9b7c7de98in02/auditlog?start_time=2020-12-06T09:00:00+0800&end_time=2020-12-10T18:00:15+0800&offset=0&limit=33

Responses
---------

-  Parameter description

   .. table:: **Table 2** Parameter description

      +--------------+------------------+------------------------------------------------------------------------------------------------------------------------+
      | Name         | Type             | Description                                                                                                            |
      +==============+==================+========================================================================================================================+
      | audit_logs   | Array of objects | Indicates the audit log details. For details about audit logs, see :ref:`Table 3 <dds_api_0099__table15702194615294>`. |
      +--------------+------------------+------------------------------------------------------------------------------------------------------------------------+
      | total_record | Integer          | Indicates the total number of records.                                                                                 |
      +--------------+------------------+------------------------------------------------------------------------------------------------------------------------+

   .. _dds_api_0099__table15702194615294:

   .. table:: **Table 3** audit_logs parameters

      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | Name                  | Type                  | Description                                                                                                        |
      +=======================+=======================+====================================================================================================================+
      | node_id               | String                | Indicates the node ID.                                                                                             |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | id                    | String                | Indicates the audit log ID.                                                                                        |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | name                  | String                | Indicates the audit log file name.                                                                                 |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | size                  | Long                  | Indicates the size of the audit log in byte.                                                                       |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | start_time            | String                | Indicates the start time of the audit log. The format is "yyyy-mm-ddThh:mm:ssZ".                                   |
      |                       |                       |                                                                                                                    |
      |                       |                       | **T** is the separator between the calendar and the hourly notation of time. **Z** indicates the time zone offset. |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | end_time              | String                | Indicates the end time of the audit log. The format is "yyyy-mm-ddThh:mm:ssZ".                                     |
      |                       |                       |                                                                                                                    |
      |                       |                       | **T** is the separator between the calendar and the hourly notation of time. **Z** indicates the time zone offset. |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+

-  Response example

   .. code-block:: text

      {
        "audit_logs": [
          {
            "id": "10190012aae94b38a10269b8ad025fc1no02_1607681849871",
            "name": "0a84b6e97780d3271fd0c00f2db42932_audit_log_65d3fe0c50984b35bc1a36e9b7c7de98in02_10190012aae94b38a10269b8ad025fc1no02_1607681849871",
            "size": 24735174,
            "node_id": "10190012aae94b38a10269b8ad025fc1no02",
            "start_time": "2020-12-11T18:14:49+0800",
            "end_time": "2020-12-11T18:17:25+0800"
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
