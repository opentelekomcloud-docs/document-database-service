:original_name: dds_api_0083.html

.. _dds_api_0083:

Restoring Data to the Original DB Instance
==========================================

Function
--------

This API is used to restore data to the original DB instance.

URI
---

-  URI format

   POST https://{Endpoint}/v3/{project_id}/instances/recovery

-  Parameter description

   .. table:: **Table 1** Parameter description

      ========== ========= =================================================
      Name       Mandatory Description
      ========== ========= =================================================
      project_id Yes       Specifies the project ID of a tenant in a region.
      ========== ========= =================================================

Requests
--------

-  Parameter description

   .. table:: **Table 2** Parameter description

      +-----------------+-----------------+-----------------+--------------------------------------------------------------------+
      | Name            | Mandatory       | Type            | Description                                                        |
      +=================+=================+=================+====================================================================+
      | source          | Yes             | Object          | Specifies the instance from which the backup was created           |
      |                 |                 |                 |                                                                    |
      |                 |                 |                 | For details, see :ref:`Table 3 <dds_api_0083__table163715367507>`. |
      +-----------------+-----------------+-----------------+--------------------------------------------------------------------+
      | target          | Yes             | Object          | Specifies the instance to which the backup is restored.            |
      |                 |                 |                 |                                                                    |
      |                 |                 |                 | For details, see :ref:`Table 4 <dds_api_0083__table168109911>`.    |
      +-----------------+-----------------+-----------------+--------------------------------------------------------------------+

   .. _dds_api_0083__table163715367507:

   .. table:: **Table 3** source field data structure description

      +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name            | Mandatory       | Type            | Description                                                                                                                                                                     |
      +=================+=================+=================+=================================================================================================================================================================================+
      | instance_id     | Yes             | String          | Specifies the instance ID, which can be obtained by calling the API for querying instances. If you do not have an instance, you can call the API used for creating an instance. |
      +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | type            | No              | String          | Specifies the restoration mode. Enumerated values include:                                                                                                                      |
      |                 |                 |                 |                                                                                                                                                                                 |
      |                 |                 |                 | -  **backup**: indicates using backup files for restoration. In this mode, **type** is optional and **backup_id** is mandatory.                                                 |
      |                 |                 |                 | -  **timestamp**: indicates the point-in-time restoration mode. In this mode, **type** is mandatory and **restore_time** is mandatory.                                          |
      +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | backup_id       | No              | String          | Specifies the ID of the backup to be restored. This parameter must be specified when the backup file is used for restoration.                                                   |
      +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | restore_time    | No              | String          | Specifies the time point of data restoration in the UNIX timestamp. The unit is millisecond and the time zone is UTC.                                                           |
      |                 |                 |                 |                                                                                                                                                                                 |
      |                 |                 |                 | .. note::                                                                                                                                                                       |
      |                 |                 |                 |                                                                                                                                                                                 |
      |                 |                 |                 |    This parameter takes effect only for replica set instances.                                                                                                                  |
      +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. _dds_api_0083__table168109911:

   .. table:: **Table 4** target field data structure description

      +-------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name        | Mandatory | Type   | Description                                                                                                                                                                                                                    |
      +=============+===========+========+================================================================================================================================================================================================================================+
      | instance_id | Yes       | String | Specifies ID of the DB instance to be restored from a backup. You can call the API for querying DB Instances to obtain the DB instance ID. If you do not have an instance, you can call the API used for creating an instance. |
      +-------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Request example

   POST https://dds.eu-de.otc.t-systems.com/v3/056538411200d4cd2f79c003c7606412/instances/recovery

   -  Restoring a backup:

      .. code-block:: text

         {
           "source": {
             "instance_id": "d8e6ca5a624745bcb546a227aa3ae1cfin02",
             "type": "backup",
             "backup_id": "2f4ddb93-b901-4b08-93d8-1d2e472f30fe"
           },
           "target": {
             "instance_id": "d8e6ca5a624745bcb546a227aa3ae1cfin02"
           }
         }

   -  Restoring to a point in time (applicable to replica set instances and cluster instances 4.0)

      .. code-block:: text

         {
           "source": {
             "instance_id": "d8e6ca5a624745bcb546a227aa3ae1cfin02",
             "type": "timestamp",
             "restore_time": 1532001446987
           },
           "target": {
             "instance_id": "d8e6ca5a624745bcb546a227aa3ae1cfin02"
           }
         }

Responses
---------

-  Parameter description

   .. table:: **Table 5** Parameter description

      ====== ====== ======================================================
      Name   Type   Description
      ====== ====== ======================================================
      job_id String ID of the asynchronous task for the restore operation.
      ====== ====== ======================================================

-  Response example

   .. code-block:: text

      {
          "job_id": "a03b1b8a-b756-467c-8a49-38720c3d23ec"
      }

Status Code
-----------

Status Code:200.

For more information, see :ref:`Status Code <dds_status_code>`.

Error Code
----------

For more information, see :ref:`Error Code <dds_error_code>`.
