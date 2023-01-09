:original_name: dds_api_0051.html

.. _dds_api_0051:

Enabling or Disabling SSL
=========================

Function
--------

This API is used to enable or disable SSL.

Constraints
-----------

-  This operation cannot be performed on frozen or abnormal instances.
-  The DB instance must be restarted to make port number modifications take effect. Exercise caution when enabling or disabling SSL.

URI
---

-  URI format

   POST https://{Endpoint}/v3/{project_id}/instances/{instance_id}/switch-ssl

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

      +-----------------+-----------------+-----------------+--------------------------------------------------------------------+
      | Name            | Mandatory       | Type            | Description                                                        |
      +=================+=================+=================+====================================================================+
      | ssl_option      | Yes             | String          | Specifies whether to enable or disable SSL.                        |
      |                 |                 |                 |                                                                    |
      |                 |                 |                 | Valid value:                                                       |
      |                 |                 |                 |                                                                    |
      |                 |                 |                 | -  The value **0** indicates that SSL is requested to be disabled. |
      |                 |                 |                 | -  The value **1** indicates that SSL is requested to be enabled.  |
      +-----------------+-----------------+-----------------+--------------------------------------------------------------------+

-  Example request

   POST https://dds.eu-de.otc.t-systems.com/v3/0549b4a43100d4f32f51c01c2fe4acdb/instances/9136fd2a9fcd405ea4674276ce36dae8in02/switch-ssl

   .. code-block:: text

      {
          "ssl_option": "0"
      }

Responses
---------

-  Parameter description

   .. table:: **Table 3** Parameter description

      +-----------------------+-----------------------+--------------------------------------------------------------------+
      | Name                  | Type                  | Description                                                        |
      +=======================+=======================+====================================================================+
      | job_id                | String                | Indicates the workflow ID.                                         |
      +-----------------------+-----------------------+--------------------------------------------------------------------+
      | ssl_option            | String                | Indicates whether to enable or disable SSL.                        |
      |                       |                       |                                                                    |
      |                       |                       | Valid value:                                                       |
      |                       |                       |                                                                    |
      |                       |                       | -  The value **0** indicates that SSL is requested to be disabled. |
      |                       |                       | -  The value **1** indicates that SSL is requested to be enabled.  |
      +-----------------------+-----------------------+--------------------------------------------------------------------+

-  Response example

   .. code-block:: text

      {
          "job_id": "3711e2ad-5787-49bc-a47f-3f0b066af9f5",
          "ssl_option": "0"
      }

Status Code
-----------

Status Code:200.

For more information, see :ref:`Status Code <dds_status_code>`.

Error Code
----------

For more information, see :ref:`Error Code <dds_error_code>`.
