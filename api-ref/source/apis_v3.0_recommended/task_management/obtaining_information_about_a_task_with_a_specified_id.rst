:original_name: dds_api_0118.html

.. _dds_api_0118:

Obtaining Information About a Task with a Specified ID
======================================================

Function
--------

This API is used to obtain information about a task with a specified ID in the task center.

Constraints
-----------

-  Currently, only asynchronous tasks in the task center of DDS Community Edition within one month can be queried.
-  After a job is generated, it takes several seconds to query the job ID.
-  The following asynchronous tasks can be queried: creating an instance (single node, replica set, or cluster), scaling up storage, changing instance class, scaling up a node, restarting a node, performing a primary/standby switchover, changing a private IP address, changing a security group, changing a database port, binding or unbinding an EIP, switching the SSL mode, and changing an AZ, enabling the shard/config IP address, creating a physical backup/snapshot backup, restoration to a new instance using a backup, point-in-time recovery, and database/table-level restoration to a specified time point.

URI
---

-  URI format

   GET /v3/{project_id}/jobs?id={id}

-  Parameter description

   .. table:: **Table 1** Parameter description

      +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------+
      | Name                  | Mandatory             | Description                                                                                        |
      +=======================+=======================+====================================================================================================+
      | project_id            | Yes                   | Project ID of a tenant in a region.                                                                |
      |                       |                       |                                                                                                    |
      |                       |                       | For details about how to obtain the project ID, see :ref:`Obtaining a Project ID <dds_projectid>`. |
      +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------+
      | id                    | Yes                   | Task ID                                                                                            |
      +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------+

Requests
--------

-  Example request

   GET https://dds.eu-de.otc.t-systems.com/v3/0549b4a43100d4f32f51c01c2fe4acdb/jobs?id=a9767ede-fe0f-4888-9003-e843a4c90514

Responses
---------

-  Normal response

   .. table:: **Table 2** Parameter description

      +------+--------+----------------------------------------------------------------------------------------+
      | Name | Type   | Description                                                                            |
      +======+========+========================================================================================+
      | job  | Object | Task information. For details, see :ref:`Table 3 <dds_api_0118__table54571314103317>`. |
      +------+--------+----------------------------------------------------------------------------------------+

   .. _dds_api_0118__table54571314103317:

   .. table:: **Table 3** job field data structure description

      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name                  | Type                  | Description                                                                                                                                                                    |
      +=======================+=======================+================================================================================================================================================================================+
      | id                    | String                | Task ID                                                                                                                                                                        |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | name                  | String                | Task name                                                                                                                                                                      |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | status                | String                | Task execution status                                                                                                                                                          |
      |                       |                       |                                                                                                                                                                                |
      |                       |                       | Valid value:                                                                                                                                                                   |
      |                       |                       |                                                                                                                                                                                |
      |                       |                       | -  **Running**: The task is being executed.                                                                                                                                    |
      |                       |                       | -  **Completed**: The task is successfully executed.                                                                                                                           |
      |                       |                       | -  **Failed**: The task fails to be executed.                                                                                                                                  |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | created               | String                | Creation time in the "yyyy-mm-ddThh:mm:ssZ" format.                                                                                                                            |
      |                       |                       |                                                                                                                                                                                |
      |                       |                       | **T** is the separator between the calendar and the hourly notation of time. **Z** indicates the time zone offset.                                                             |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | ended                 | String                | End time in the "yyyy-mm-ddThh:mm:ssZ" format.                                                                                                                                 |
      |                       |                       |                                                                                                                                                                                |
      |                       |                       | **T** is the separator between the calendar and the hourly notation of time. **Z** indicates the time zone offset.                                                             |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | progress              | String                | Task execution progress                                                                                                                                                        |
      |                       |                       |                                                                                                                                                                                |
      |                       |                       | .. note::                                                                                                                                                                      |
      |                       |                       |                                                                                                                                                                                |
      |                       |                       |    The execution progress (such as **"60%"**, indicating the task execution progress is 60%) is displayed only when the task is being executed. Otherwise, **""** is returned. |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | instance              | Object                | Instance on which the task is executed.                                                                                                                                        |
      |                       |                       |                                                                                                                                                                                |
      |                       |                       | For details, see :ref:`Table 4 <dds_api_0118__table4062895917262>`.                                                                                                            |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | fail_reason           | String                | Task failure information.                                                                                                                                                      |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. _dds_api_0118__table4062895917262:

   .. table:: **Table 4** instance field data structure description

      ==== ====== ================
      Name Type   Description
      ==== ====== ================
      id   String Instance ID
      name String DB instance name
      ==== ====== ================

   .. note::

      In the response example, some tasks in the task center are used as examples.

-  Example normal response

   A task is successfully executed.

   .. code-block:: text

      {
        "job": {
          "id": "f85104b5-4a9c-4e0f-9505-fc5409d8f7ae",
          "name": "Create_MongoDB",
          "status": "Completed",
          "created": "2021-07-12T09:22:04+0000",
          "ended": "2021-07-12T10:10:13+0000",
          "progress": "",
          "instance": {
            "id": "d87f5b33049144ec95f0cab0a5f22cfbin02",
            "name": "dds-5ff4-sh"
          },
          "fail_reason": null
        }
      }

   A task is being executed:

   .. code-block:: text

      {
        "job": {
          "id": "9d10bfd1-affb-49c3-b977-298950a8d6fa",
          "name": "Create_MongoDB",
          "status": "Running",
          "created": "2021-07-13T07:28:43+0000",
          "ended": "2021-07-13T07:28:53+0000",
          "progress": "9%",
          "instance": {
            "id": "cf538a2dd8ec4b26860b27060902712fin02",
            "name": "dds-3a98-wcc"
          },
          "fail_reason": null
        }
      }

   A task fails to be executed:

   .. code-block:: text

      {
        "job": {
          "id": "a03b1b8a-b756-467c-8a49-38720c3d23ec",
          "name": "Restore_MongoDB_Replica",
          "status": "Failed",
          "created": "2021-07-13T04:55:58+0000",
          "ended": "2021-07-13T05:20:04+0000",
          "progress": "",
          "instance": {
            "id": "7beb15d5db9c4742b7c817789244844ein02",
            "name": "lenn-v3-restore-4"
          },
      "fail_reason": "Failed to upgrade the DB Agent."
        }
      }

Status Code
-----------

Status Code:200.

For more information, see :ref:`Status Code <dds_status_code>`.

Error Code
----------

For more information, see :ref:`Error Code <dds_error_code>`.
