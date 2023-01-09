:original_name: dds_api_0053.html

.. _dds_api_0053:

Modifying a DB Instance Name
============================

Function
--------

This API is used to modify a DB instance name.

Constraints
-----------

The name of the DB instance that is being created or fails to be created cannot be modified.

URI
---

-  URI format

   PUT https://{Endpoint}/v3/{project_id}/instances/{instance_id}/modify-name

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

      +-------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name              | Mandatory       | Type            | Description                                                                                                                                                                                                            |
      +===================+=================+=================+========================================================================================================================================================================================================================+
      | new_instance_name | Yes             | String          | Specifies the DB instance name. The instance name can be the same as an existing instance name.                                                                                                                        |
      |                   |                 |                 |                                                                                                                                                                                                                        |
      |                   |                 |                 | -  The instance name must contain 4 to 64 characters and must start with a letter. It is case sensitive and can contain letters, digits, hyphens (-), and underscores (_). It cannot contain other special characters. |
      +-------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Example request

   PUT https://dds.eu-de.otc.t-systems.com/v3/0549b4a43100d4f32f51c01c2fe4acdb/instances/9136fd2a9fcd405ea4674276ce36dae8in02/modify-name

   .. code-block:: text

      {
          "new_instance_name": "myNewName"
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
