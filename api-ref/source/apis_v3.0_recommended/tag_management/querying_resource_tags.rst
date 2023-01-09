:original_name: dds_api_0034.html

.. _dds_api_0034:

Querying Resource Tags
======================

Function
--------

This API is used to query tags of a specified resource.

Constraints
-----------

A maximum of 20 tags can be added to a DB instance. The tag key must be unique.

URI
---

-  URI format

   GET https://{Endpoint}/v3/{project_id}/instances/{instance_id}/tags

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

-  Example request

   GET https://dds.eu-de.otc.t-systems.com/v3/0549b4a43100d4f32f51c01c2fe4acdb/instances/cc6345c64cec47499182467ea0dd432ain02/tags

Responses
---------

-  Parameter description

   .. table:: **Table 2** Parameter description

      +------+-----------+------------------+-----------------------------------------------------------------------------------------------------+
      | Name | Mandatory | Type             | Description                                                                                         |
      +======+===========+==================+=====================================================================================================+
      | tags | Yes       | Array of objects | Indicates the tag list. For more information, see :ref:`Table 3 <dds_api_0034__table066514318552>`. |
      +------+-----------+------------------+-----------------------------------------------------------------------------------------------------+

   .. _dds_api_0034__table066514318552:

   .. table:: **Table 3** tags field data structure description

      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------+
      | Name            | Mandatory       | Type            | Description                                                                                                     |
      +=================+=================+=================+=================================================================================================================+
      | key             | Yes             | String          | Indicates the tag key. The value contains 36 Unicode characters and cannot be blank.                            |
      |                 |                 |                 |                                                                                                                 |
      |                 |                 |                 | Character set: 0-9, A-Z, a-z, "_", "-", and "@".                                                                |
      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------+
      | value           | Yes             | String          | Indicates the tag value. The value contains a maximum of 43 Unicode characters and can also be an empty string. |
      |                 |                 |                 |                                                                                                                 |
      |                 |                 |                 | Character set: 0-9, A-Z, a-z, "_", "-", and "@".                                                                |
      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------+

-  Response example

   .. code-block:: text

      {
        "tags": [
          {
            "key": "key1",
            "value": "value1"
          },
          {
            "key": "key2",
            "value": "value2"
          }
        ]
      }

Status Code
-----------

Status Code:200.

For more information, see :ref:`Status Code <dds_status_code>`.

Error Code
----------

For more information, see :ref:`Error Code <dds_error_code>`.
