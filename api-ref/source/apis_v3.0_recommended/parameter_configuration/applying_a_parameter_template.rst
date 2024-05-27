:original_name: dds_api_0107.html

.. _dds_api_0107:

Applying a Parameter Template
=============================

Description
-----------

This API is used to change a parameter template for a specified DB instance.

URI
---

-  URI format

   PUT https://{Endpoint}/v3/{project_id}/configurations/{config_id}/apply

.. table:: **Table 1** Request parameters

   +--------------+--------+-----------+---------------------------------------------------+
   | Name         | Type   | Mandatory | Description                                       |
   +==============+========+===========+===================================================+
   | x-auth-token | String | Yes       | User token.                                       |
   +--------------+--------+-----------+---------------------------------------------------+
   | project_id   | String | Yes       | Specifies the project ID of a tenant in a region. |
   +--------------+--------+-----------+---------------------------------------------------+
   | config_id    | String | Yes       | Parameter template ID.                            |
   +--------------+--------+-----------+---------------------------------------------------+

Requests
--------

-  Parameter description

   .. table:: **Table 2** Request body parameters

      +-----------------+-----------------+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name            | Mandatory       | Type             | Description                                                                                                                                                                                                      |
      +=================+=================+==================+==================================================================================================================================================================================================================+
      | entity_ids      | Yes             | Array of strings | Instance IDs, group IDs, or node IDs. You can call the API used for querying instances and details to obtain the value. If you do not have an instance, you can call the API used for creating an instance.      |
      |                 |                 |                  |                                                                                                                                                                                                                  |
      |                 |                 |                  | -  If the DB instance type is cluster and the shard or config parameter template is to be changed, the value is the group ID. If the parameter template of the mongos node is changed, the value is the node ID. |
      |                 |                 |                  |                                                                                                                                                                                                                  |
      |                 |                 |                  | -  If the DB instance to be changed is a replica set instance or a single node instance, the value is the instance ID.                                                                                           |
      +-----------------+-----------------+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Example Request
---------------

Applying a parameter template whose **entity_ids** is **73ea2bf70c73497f89ee0ad4ee008aa2no02** to a specified DB instance

.. code-block::

   {
     "entity_ids": [
       "73ea2bf70c73497f89ee0ad4ee008aa2no02"
     ]
   }

Responses
---------

-  Parameter description

   .. table:: **Table 3** Response body parameters

      +--------+--------+------------------------------------------------------------------------------+
      | Name   | Type   | Description                                                                  |
      +========+========+==============================================================================+
      | job_id | String | Indicates the ID of the asynchronous task for applying a parameter template. |
      +--------+--------+------------------------------------------------------------------------------+

-  Response example

   .. code-block:: text

      {
        "job_id" : "bf26cf3c-d046-4080-bb45-f114be7afa5f"
      }

Status Code
-----------

Status Code:200.

For more information, see :ref:`Status Code <dds_status_code>`.

Error Code
----------

For more information, see :ref:`Error Code <dds_error_code>`.
