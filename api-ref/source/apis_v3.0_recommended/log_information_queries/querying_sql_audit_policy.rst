:original_name: dds_api_0098.html

.. _dds_api_0098:

Querying SQL Audit Policy
=========================

Function
--------

This API is used to query the policy for SQL audit logs.

URI
---

-  URI format

   GET https://{Endpoint}/v3/{project_id}/instances/{instance_id}/auditlog-policy

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

-  Example request

   GET https://dds.eu-de.otc.t-systems.com/v3/0549b4a43100d4f32f51c01c2fe4acdb/instances/5cecca4c20e04146862651b8d385f26ain02/auditlog-policy

Responses
---------

-  Parameter description

   .. table:: **Table 2** Parameter description

      +-------------+------------------+-----------------------------------------------------------------------------------------------------+
      | Name        | Type             | Description                                                                                         |
      +=============+==================+=====================================================================================================+
      | keep_days   | Integer          | Indicates the number of days for storing audit logs. The value is **0** when SQL audit is disabled. |
      +-------------+------------------+-----------------------------------------------------------------------------------------------------+
      | audit_scope | String           | Indicates the audit scope.                                                                          |
      +-------------+------------------+-----------------------------------------------------------------------------------------------------+
      | audit_types | Array of strings | Indicates the audit type.                                                                           |
      +-------------+------------------+-----------------------------------------------------------------------------------------------------+

-  Response example

   .. code-block:: text

      {
         "keep_days":7,
         "audit_scope":"all",
         "audit_types":["insert"]
      }

Status Code
-----------

Status Code:200.

For more information, see :ref:`Status Code <dds_status_code>`.

Error Code
----------

For more information, see :ref:`Error Code <dds_error_code>`.
