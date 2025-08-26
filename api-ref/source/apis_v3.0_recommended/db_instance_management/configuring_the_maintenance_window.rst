:original_name: dds_api_023.html

.. _dds_api_023:

Configuring the Maintenance Window
==================================

API Description
---------------

This API is used to modify the time range within which you are allowed to start a task that affects the running of database instances, for example, the time window for upgrading the operating system and database software.

URI
---

-  URI format

   PUT https://{Endpoint}/v3/{project_id}/instances/{instance_id}/maintenance-window

   .. table:: **Table 1** Path parameters

      +-------------+-----------+--------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name        | Mandatory | Type   | Description                                                                                                                                                                                                                                    |
      +=============+===========+========+================================================================================================================================================================================================================================================+
      | project_id  | Yes       | String | Project ID of a tenant in a region. To obtain the project ID, see :ref:`Obtaining a Project ID <dds_projectid>`.                                                                                                                               |
      +-------------+-----------+--------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | instance_id | Yes       | String | Instance ID, which can be obtained by calling the API described in :ref:`Querying Instances and Details <dds_api_0023>`. If you do not have an instance, call the API described in :ref:`Creating a DB Instance <dds_api_0020>` to create one. |
      +-------------+-----------+--------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Requests
--------

-  Parameter description

   .. table:: **Table 2** Request header parameters

      +--------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name         | Mandatory | Type   | Description                                                                                                                                                                                           |
      +==============+===========+========+=======================================================================================================================================================================================================+
      | Content-Type | Yes       | String | Specifies the MIME type of the request body. You are advised to use the default value **application/json**. For APIs used to upload objects or images, the value can vary depending on the flow type. |
      +--------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | X-Auth-Token | Yes       | String | User token obtained from IAM. For details, see :ref:`Authentication <dds_api_0010>`.                                                                                                                  |
      +--------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. table:: **Table 3** Request body parameters

      +------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name       | Mandatory | Type   | Description                                                                                                                                                                                                     |
      +============+===========+========+=================================================================================================================================================================================================================+
      | start_time | Yes       | String | Start time. The value must be a valid value in the "HH:MM" format. The current time is the UTC time. The value cannot be the same as the end time. Gap between "start_time" and "end_time" must be at least 1h. |
      +------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | end_time   | Yes       | String | End time. The value must be a valid value in the "HH:MM" format. The current time is the UTC time. The value cannot be the same as the start time. Gap between "start_time" and "end_time" must be at least 1h. |
      +------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Example request

   Configuring the maintenance window

   .. code-block::

      {
        "start_time" : "14:00",
        "end_time" : "15:00"
      }

Responses
---------

None

Status Code
-----------

Status Code:200.

For more information, see :ref:`Status Code <dds_status_code>`.

Error Code
----------

For details, see :ref:`Error Code <dds_error_code>`.
