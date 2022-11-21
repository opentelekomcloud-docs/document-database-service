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

   DELETE /v3/{project_id}/instances/{instance_id}

-  Parameter description

   .. table:: **Table 1** Parameter description

      =========== ========= =================================================
      Name        Mandatory Description
      =========== ========= =================================================
      project_id  Yes       Specifies the project ID of a tenant in a region.
      instance_id Yes       Specifies the DB instance ID.
      =========== ========= =================================================

Requests
--------

-  Request header

   .. code-block:: text

      DELETE https://DDS endpoint/v3/{project_id}/instances/{instance_id}

-  Request body

   N/A

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

**Status Code**
---------------

For more information, see :ref:`Status Code <dds_status_code>`.

Error Code
----------

For more information, see :ref:`Error Code <dds_error_code>`.
