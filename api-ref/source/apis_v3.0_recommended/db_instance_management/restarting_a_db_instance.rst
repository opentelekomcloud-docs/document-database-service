:original_name: dds_api_0021.html

.. _dds_api_0021:

Restarting a DB Instance
========================

Function
--------

This API is used to restart a DB instance.

.. important::

   The DDS DB instance will be unavailable during the restart process. Exercise caution when performing this operation.

Constraints
-----------

If the instance status is not normal, the instance cannot be restarted.

URI
---

-  URI format

   POST https://{Endpoint}/v3/{project_id}/instances/{instance_id}/restart

-  Parameter description

   .. table:: **Table 1** Parameter description

      +-------------+-----------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name        | Mandatory | Description                                                                                                                                                             |
      +=============+===========+=========================================================================================================================================================================+
      | project_id  | Yes       | Specifies the project ID of a tenant in a region.                                                                                                                       |
      +-------------+-----------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | instance_id | Yes       | Specifies the instance ID, which can be obtained by calling the API for querying instances. If you do not have an instance, you can call the API to create an instance. |
      +-------------+-----------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Requests
--------

-  Parameter description

   .. table:: **Table 2** Parameter description

      +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name            | Mandatory       | Type            | Description                                                                                                                                                                                          |
      +=================+=================+=================+======================================================================================================================================================================================================+
      | target_type     | No              | String          | Specifies the type of the object to restart.                                                                                                                                                         |
      |                 |                 |                 |                                                                                                                                                                                                      |
      |                 |                 |                 | -  This parameter is mandatory when you restart one or more nodes of a cluster instance.                                                                                                             |
      |                 |                 |                 |                                                                                                                                                                                                      |
      |                 |                 |                 |    -  Set the value to **mongos** if mongos nodes are restarted.                                                                                                                                     |
      |                 |                 |                 |    -  Set the value to **shard** if shard nodes are restarted.                                                                                                                                       |
      |                 |                 |                 |    -  Set the value to **config** if config nodes are restarted.                                                                                                                                     |
      |                 |                 |                 |                                                                                                                                                                                                      |
      |                 |                 |                 | -  This parameter is not transferred when the DB instance is restarted.                                                                                                                              |
      +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | target_id       | Yes             | String          | Specifies the ID of the object to be restarted, which can be obtained by calling the API for querying instances. If you do not have an instance, you can call the API used for creating an instance. |
      |                 |                 |                 |                                                                                                                                                                                                      |
      |                 |                 |                 | -  In a cluster instance, the value is the ID of the node to restart.                                                                                                                                |
      |                 |                 |                 | -  When you restart the entire DB instance, the value is the DB instance ID.                                                                                                                         |
      +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Example request

   POST https://dds.eu-de.otc.t-systems.com/v3/0549b4a43100d4f32f51c01c2fe4acdb/instances/9136fd2a9fcd405ea4674276ce36dae8in02/restart

   Restart the DB instance.

   .. code-block:: text

      {
          "target_id":"9136fd2a9fcd405ea4674276ce36dae8in02"
      }

   Restart shards.

   .. code-block:: text

      {
             "target_type":"shard",
             "target_id":"84e7c96b82aa4fedb3b00f98edd71ba4gr02"
      }

   Restart configs.

   .. code-block:: text

      {
            "target_type":"config",
            "target_id":"06439baa35c146d3a8965af59d370908gr02"
      }

   Restart mongos.

   .. code-block:: text

      {
            "target_type":"mongos",
            "target_id":"bd4dccbd53ae48d5bd3046bebf715079no02"
      }

Responses
---------

-  Parameter description

   .. table:: **Table 3** Parameter description

      ====== ====== ==========================
      Name   Type   Description
      ====== ====== ==========================
      job_id String Indicates the workflow ID.
      ====== ====== ==========================

-  Response example

   .. code-block:: text

      {
          "job_id": "3711e2ad-5787-49bc-a47f-3f0b066af9f5"
      }

Status Code
-----------

Status Code:202.

For more information, see :ref:`Status Code <dds_status_code>`.

Error Code
----------

For more information, see :ref:`Error Code <dds_error_code>`.
