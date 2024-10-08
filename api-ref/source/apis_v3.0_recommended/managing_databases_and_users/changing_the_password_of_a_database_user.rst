:original_name: dds_api_0075.html

.. _dds_api_0075:

Changing the Password of a Database User
========================================

Function
--------

This API is used to change the password of a database user

Constraints
-----------

This operation cannot be performed on frozen or abnormal instances.

URI
---

-  URI format

   PUT https://{Endpoint}/v3/{project_id}/instances/{instance_id}/reset-password

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

      +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name            | Mandatory       | Type            | Description                                                                                                                                                                              |
      +=================+=================+=================+==========================================================================================================================================================================================+
      | user_name       | No              | String          | Specifies the database username. The default value is **"rwuser"**.                                                                                                                      |
      |                 |                 |                 |                                                                                                                                                                                          |
      |                 |                 |                 | The value must be 1 to 64 characters and can contain only letters (from A to Z or from a to z), digits (from 0 to 9), hyphens (-), and periods (.).                                      |
      +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | user_pwd        | Yes             | String          | Specifies the database password.                                                                                                                                                         |
      |                 |                 |                 |                                                                                                                                                                                          |
      |                 |                 |                 | -  The value must be 8 to 32 characters in length and contain uppercase letters (A to Z), lowercase letters (a to z), digits (0 to 9), and special characters, such as\ ``~!@#%^*-_=+?`` |
      |                 |                 |                 | -  Enter a strong password to improve security, preventing security risks such as brute force cracking.                                                                                  |
      +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | db_name         | No              | String          | Specifies the database name. The default value is **"admin"**.                                                                                                                           |
      +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Request example

   .. code-block:: text

      {
      "user_name": "rwuser",
      "user_pwd": "******"
      }

Responses
---------

-  Response example

   .. code-block:: text

      {}

Status Code
-----------

Status Code:200.

For more information, see :ref:`Status Code <dds_status_code>`.

Error Code
----------

For more information, see :ref:`Error Code <dds_error_code>`.
