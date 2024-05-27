:original_name: dds_api_0088.html

.. _dds_api_0088:

Obtaining Parameter Templates
=============================

Description
-----------

This API is used to obtain parameter templates, including all databases' default parameter templates and user-created parameter templates.

Restrictions
------------

This API applies only to DDS Community Edition.

URI
---

-  URI format

   GET https://{Endpoint}/v3/{project_id}/configurations

.. table:: **Table 1** Request parameters

   +--------------+--------+-----------+---------------------------------------------------+
   | Name         | Type   | Mandatory | Description                                       |
   +==============+========+===========+===================================================+
   | x-auth-token | String | Yes       | User token.                                       |
   +--------------+--------+-----------+---------------------------------------------------+
   | project_id   | String | Yes       | Specifies the project ID of a tenant in a region. |
   +--------------+--------+-----------+---------------------------------------------------+

.. table:: **Table 2** Query parameters

   +-----------+---------+-----------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Type    | Mandatory | Description                                                                                                                                                                                                                                 |
   +===========+=========+===========+=============================================================================================================================================================================================================================================+
   | offset    | Integer | No        | The index position. If **offset** is set to *N*, the resource query starts from the N+1 piece of data. The value is **0** by default, indicating that the query starts from the first piece of data. The value cannot be a negative number. |
   +-----------+---------+-----------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | limit     | Integer | No        | Number of records displayed on each page. The default value is 100.                                                                                                                                                                         |
   +-----------+---------+-----------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Requests
--------

None

Responses
---------

-  Parameter description

   .. table:: **Table 3** Response body parameters

      +----------------+------------------+------------------------------------------------------------------------------------------------+
      | Name           | Type             | Description                                                                                    |
      +================+==================+================================================================================================+
      | total_count    | Integer          | The total number of queried records.                                                           |
      +----------------+------------------+------------------------------------------------------------------------------------------------+
      | quota          | Integer          | Maximum number of custom parameter templates that can be created.                              |
      +----------------+------------------+------------------------------------------------------------------------------------------------+
      | configurations | Array of objects | The parameter template list. For details, see :ref:`Table 4 <dds_api_0088__table11320215139>`. |
      +----------------+------------------+------------------------------------------------------------------------------------------------+

   .. _dds_api_0088__table11320215139:

   .. table:: **Table 4** Data structure description of the configurations field

      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | Parameter             | Type                  | Description                                                                                                        |
      +=======================+=======================+====================================================================================================================+
      | id                    | String                | Parameter template ID.                                                                                             |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | name                  | String                | Parameter template name.                                                                                           |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | description           | String                | Parameter template description.                                                                                    |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | datastore_version     | String                | Database version.                                                                                                  |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | datastore_name        | String                | Database type.                                                                                                     |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | node_type             | String                | Node type of the parameter template.                                                                               |
      |                       |                       |                                                                                                                    |
      |                       |                       | -  **mongos**: the mongos node type.                                                                               |
      |                       |                       | -  **shard**: the shard node type.                                                                                 |
      |                       |                       | -  **config**: the config node type.                                                                               |
      |                       |                       | -  **replica**: the replica set type.                                                                              |
      |                       |                       | -  **single** the single node type.                                                                                |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | created               | String                | Creation time in the "yyyy-MM-ddTHH:mm:ssZ" format.                                                                |
      |                       |                       |                                                                                                                    |
      |                       |                       | **T** is the separator between the calendar and the hourly notation of time. **Z** indicates the time zone offset. |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | updated               | String                | Update time in the "yyyy-MM-ddTHH:mm:ssZ" format.                                                                  |
      |                       |                       |                                                                                                                    |
      |                       |                       | **T** is the separator between the calendar and the hourly notation of time. **Z** indicates the time zone offset. |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | user_defined          | Boolean               | Indicates whether the parameter template is created by users.                                                      |
      |                       |                       |                                                                                                                    |
      |                       |                       | -  **false**: The parameter template is a default parameter template.                                              |
      |                       |                       | -  **true**: The parameter template is a custom template.                                                          |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+

-  Response example

   .. code-block:: text

      {
        "total_count" : 1,
        "quota" : 100,
        "configurations" : [ {
          "id" : "07fc12a8e0e94df7a3fcf53d0b5e1605pr01",
          "name" : "test1",
          "description" : "",
          "datastore_name" : "mongos",
          "node_type":"shard",
          "datastore_version" : "4.0",
          "created" : "2017-01-01T10:00:00",
          "updated" : "2017-01-01T10:00:00",
          "user_defined" : true
        } ]
      }

Status Code
-----------

Status Code:200.

For more information, see :ref:`Status Code <dds_status_code>`.

Error Code
----------

For more information, see :ref:`Error Code <dds_error_code>`.
