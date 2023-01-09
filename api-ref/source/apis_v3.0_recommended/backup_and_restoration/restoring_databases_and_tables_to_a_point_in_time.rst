:original_name: dds_api_0084.html

.. _dds_api_0084:

Restoring Databases and Tables to a Point in Time
=================================================

Function
--------

This API is used to restore databases and tables at a point in time.

Constraints
-----------

This API applies only to replica sets.

URI
---

-  URI format

   POST https://{Endpoint}/v3/{project_id}/instances/{instance_id}/restore/collections

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

      +---------------------+-----------------+------------------+--------------------------------------------------------------------+
      | Name                | Mandatory       | Type             | Description                                                        |
      +=====================+=================+==================+====================================================================+
      | restore_collections | Yes             | Array of objects | Specifies the database information.                                |
      |                     |                 |                  |                                                                    |
      |                     |                 |                  | For details, see :ref:`Table 3 <dds_api_0084__table163715367507>`. |
      +---------------------+-----------------+------------------+--------------------------------------------------------------------+

   .. _dds_api_0084__table163715367507:

   .. table:: **Table 3** restore_collections data structure description

      +-----------------------+-----------------+------------------+-----------------------------------------------------------------------+
      | Name                  | Mandatory       | Type             | Description                                                           |
      +=======================+=================+==================+=======================================================================+
      | database              | Yes             | String           | Specifies the database name.                                          |
      +-----------------------+-----------------+------------------+-----------------------------------------------------------------------+
      | collections           | No              | Array of objects | Specifies the collection information.                                 |
      |                       |                 |                  |                                                                       |
      |                       |                 |                  | For details, see :ref:`Table 4 <dds_api_0084__table168109911>`.       |
      +-----------------------+-----------------+------------------+-----------------------------------------------------------------------+
      | restore_database_time | No              | String           | Specifies the database restoration time point.                        |
      |                       |                 |                  |                                                                       |
      |                       |                 |                  | This parameter is mandatory for database-level restoration,           |
      |                       |                 |                  |                                                                       |
      |                       |                 |                  | The value is a UNIX timestamp, in milliseconds. The time zone is UTC. |
      +-----------------------+-----------------+------------------+-----------------------------------------------------------------------+

   .. _dds_api_0084__table168109911:

   .. table:: **Table 4** collections data structure description

      +-------------------------+-----------------+-----------------+-----------------------------------------------------------------------+
      | Name                    | Mandatory       | Type            | Description                                                           |
      +=========================+=================+=================+=======================================================================+
      | old_name                | Yes             | String          | Specifies the original table name before the restoration.             |
      +-------------------------+-----------------+-----------------+-----------------------------------------------------------------------+
      | new_name                | No              | String          | Specifies the table name after the restoration.                       |
      +-------------------------+-----------------+-----------------+-----------------------------------------------------------------------+
      | restore_collection_time | Yes             | String          | Specifies the collection restoration time point.                      |
      |                         |                 |                 |                                                                       |
      |                         |                 |                 | The value is a UNIX timestamp, in milliseconds. The time zone is UTC. |
      +-------------------------+-----------------+-----------------+-----------------------------------------------------------------------+

-  Request example

   POST https://dds.eu-de.otc.t-systems.com/v3/056538411200d4cd2f79c003c7606412/instances/d5833c2854a4486cb7960f829269e211in02/restore/collections.

   -  Database-level restoration

      .. code-block:: text

         {
           "restore_collections": [
             {
               "database": "test",
               "restore_database_time": 1607762955000
             }
           ]
         }

   -  Collection-level restoration

      .. code-block:: text

         {
           "restore_collections": [
             {
               "database": "test",
               "collections": [
                 {
                   "old_name": "test",
                   "restore_collection_time": 1607762955000
                 }
               ]
             }
           ]
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

-  Abnormal Response

   For details, see :ref:`Abnormal Request Results <dds_api_0060>`.

Status Code
-----------

Status Code:200.

For more information, see :ref:`Status Code <dds_status_code>`.

Error Code
----------

For more information, see :ref:`Error Code <dds_error_code>`.
