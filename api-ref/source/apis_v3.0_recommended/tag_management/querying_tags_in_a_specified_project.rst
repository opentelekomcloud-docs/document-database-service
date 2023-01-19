:original_name: dds_api_0035.html

.. _dds_api_0035:

Querying Tags in a Specified Project
====================================

Function
--------

This API is used to query all tags of instances in a specified project.

URI
---

-  URI format

   GET https://{Endpoint}/v3/{project_id}/tags

-  Parameter description

   .. table:: **Table 1** Parameter description

      ========== ========= =================================================
      Name       Mandatory Description
      ========== ========= =================================================
      project_id Yes       Specifies the project ID of a tenant in a region.
      ========== ========= =================================================

Requests
--------

-  Example request

   GET https://dds.eu-de.otc.t-systems.com/v3/0549b4a43100d4f32f51c01c2fe4acdb/tags

Responses
---------

-  Parameter description

   .. table:: **Table 2** Parameter description

      +------+-----------+------------------+------------------------------------------------------------------------------------------------------+
      | Name | Mandatory | Type             | Description                                                                                          |
      +======+===========+==================+======================================================================================================+
      | tags | Yes       | Array of objects | Indicates the tag list. For more information, see :ref:`Table 3 <dds_api_0035__table1429181375610>`. |
      +------+-----------+------------------+------------------------------------------------------------------------------------------------------+

   .. _dds_api_0035__table1429181375610:

   .. table:: **Table 3** tags field data structure description

      +-----------------+-----------------+------------------+--------------------------------------------------------------------------------------------------------------+
      | Name            | Mandatory       | Type             | Description                                                                                                  |
      +=================+=================+==================+==============================================================================================================+
      | key             | Yes             | String           | Indicates the tag key. The value contains 36 Unicode characters and cannot be blank.                         |
      |                 |                 |                  |                                                                                                              |
      |                 |                 |                  | Character set: 0-9, A-Z, a-z, "_", "-", and "@".                                                             |
      +-----------------+-----------------+------------------+--------------------------------------------------------------------------------------------------------------+
      | values          | Yes             | Array of strings | Lists the tag values. The value contains a maximum of 43 Unicode characters and can also be an empty string. |
      |                 |                 |                  |                                                                                                              |
      |                 |                 |                  | Character set: 0-9, A-Z, a-z, "_", "-", and "@".                                                             |
      +-----------------+-----------------+------------------+--------------------------------------------------------------------------------------------------------------+

-  Response example

   .. code-block:: text

      {
        "tags": [
          {
            "key": "key1",
            "values": [
              "value1",
              "value2"
            ]
          },
          {
            "key": "key2",
            "values": [
              "value1",
              "value2"
            ]
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
