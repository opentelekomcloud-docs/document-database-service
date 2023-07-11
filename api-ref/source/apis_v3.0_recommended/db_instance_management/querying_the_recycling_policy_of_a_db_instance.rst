:original_name: dds_api_0215.html

.. _dds_api_0215:

Querying the Recycling Policy of a DB Instance
==============================================

API Description
---------------

This API is used to query the recycling policy of a DB instance.

URI
---

-  URI format

   GET https://{Endpoint}/v3/{project_id}/instances/recycle-policy

-  Parameter description

   .. table:: **Table 1** Request parameters

      +--------------+-----------+--------+---------------------------------------------------+
      | Name         | Mandatory | Type   | Description                                       |
      +==============+===========+========+===================================================+
      | x-auth-token | Yes       | String | User token.                                       |
      +--------------+-----------+--------+---------------------------------------------------+
      | project_id   | Yes       | String | Specifies the project ID of a tenant in a region. |
      +--------------+-----------+--------+---------------------------------------------------+

Requests
--------

-  Example request

   GET https://dds.eu-de.otc.t-systems.com/v3/0549b4a43100d4f32f51c01c2fe4acdb/instances/recycle-policy

Responses
---------

-  Parameter description

   .. table:: **Table 2** Response body parameters

      +----------------+-----------------------------------------------------------------+----------------------------+
      | Name           | Type                                                            | Description                |
      +================+=================================================================+============================+
      | recycle_policy | :ref:`RecyclePolicy <dds_api_0215__table19191130122514>` object | Instance recycling policy. |
      +----------------+-----------------------------------------------------------------+----------------------------+

   .. _dds_api_0215__table19191130122514:

   .. table:: **Table 3** RecyclePolicy

      +--------------------------+-----------------------+------------------------------------------------------------------------------+
      | Name                     | Type                  | Description                                                                  |
      +==========================+=======================+==============================================================================+
      | enabled                  | Boolean               | Whether to enable the recycling policy.                                      |
      |                          |                       |                                                                              |
      |                          |                       | -  **true**: Enable the recycling policy.                                    |
      +--------------------------+-----------------------+------------------------------------------------------------------------------+
      | retention_period_in_days | Integer               | Policy retention period (1 to 7 days). The value must be a positive integer. |
      +--------------------------+-----------------------+------------------------------------------------------------------------------+

-  Response Example

   .. code-block::

      {
        "recycle_policy" : {
          "enabled" : true,
          "retention_period_in_days" : 3
        }
      }

Status Code
-----------

Status Code:200.

For more information, see :ref:`Status Code <dds_status_code>`.

Error Code
----------

For more information, see :ref:`Error Code <dds_error_code>`.
