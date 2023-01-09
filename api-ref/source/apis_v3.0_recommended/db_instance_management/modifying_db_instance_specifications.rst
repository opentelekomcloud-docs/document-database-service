:original_name: dds_api_0026.html

.. _dds_api_0026:

Modifying DB Instance Specifications
====================================

Function
--------

This API is used to modify the instance specifications.

.. important::

   Services will be interrupted for 5 to 10 minutes when you modify DB instance specifications. Exercise caution when performing this operation.

Constraints
-----------

-  If you want to change the specifications to other specifications of the same series, the new specifications cannot be the same as the original specifications.
-  Specifications can be modified only when the DB instance status is normal.

URI
---

-  URI format

   POST https://{Endpoint}/v3/{project_id}/instances/{instance_id}/resize

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

      +--------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------+
      | Name   | Mandatory | Type   | Description                                                                                                           |
      +========+===========+========+=======================================================================================================================+
      | resize | Yes       | Object | Specifies the specification information. For more information, see :ref:`Table 3 <dds_api_0026__table5971833216954>`. |
      +--------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------+

   .. _dds_api_0026__table5971833216954:

   .. table:: **Table 3** resize field data structure description

      +------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name             | Mandatory       | Type            | Description                                                                                                                                                                                                                              |
      +==================+=================+=================+==========================================================================================================================================================================================================================================+
      | target_type      | No              | String          | Specifies the object type:                                                                                                                                                                                                               |
      |                  |                 |                 |                                                                                                                                                                                                                                          |
      |                  |                 |                 | -  This parameter is mandatory for a cluster instance. If you modify the specifications of a mongos node, the value is **mongos**. If you modify the specifications of a shard node, the value is **shard**.                             |
      |                  |                 |                 | -  This parameter is not transferred for replica set and single node instances.                                                                                                                                                          |
      +------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | target_id        | Yes             | String          | Specifies the ID of the node or instance whose specifications are to be modified. You can obtain the ID by calling the API for querying instances. If you do not have an instance, you can call the API used for creating an instance.   |
      |                  |                 |                 |                                                                                                                                                                                                                                          |
      |                  |                 |                 | -  If you modify the specifications of a mongos node, the value is the mongos node ID. If you modify the specifications of a shard node, the value is the shard node ID.                                                                 |
      |                  |                 |                 | -  For a replica set instance, the value is the DB instance ID.                                                                                                                                                                          |
      |                  |                 |                 | -  For a single node instance, the value is the DB instance ID.                                                                                                                                                                          |
      +------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | target_spec_code | Yes             | String          | Specifies the resource specification code of the new specification. For details about how to obtain the value, see the response values of **flavors.spec_code** in :ref:`Querying Database Specifications <dds_instance_specification>`. |
      +------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Example request

   POST https://dds.eu-de.otc.t-systems.com/v3/0549b4a43100d4f32f51c01c2fe4acdb/instances/9136fd2a9fcd405ea4674276ce36dae8in02/resize

   Modify the mongos node specifications.

   .. code-block:: text

      {
        "resize": {
          "target_type": "mongos",
          "target_id": "a742c13a284949adad177672e8a0f01cno02",
          "target_spec_code": "dds.mongodb.c3.large.4.mongos"
        }
      }

   Modify the shard node specifications.

   .. code-block:: text

      {
        "resize": {
          "target_type": "shard",
          "target_id": "aeeb40a704904977ad78993d138ec942gr02",
          "target_spec_code": "dds.momgodb.c3.large.4.shard"
        }
      }

   Modify the config node specifications.

   .. code-block:: text

      {
        "resize": {
          "target_type": "config",
          "target_id": "10a1c330537b42c1a9b3f7a5ebcda35egr02",
          "target_spec_code": "dds.momgodb.c3.xlarge.2.config"
        }
      }

   Modify specifications of a replica set or a single node instance.

   .. code-block:: text

      {
        "resize": {
          "target_id": "aeeb40a704904977ad78993d138ec942in02",
          "target_spec_code": "dds.mongodb.c3.medium.4.repset"
        }
      }

Responses
---------

-  Parameter description

   .. table:: **Table 4** Parameter description

      ====== ====== ======================
      Name   Type   Description
      ====== ====== ======================
      job_id String Indicates the task ID.
      ====== ====== ======================

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
