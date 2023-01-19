:original_name: dds_api_0025.html

.. _dds_api_0025:

Adding Nodes for a Cluster Instance
===================================

Function
--------

This API is used to add nodes for a specified cluster instance.

Constraints
-----------

-  Only the mongos and shard nodes can be added.
-  The specifications of the new node must be the same as those of the existing nodes in the instance.

URI
---

-  URI format

   POST https://{Endpoint}/v3/{project_id}/instances/{instance_id}/enlarge

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

      +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name            | Mandatory       | Type            | Description                                                                                                                                                                                                                  |
      +=================+=================+=================+==============================================================================================================================================================================================================================+
      | type            | Yes             | String          | Specifies the object to be scaled.                                                                                                                                                                                           |
      |                 |                 |                 |                                                                                                                                                                                                                              |
      |                 |                 |                 | -  Set the value to **mongos** if mongos nodes are to be added.                                                                                                                                                              |
      |                 |                 |                 | -  Set the value to **shard** if shard nodes are to be added.                                                                                                                                                                |
      +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | spec_code       | Yes             | String          | Specifies the resource specification code. For details about how to obtain the resource specification code, see the **flavors.spec_code** parameter in :ref:`Querying Database Specifications <dds_instance_specification>`. |
      +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | num             | Yes             | String          | Specifies the number of mongos or shard nodes to be added. A cluster instance supports up to 32 mongos nodes and 32 shard nodes.                                                                                             |
      +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | volume          | No              | Object          | Specifies the volume information. For more information, see :ref:`Table 3 <dds_api_0025__table62051323653>`.                                                                                                                 |
      |                 |                 |                 |                                                                                                                                                                                                                              |
      |                 |                 |                 | -  This parameter is not transferred when the mongos nodes are to be added.                                                                                                                                                  |
      |                 |                 |                 | -  This parameter is mandatory when the shard nodes are to be added.                                                                                                                                                         |
      |                 |                 |                 |                                                                                                                                                                                                                              |
      |                 |                 |                 |    .. note::                                                                                                                                                                                                                 |
      |                 |                 |                 |                                                                                                                                                                                                                              |
      |                 |                 |                 |       If multiple shards are added at a time, the shards must have the same specifications and disk capacity.                                                                                                                |
      +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. _dds_api_0025__table62051323653:

   .. table:: **Table 3** volume field data structure description

      +------+-----------+--------+------------------------------------------------------------------------------------------+
      | Name | Mandatory | Type   | Description                                                                              |
      +======+===========+========+==========================================================================================+
      | size | Yes       | String | Specifies the disk capacity of all new shards. The value range is from 10 GB to 2000 GB. |
      +------+-----------+--------+------------------------------------------------------------------------------------------+

-  Example request

   POST https://dds.eu-de.otc.t-systems.com/v3/0549b4a43100d4f32f51c01c2fe4acdb/instances/9136fd2a9fcd405ea4674276ce36dae8in02/enlarge

   Number of mongos nodes to be added:

   .. code-block:: text

      {
          "type": "mongos",
          "spec_code":"dds.mongodb.c3.medium.4.mongos",
          "num": 1
      }

   Number of shard nodes to be added:

   .. code-block:: text

      {
          "type": "shard",
          "spec_code":"dds.mongodb.c3.medium.4.shard",
          "num": 1,
              "volume": {
                   "size": 330
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
          "job_id": "4008c8914b624785a02ab7966d4d"
      }

Status Code
-----------

Status Code:202.

For more information, see :ref:`Status Code <dds_status_code>`.

Error Code
----------

For more information, see :ref:`Error Code <dds_error_code>`.
