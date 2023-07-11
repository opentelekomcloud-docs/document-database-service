:original_name: dds_api_0138.html

.. _dds_api_0138:

Setting the Recycle Bin Policy
==============================

API Description
---------------

This API is used to set the recycle bin policy for an instance.

URI
---

-  URI format

   PUT https://{Endpoint}/v3/{project_id}/instances/recycle-policy

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

-  Parameter description

   .. table:: **Table 2** Request body parameters

      +----------------+-----------+--------+-----------------------------------------------------------------------------------------------+
      | Name           | Mandatory | Type   | Description                                                                                   |
      +================+===========+========+===============================================================================================+
      | recycle_policy | Yes       | Object | Instance recycling policy. For details, see :ref:`Table 3 <dds_api_0138__table159257245612>`. |
      +----------------+-----------+--------+-----------------------------------------------------------------------------------------------+

   .. _dds_api_0138__table159257245612:

   .. table:: **Table 3** RecyclePolicy

      +--------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name                     | Mandatory       | Type            | Description                                                                                                                                              |
      +==========================+=================+=================+==========================================================================================================================================================+
      | enabled                  | Yes             | Boolean         | The recycling policy is enabled and cannot be disabled.                                                                                                  |
      |                          |                 |                 |                                                                                                                                                          |
      |                          |                 |                 | -  **true**: The recycling policy is enabled.                                                                                                            |
      +--------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+
      | retention_period_in_days | No              | Integer         | Policy retention duration (1 to 7 days). The value is a positive integer. If this parameter is left blank, the policy is retained for 7 days by default. |
      +--------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Request example

   .. code-block:: text

      PUT https://dds.eu-de.otc.t-systems.com/v3/619d3e78f61b4be68bc5aa0b59edcf7b/instances/recycle-policy

      {
        "recycle_policy" : {
          "enabled" : true,
          "retention_period_in_days" : 3
        }
      }

Responses
---------

-  Parameter description

   None

-  Response example

   None

Status Code
-----------

Status Code:200.

For more information, see :ref:`Status Code <dds_status_code>`.

Error Code
----------

For more information, see :ref:`Error Code <dds_error_code>`.
