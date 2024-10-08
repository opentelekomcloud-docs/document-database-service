:original_name: dds_api_0097.html

.. _dds_api_0097:

Setting SQL Audit
=================

Function
--------

This API is used to set a policy for SQL audit logs.

URI
---

-  URI format

   POST https://{Endpoint}/v3/{project_id}/instances/{instance_id}/auditlog-policy

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

      +-------------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name              | Mandatory       | Type             | Description                                                                                                                                                                                                          |
      +===================+=================+==================+======================================================================================================================================================================================================================+
      | keep_days         | Yes             | Integer          | Specifies the number of days for storing audit logs. The value can be 0 or ranges from 7 to 732.                                                                                                                     |
      |                   |                 |                  |                                                                                                                                                                                                                      |
      |                   |                 |                  | -  **0**: indicates that SQL audit is disabled.                                                                                                                                                                      |
      |                   |                 |                  | -  **7** to **732**: indicates the retention days for audit logs after SQL audit is enabled.                                                                                                                         |
      +-------------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | reserve_auditlogs | No              | String           | This parameter is valid only when SQL audit is disabled.                                                                                                                                                             |
      |                   |                 |                  |                                                                                                                                                                                                                      |
      |                   |                 |                  | -  **true** (default value): indicates that historical audit logs are retained when SQL audit is disabled.                                                                                                           |
      |                   |                 |                  | -  **false**: indicates that existing historical audit logs are deleted when SQL audit is disabled.                                                                                                                  |
      +-------------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | audit_scope       | No              | String           | This parameter is valid only when the audit log policy is enabled. If this parameter is left blank or set to **all**, all audit log policies are enabled by default.                                                 |
      |                   |                 |                  |                                                                                                                                                                                                                      |
      |                   |                 |                  | Audit scope:                                                                                                                                                                                                         |
      |                   |                 |                  |                                                                                                                                                                                                                      |
      |                   |                 |                  | Enter the database or collection name. Use commas (,) to separate multiple databases or collections. If the name contains a comma (,), add a dollar sign ($) before the comma to distinguish it from the separators. |
      |                   |                 |                  |                                                                                                                                                                                                                      |
      |                   |                 |                  | Enter a maximum of 1024 characters. The value cannot contain spaces or the following special characters\ ``"[]{}():?`` The dollar sign ($) can be used only in escape mode.                                          |
      +-------------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | audit_types       | No              | Array of strings | This parameter is valid only when the audit log policy is enabled. If this parameter is left blank, all audit log policies are enabled by default.                                                                   |
      |                   |                 |                  |                                                                                                                                                                                                                      |
      |                   |                 |                  | Specifies the audit type. The value is **auth**, **insert**, **delete**, **update**, **query**, or **command**.                                                                                                      |
      +-------------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Request example

   POST https://dds.eu-de.otc.t-systems.com/v3/0549b4a43100d4f32f51c01c2fe4acdb/instances/5cecca4c20e04146862651b8d385f26ain02/auditlog-policy

   -  Enabling or updating the audit log policy

      .. code-block:: text

         {
           "keep_days": 7,
           "audit_scope": "all",
           "audit_types": [
             "insert"
           ]
         }

   -  Disabling the policy for SQL audit logs:

      .. code-block:: text

         {
           "keep_days": 0,
           "reserve_auditlogs": false
         }

Responses
---------

Response example

.. code-block:: text

   {}

Status Code
-----------

Status Code:200.

For more information, see :ref:`Status Code <dds_status_code>`.

Error Code
----------

For more information, see :ref:`Error Code <dds_error_code>`.
