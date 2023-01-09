:original_name: dds_api_0027.html

.. _dds_api_0027:

Creating a Manual Backup
========================

Function
--------

This API is used to create a manual backup for a DB instance.

URI
---

-  URI format

   POST https://{Endpoint}/v3/{project_id}/backups

-  Parameter description

   .. table:: **Table 1** Parameter description

      ========== ========= =================================================
      Name       Mandatory Description
      ========== ========= =================================================
      project_id Yes       Specifies the project ID of a tenant in a region.
      ========== ========= =================================================

Requests
--------

-  Parameter description

   .. table:: **Table 2** Parameter description

      +--------+-----------+--------+----------------------------------------------------------------------------------------------------------------------+
      | Name   | Mandatory | Type   | Description                                                                                                          |
      +========+===========+========+======================================================================================================================+
      | backup | Yes       | Object | Specifies the backup parameter objects For more information, see :ref:`Table 3 <dds_api_0027__table35260043174853>`. |
      +--------+-----------+--------+----------------------------------------------------------------------------------------------------------------------+

   .. _dds_api_0027__table35260043174853:

   .. table:: **Table 3** backup field data structure description

      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name            | Mandatory       | Type            | Description                                                                                                                                                                                                     |
      +=================+=================+=================+=================================================================================================================================================================================================================+
      | instance_id     | Yes             | String          | Specifies the instance ID, which can be obtained by calling the API for querying instances. If you do not have an instance, you can call the API used for creating an instance.                                 |
      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | name            | Yes             | String          | Specifies the manual backup name.                                                                                                                                                                               |
      |                 |                 |                 |                                                                                                                                                                                                                 |
      |                 |                 |                 | The value must be 4 to 64 characters in length and start with a letter (from A to Z or from a to z). It is case-sensitive and can contain only letters, digits (from 0 to 9), hyphens (-), and underscores (_). |
      |                 |                 |                 |                                                                                                                                                                                                                 |
      |                 |                 |                 | .. caution::                                                                                                                                                                                                    |
      |                 |                 |                 |                                                                                                                                                                                                                 |
      |                 |                 |                 |    CAUTION:                                                                                                                                                                                                     |
      |                 |                 |                 |    Name of the Backup has to be unique among all other backups on Project.                                                                                                                                      |
      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | description     | No              | String          | Specifies the manual backup description.                                                                                                                                                                        |
      |                 |                 |                 |                                                                                                                                                                                                                 |
      |                 |                 |                 | The description must consist of a maximum of 256 characters and cannot contain the following special characters: >!<"&'=                                                                                        |
      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Example request

   POST https://dds.eu-de.otc.t-systems.com/v3/0549b4a43100d4f32f51c01c2fe4acdb/backups

   .. code-block:: text

      {
              "backup":{
                      "instance_id": "a89dab5e39394eccbdb77b19d57b0180in02",
                      "name": "mybackup1",
                      "description": "The first Manual backup"
              }
      }

Responses
---------

-  Parameter description

   .. table:: **Table 4** Parameter description

      ========= ====== ==============================================
      Name      Type   Description
      ========= ====== ==============================================
      job_id    String The ID of the asynchronous manual backup task.
      backup_id String Manual backup ID
      ========= ====== ==============================================

-  Response example

   .. code-block:: text

      {
          "job_id": "a03b1b8a-b756-467c-8a49-38720c3d23ec",
          "backup_id": "bf9ee62a7f7044c583c6765c916c36edbr02"
      }

Status Code
-----------

Status Code:200.

For more information, see :ref:`Status Code <dds_status_code>`.

Error Code
----------

For more information, see :ref:`Error Code <dds_error_code>`.
