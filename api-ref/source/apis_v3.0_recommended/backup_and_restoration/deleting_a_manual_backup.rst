:original_name: dds_api_0028.html

.. _dds_api_0028:

Deleting a Manual Backup
========================

Function
--------

This API is used to delete a manual backup for a DB instance.

URI
---

-  URI format

   DELETE https://{Endpoint}/v3/{project_id}/backups/{backup_id}

-  Parameter description

   .. table:: **Table 1** Parameter description

      ========== ========= =================================================
      Name       Mandatory Description
      ========== ========= =================================================
      project_id Yes       Specifies the project ID of a tenant in a region.
      backup_id  Yes       Specifies the backup file ID.
      ========== ========= =================================================

Requests
--------

-  Example request

   DELETE https://dds.eu-de.otc.t-systems.com/v3/0549b4a43100d4f32f51c01c2fe4acdb/backups/8d9586c40b33449a815518d4635a2cd9br02

Responses
---------

-  Parameter description

   .. table:: **Table 2** Parameter description

      ====== ====== ======================
      Name   Type   Description
      ====== ====== ======================
      job_id String Indicates the task ID.
      ====== ====== ======================

-  Response example

   .. code-block:: text

      {
          "job_id": "fcaab90b-960d-4441-b73d-a5b2532c5ec5"
      }

Status Code
-----------

Status Code:200.

For more information, see :ref:`Status Code <dds_status_code>`.

Error Code
----------

For more information, see :ref:`Error Code <dds_error_code>`.
