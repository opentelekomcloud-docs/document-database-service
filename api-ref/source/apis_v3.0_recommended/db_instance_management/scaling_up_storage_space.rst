:original_name: dds_api_0024.html

.. _dds_api_0024:

Scaling Up Storage Space
========================

Function
--------

This API is used to scale up the storage space of a DB instance.

URI
---

-  URI format

   POST https://{Endpoint}/v3/{project_id}/instances/{instance_id}/enlarge-volume

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

      +--------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------------------+
      | Name   | Mandatory | Type   | Description                                                                                                                           |
      +========+===========+========+=======================================================================================================================================+
      | volume | Yes       | Object | Specifies detailed information about the volume request. For more information, see :ref:`Table 3 <dds_api_0024__table3840102812918>`. |
      +--------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------------------+

   .. _dds_api_0024__table3840102812918:

   .. table:: **Table 3** volume field data structure description

      +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name            | Mandatory       | Type            | Description                                                                                                                                           |
      +=================+=================+=================+=======================================================================================================================================================+
      | group_id        | No              | String          | Specifies the role ID.                                                                                                                                |
      |                 |                 |                 |                                                                                                                                                       |
      |                 |                 |                 | -  For a cluster instance, this parameter is set to the ID of the shard group.                                                                        |
      |                 |                 |                 | -  This parameter is not transferred for replica set and single node instances.                                                                       |
      +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------+
      | size            | Yes             | String          | Specifies the requested disk capacity. The value must be an integer multiple of 10 and greater than the current storage space.                        |
      |                 |                 |                 |                                                                                                                                                       |
      |                 |                 |                 | -  In a cluster instance, this parameter indicates the storage space of shard nodes. The value range is from 10 GB to 2000 GB.                        |
      |                 |                 |                 | -  In a replica set instance, this parameter indicates the disk capacity of the DB instance to be expanded. The value range is from 10 GB to 2000 GB. |
      |                 |                 |                 | -  In a single node instance, this parameter indicates the disk capacity of the DB instance to be expanded. The value range is from 10 GB to 1000 GB. |
      +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Example request

   POST https://dds.eu-de.otc.t-systems.com/v3/0549b4a43100d4f32f51c01c2fe4acdb/instances/9136fd2a9fcd405ea4674276ce36dae8in02/enlarge-volume

   Clusters:

   .. code-block:: text

      {
          "volume":
              {
                  "group_id":"1b0c008adbcb495c81a3d5762a02a2abgr02",
                  "size":20
              }
      }

   Replica sets:

   .. code-block:: text

      {
          "volume":
              {
                  "size":20
              }
      }

   Single nodes:

   .. code-block:: text

      {
          "volume":
              {
                  "size":20
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
