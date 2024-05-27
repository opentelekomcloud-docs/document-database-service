:original_name: dds_api_0108.html

.. _dds_api_0108:

Obtaining Parameters of a Specified DB Instance
===============================================

Description
-----------

This API is used to obtain information about parameters of a specified DB instance.

Restrictions
------------

This API applies only to DDS Community Edition.

URI
---

-  URI format

   GET https://{Endpoint}/v3/{project_id}/instances/{instance_id}/configurations

Requests
--------

Parameter description

.. table:: **Table 1** Request parameters

   +--------------+--------+--------+-----------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Name         | Type   | IN     | Mandatory | Description                                                                                                                                                                             |
   +==============+========+========+===========+=========================================================================================================================================================================================+
   | x-auth-token | string | header | Yes       | User token.                                                                                                                                                                             |
   +--------------+--------+--------+-----------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Content-Type | string | header | Yes       | MIME type of the request body. You are advised to use the default value **application/json**. For APIs used to upload objects or images, the value can vary depending on the flow type. |
   +--------------+--------+--------+-----------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | project_id   | string | path   | Yes       | Specifies the project ID of a tenant in a region.                                                                                                                                       |
   +--------------+--------+--------+-----------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | instance_id  | string | path   | Yes       | Specifies the instance ID, which can be obtained by calling the API for querying instances. If you do not have an instance, you can call the API used for creating an instance.         |
   +--------------+--------+--------+-----------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 2** Query parameters

   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Type            | Mandatory       | Description                                                                                                                                                                                                  |
   +=================+=================+=================+==============================================================================================================================================================================================================+
   | entity_id       | String          | Yes             | -  Instance ID, group ID, or node ID. You can call the API used for querying instances and details to obtain the value. If you do not have an instance, you can call the API used for creating an instance.  |
   |                 |                 |                 | -  If the DB instance type is cluster and the shard or config parameter template is obtained, the value is the group ID. If the parameter template of the mongos node is obtained, the value is the node ID. |
   |                 |                 |                 | -  If the DB instance type is a replica set instance or a single node instance, the value is the instance ID.                                                                                                |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Responses
---------

-  Parameter description

   .. table:: **Table 3** Response body parameters

      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | Name                  | Type                  | Description                                                                                                        |
      +=======================+=======================+====================================================================================================================+
      | id                    | String                | Instance parameter configuration ID. This parameter can be used only for parameter comparison.                     |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | node_type             | String                | Node type of the parameter template.                                                                               |
      |                       |                       |                                                                                                                    |
      |                       |                       | -  **mongos**: the mongos node type.                                                                               |
      |                       |                       | -  **shard**: the shard node type.                                                                                 |
      |                       |                       | -  **config**: the config node type.                                                                               |
      |                       |                       | -  **replica**: the replica set type.                                                                              |
      |                       |                       | -  **single**: the single node type.                                                                               |
      |                       |                       | -  **readonly**: the read replica type.                                                                            |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | datastore_version     | String                | Database version.                                                                                                  |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | datastore_name        | String                | Database type.                                                                                                     |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | created               | String                | Creation time in the "yyyy-MM-ddTHH:mm:ssZ" format.                                                                |
      |                       |                       |                                                                                                                    |
      |                       |                       | **T** is the separator between the calendar and the hourly notation of time. **Z** indicates the time zone offset. |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | updated               | String                | Update time in the "yyyy-MM-ddTHH:mm:ssZ" format.                                                                  |
      |                       |                       |                                                                                                                    |
      |                       |                       | **T** is the separator between the calendar and the hourly notation of time. **Z** indicates the time zone offset. |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | parameters            | Array of objects      | Indicates the parameters defined by users based on the default parameter templates.                                |
      |                       |                       |                                                                                                                    |
      |                       |                       | For details, see :ref:`Table 4 <dds_api_0108__table5590121518481>`.                                                |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+

   .. _dds_api_0108__table5590121518481:

   .. table:: **Table 4** Data structure description of the parameters field

      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------+
      | Name                  | Type                  | Description                                                                                                                        |
      +=======================+=======================+====================================================================================================================================+
      | name                  | String                | The parameter name.                                                                                                                |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------+
      | value                 | String                | Parameter value.                                                                                                                   |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------+
      | value_range           | String                | The value range.                                                                                                                   |
      |                       |                       |                                                                                                                                    |
      |                       |                       | For example, the value of the Integer type ranges from **0** to **1**, and the value of the Boolean type is **true** or **false**. |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------+
      | restart_required      | Boolean               | Whether the instance needs to be restarted.                                                                                        |
      |                       |                       |                                                                                                                                    |
      |                       |                       | -  If the value is **true**, restart is required.                                                                                  |
      |                       |                       | -  If the value is **false**, restart is not required.                                                                             |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------+
      | readonly              | Boolean               | Whether the parameter group is read-only.                                                                                          |
      |                       |                       |                                                                                                                                    |
      |                       |                       | -  If the value **false**, the parameter is not read-only.                                                                         |
      |                       |                       | -  If the value is **true**, the parameter is read-only.                                                                           |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------+
      | type                  | String                | The parameter type. The value can be **integer**, **string**, **boolean**, **float**, or **list**.                                 |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------+
      | description           | String                | The parameter description.                                                                                                         |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------+

-  Response example

   .. code-block:: text

      {
          "id" : "5afa71df29ed4378bd7f6fef107daf6fin02",
          "node_type" : "replica",
          "datastore_version" : "4.0",
          "datastore_name" : "mongos",
          "created" : "2017-01-01T10:00:00",
          "updated" : "2017-01-01T10:00:00",
          "parameters" : [ {
            "name" : "cursorTimeoutMillis",
            "value" : "600000",
            "restart_required" : false,
            "readonly" : false,
            "description": "Specify the expiration time of idle cursors. DDS will delete idle cursors.",
            "value_range" : "600000-1000000"
          } ]
        }

Status Code
-----------

Status Code:200.

For more information, see :ref:`Status Code <dds_status_code>`.

Error Code
----------

For more information, see :ref:`Error Code <dds_error_code>`.
