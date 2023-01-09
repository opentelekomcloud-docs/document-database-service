:original_name: dds_api_0022.html

.. _dds_api_0022:

Deleting a DB Instance
======================

Function
--------

This API is used to delete a DB instance.

URI
---

-  URI format

   DELETE https://{Endpoint}/v3/{project_id}/instances/{instance_id}

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

   DELETE https://dds.eu-de.otc.t-systems.com/v3/0549b4a43100d4f32f51c01c2fe4acdb/instances/9136fd2a9fcd405ea4674276ce36dae8in02

Responses
---------

-  Parameter description

   .. table:: **Table 2** Parameter description

      ====== ====== ==========================
      Name   Type   Description
      ====== ====== ==========================
      job_id String Indicates the workflow ID.
      ====== ====== ==========================

-  Response example

   .. code-block:: text

      {
            "job_id": "252f11f1-2912-4c06-be55-1999bde659c5"
      }

Status Code
-----------

Status Code:202.

For more information, see :ref:`Status Code <dds_status_code>`.

Error Code
----------

For more information, see :ref:`Error Code <dds_error_code>`.
