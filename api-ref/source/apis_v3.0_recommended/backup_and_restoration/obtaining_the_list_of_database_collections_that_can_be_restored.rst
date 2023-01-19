:original_name: dds_api_0082.html

.. _dds_api_0082:

Obtaining the List of Database Collections That Can Be Restored
===============================================================

Function
--------

This API is used to obtain the list of databases collections that can be restored.

Constraints
-----------

This API applies only to replica sets.

URI
---

-  URI format

   GET https://{Endpoint}/v3/{project_id}/instances/{instance_id}/restore-collection?db_name={db_name}&restore_time={restore_time}&offset={offset}&limit={limit}

-  Parameter description

   .. table:: **Table 1** Parameter description

      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name                  | Mandatory             | Description                                                                                                                                                                     |
      +=======================+=======================+=================================================================================================================================================================================+
      | project_id            | Yes                   | Specifies the project ID of a tenant in a region.                                                                                                                               |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | instance_id           | Yes                   | Specifies the instance ID, which can be obtained by calling the API for querying instances. If you do not have an instance, you can call the API used for creating an instance. |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | db_name               | Yes                   | Specifies the database name.                                                                                                                                                    |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | restore_time          | Yes                   | Specifies the restoration time point.                                                                                                                                           |
      |                       |                       |                                                                                                                                                                                 |
      |                       |                       | The value is a UNIX timestamp, in milliseconds. The time zone is UTC.                                                                                                           |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | offset                | No                    | Specifies the index position.                                                                                                                                                   |
      |                       |                       |                                                                                                                                                                                 |
      |                       |                       | -  The value is an integer greater than or equal to 0.                                                                                                                          |
      |                       |                       | -  If this parameter is not transferred, the value is **0** by default.                                                                                                         |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | limit                 | No                    | Specifies the upper limit of the number of queried records.                                                                                                                     |
      |                       |                       |                                                                                                                                                                                 |
      |                       |                       | -  The value ranges from 1 to 100.                                                                                                                                              |
      |                       |                       | -  If this parameter is not transferred, the first 100 records are queried by default.                                                                                          |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Requests
--------

-  Example request

   Get https://dds.eu-de.otc.t-systems.com/v3/056538411200d4cd2f79c003c7606412/instances/d5833c2854a4486cb7960f829269e211in02/restore-collection?db_name=mydbx&restore_time=1607689584000&limit=10&offset=0

Responses
---------

-  Parameter description

   .. table:: **Table 2** Parameter description

      +-------------+------------------+-------------------------------------------------------------------------------------+
      | Name        | Type             | Description                                                                         |
      +=============+==================+=====================================================================================+
      | collections | Array of objects | Indicates the list of collections. Each element in the list indicates a collection. |
      +-------------+------------------+-------------------------------------------------------------------------------------+
      | total_count | Integer          | Indicates the total number of collections.                                          |
      +-------------+------------------+-------------------------------------------------------------------------------------+

   .. table:: **Table 3** Parameter description

      ==== ====== ==============================
      Name Type   Description
      ==== ====== ==============================
      name String Indicates the collection name.
      ==== ====== ==============================

-  Response example

   .. code-block:: text

      {
        "collections": [
          "dds-test"
        ],
        "total_count": 1
      }

Status Code
-----------

Status Code:200.

For more information, see :ref:`Status Code <dds_status_code>`.

Error Code
----------

For more information, see :ref:`Error Code <dds_error_code>`.
