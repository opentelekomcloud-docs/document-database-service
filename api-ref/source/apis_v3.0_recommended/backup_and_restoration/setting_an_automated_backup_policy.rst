:original_name: dds_api_0031.html

.. _dds_api_0031:

Setting an Automated Backup Policy
==================================

Function
--------

This API is used to set an automated backup policy.

URI
---

-  URI format

   PUT https://{Endpoint}/v3/{project_id}/instances/{instance_id}/backups/policy

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

      +---------------+-----------+--------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name          | Mandatory | Type   | Description                                                                                                                                                                  |
      +===============+===========+========+==============================================================================================================================================================================+
      | backup_policy | Yes       | Object | Specifies the backup policy object, including the backup retention period (days) and start time. For more information, see :ref:`Table 3 <dds_api_0031__table163715367507>`. |
      +---------------+-----------+--------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. _dds_api_0031__table163715367507:

   .. table:: **Table 3** backup_policy field data structure description

      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name            | Mandatory       | Type            | Description                                                                                                                                                                                                                                               |
      +=================+=================+=================+===========================================================================================================================================================================================================================================================+
      | keep_days       | Yes             | String          | Specifies the number of days to retain the generated backup files.                                                                                                                                                                                        |
      |                 |                 |                 |                                                                                                                                                                                                                                                           |
      |                 |                 |                 | The value range is from 0 to 732. The value **0** indicates that the automated backup policy is disabled.                                                                                                                                                 |
      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | start_time      | No              | String          | Specifies the backup time window. Automated backups will be triggered during the backup time window. This parameter is mandatory if the automated backup policy is enabled. This parameter is not transferred if the automated backup policy is disabled. |
      |                 |                 |                 |                                                                                                                                                                                                                                                           |
      |                 |                 |                 | The value must be a valid value in the "hh:mm-HH:MM" format. The current time is in the UTC format.                                                                                                                                                       |
      |                 |                 |                 |                                                                                                                                                                                                                                                           |
      |                 |                 |                 | -  The **HH** value must be 1 greater than the **hh** value.                                                                                                                                                                                              |
      |                 |                 |                 | -  The values of **mm** and **MM** must be the same and must be set to **00**.                                                                                                                                                                            |
      |                 |                 |                 |                                                                                                                                                                                                                                                           |
      |                 |                 |                 | Example value:                                                                                                                                                                                                                                            |
      |                 |                 |                 |                                                                                                                                                                                                                                                           |
      |                 |                 |                 | 23:00-00:00                                                                                                                                                                                                                                               |
      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | period          | No              | String          | Specifies the backup cycle configuration. Data will be automatically backed up on the selected days every week.                                                                                                                                           |
      |                 |                 |                 |                                                                                                                                                                                                                                                           |
      |                 |                 |                 | Value range: The value is a number separated by DBS case commas (,). The number indicates the week. The restrictions on the backup retention period are as follows:                                                                                       |
      |                 |                 |                 |                                                                                                                                                                                                                                                           |
      |                 |                 |                 | -  This parameter is not transferred if its value is set to **0**.                                                                                                                                                                                        |
      |                 |                 |                 | -  If you set the retention period to 1 to 6 days, data is automatically backed up each day of the week. Set the parameter value to **1,2,3,4,5,6,7**.                                                                                                    |
      |                 |                 |                 | -  If you set the retention period to 7 to 732 days, select at least one day of the week for the backup cycle. Example value: **1,2,3,4**                                                                                                                 |
      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Example request

   PUT https://dds.eu-de.otc.t-systems.com/v3/97b026aa9cc4417888c14c84a1ad9860/instances/cc6345c64cec47499182467ea0dd432ain02/backups/policy

   .. code-block:: text

      {
          "backup_policy": {
              "keep_days": 9,
              "start_time": "23:00-00:00",
              "period": "1,4,5,6,7"
          }
      }

   Disable an automated backup policy.

   .. code-block:: text

      {
          "backup_policy": {
              "keep_days": 0
          }
      }

Responses
---------

.. code-block:: text

   {}

Status Code
-----------

Status Code:200.

For more information, see :ref:`Status Code <dds_status_code>`.

Error Code
----------

For more information, see :ref:`Error Code <dds_error_code>`.
