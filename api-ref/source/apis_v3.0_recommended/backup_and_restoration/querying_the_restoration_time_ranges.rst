:original_name: dds_api_0080.html

.. _dds_api_0080:

Querying the Restoration Time Ranges
====================================

Function
--------

This API is used to query the restoration time range of a DB instance.

Constraints
-----------

Currently, this API only supports replica set instances and cluster instances 4.0.

URI
---

-  URI format

   GET https://{Endpoint}/v3/{project_id}/instances/{instance_id}/restore-time?date={yyyy-mm-dd}

-  Parameter description

   .. table:: **Table 1** Parameter description

      +-------------+-----------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name        | Mandatory | Description                                                                                                                                                                     |
      +=============+===========+=================================================================================================================================================================================+
      | project_id  | Yes       | Specifies the project ID of a tenant in a region.                                                                                                                               |
      +-------------+-----------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | instance_id | Yes       | Specifies the instance ID, which can be obtained by calling the API for querying instances. If you do not have an instance, you can call the API used for creating an instance. |
      +-------------+-----------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | date        | Yes       | Specifies the date to be queried in UTC time zone. The value is in the yyyy-mm-dd format.                                                                                       |
      +-------------+-----------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Requests
--------

-  Example request

   Get https://dds.eu-de.otc.t-systems.com/v3/056538411200d4cd2f79c003c7606412/instances/d5833c2854a4486cb7960f829269e211in02/restore-time?date=2020-12-12

Responses
---------

-  Parameter description

   .. table:: **Table 2** Parameter description

      +--------------+------------------+-------------------------------------------------------------------------------------------------------------+
      | Name         | Type             | Description                                                                                                 |
      +==============+==================+=============================================================================================================+
      | restore_time | Array of objects | Indicates the restoration time ranges. For details, see :ref:`Table 3 <dds_api_0080__table15985133144213>`. |
      +--------------+------------------+-------------------------------------------------------------------------------------------------------------+

   .. _dds_api_0080__table15985133144213:

   .. table:: **Table 3** restore_time parameters

      +------------+------+----------------------------------------------------------------------------------------------------------------------------------------+
      | Name       | Type | Description                                                                                                                            |
      +============+======+========================================================================================================================================+
      | start_time | Long | Indicates the start time of the restoration time range in the UNIX timestamp format. The unit is millisecond and the time zone is UTC. |
      +------------+------+----------------------------------------------------------------------------------------------------------------------------------------+
      | end_time   | Long | Indicates the end time of the restoration time range in the UNIX timestamp format. The unit is millisecond and the time zone is UTC.   |
      +------------+------+----------------------------------------------------------------------------------------------------------------------------------------+

-  Response example

   .. code-block:: text

      {
        "restore_time": [
          {
            "start_time": 1607731200000,
            "end_time": 1607756414000
          },
          {
            "start_time": 1607756825000,
            "end_time": 1607761999000
          },
          {
            "start_time": 1607762943000,
            "end_time": 1607817599000
          }
        ]
      }

Status Code
-----------

Status Code:200.

For more information, see :ref:`Status Code <dds_status_code>`.

Error Code
----------

For more information, see :ref:`Error Code <dds_error_code>`.
