:original_name: dds_api_0089.html

.. _dds_api_0089:

Obtaining Details About a Parameter Template
============================================

Description
-----------

This API is used to obtain parameter details of a specified parameter template.

Restrictions
------------

This API applies only to DDS Community Edition.

URI
---

-  URI format

   GET https://{Endpoint}/v3/{project_id}/configurations/{config_id}

.. table:: **Table 1** Request parameters

   +--------------+--------+-----------+---------------------------------------------------+
   | Name         | Type   | Mandatory | Description                                       |
   +==============+========+===========+===================================================+
   | x-auth-token | String | Yes       | User token.                                       |
   +--------------+--------+-----------+---------------------------------------------------+
   | project_id   | String | Yes       | Specifies the project ID of a tenant in a region. |
   +--------------+--------+-----------+---------------------------------------------------+
   | config_id    | String | Yes       | Parameter template ID.                            |
   +--------------+--------+-----------+---------------------------------------------------+

Requests
--------

None

Responses
---------

-  Parameter description

   .. table:: **Table 2** Response body parameters

      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | Name                  | Type                  | Description                                                                                                        |
      +=======================+=======================+====================================================================================================================+
      | id                    | String                | The parameter template ID.                                                                                         |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | name                  | String                | Parameter template name.                                                                                           |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | datastore_version     | String                | Database version.                                                                                                  |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | datastore_name        | String                | Database type.                                                                                                     |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | description           | String                | The parameter template description.                                                                                |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | created               | String                | Creation time in the "yyyy-MM-ddTHH:mm:ssZ" format.                                                                |
      |                       |                       |                                                                                                                    |
      |                       |                       | **T** is the separator between the calendar and the hourly notation of time. **Z** indicates the time zone offset. |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | updated               | String                | Update time in the "yyyy-MM-ddTHH:mm:ssZ" format.                                                                  |
      |                       |                       |                                                                                                                    |
      |                       |                       | **T** is the separator between the calendar and the hourly notation of time. **Z** indicates the time zone offset. |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+
      | parameters            | Array of objects      | The parameters defined by users based on the default parameter templates.                                          |
      |                       |                       |                                                                                                                    |
      |                       |                       | For details, see :ref:`Table 3 <dds_api_0089__table34207804>`.                                                     |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------+

   .. _dds_api_0089__table34207804:

   .. table:: **Table 3** Data structure description of the parameters field

      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------+
      | Name                  | Type                  | Description                                                                             |
      +=======================+=======================+=========================================================================================+
      | name                  | String                | The parameter name.                                                                     |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------+
      | value                 | String                | The parameter value.                                                                    |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------+
      | description           | String                | The parameter description.                                                              |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------+
      | type                  | String                | Parameter type.                                                                         |
      |                       |                       |                                                                                         |
      |                       |                       | The value can be **integer**, **string**, **boolean**, **float**, or **list**.          |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------+
      | value_range           | String                | Value range.                                                                            |
      |                       |                       |                                                                                         |
      |                       |                       | For example, the value of integer is 0 or 1, and the value of boolean is true or false. |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------+
      | restart_required      | Boolean               | Whether the instance needs to be restarted.                                             |
      |                       |                       |                                                                                         |
      |                       |                       | -  If the value is **true**, restart is required.                                       |
      |                       |                       | -  If the value is **false**, restart is not required.                                  |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------+
      | readonly              | Boolean               | Whether the parameter is read-only.                                                     |
      |                       |                       |                                                                                         |
      |                       |                       | -  If the value is **true**, the parameter is read-only.                                |
      |                       |                       | -  If the value **false**, the parameter is not read-only.                              |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------+

-  Response example

   .. code-block:: text

      {
        "id": "07fc12a8e0e94df7a3fcf53d0b5e1605pr01",
        "name": "paramsGroup-test",
        "description": "",
        "datastore_name": "mongodb",
        "datastore_version": "4.0",
        "created": "2017-01-01T10:00:00",
        "updated": "2017-01-01T10:00:00",
        "parameters": [
          {
            "name": "cursorTimeoutMillis",
            "type": "integer",
            "value": "600000",
            "description": "Specify the expiration time of idle cursors. DDS will delete idle cursors.",
            "value_range": "600000-1000000",
            "restart_required": false,
            "readonly": false
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
