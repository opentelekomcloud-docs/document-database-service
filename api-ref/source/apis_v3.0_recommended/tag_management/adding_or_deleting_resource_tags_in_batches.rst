:original_name: dds_api_0033.html

.. _dds_api_0033:

Adding or Deleting Resource Tags in Batches
===========================================

Function
--------

This API is used to add or delete tags of the specified instance in batches.

Constraints
-----------

-  A maximum of 20 tags can be added to a DB instance. The tag key must be unique.

   -  If the request body contains duplicated keys, an error message will be reported when the API is called.
   -  If the key in the request body is the same as an existing key in the specified instance, the value of the **value** parameter that corresponds to the existing key is overwritten.

-  If tags to be deleted do not exist, the operation is considered to be successful by default. The character set of the tags will not be checked. The tag structure in the request body cannot be missing, and the key cannot be left blank or an empty string.

URI
---

-  URI format

   POST https://{Endpoint}/v3/{project_id}/instances/{instance_id}/tags/action

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

      +-----------------+-----------------+------------------+-------------------------------------------------------------------------------------------------------+
      | Name            | Mandatory       | Type             | Description                                                                                           |
      +=================+=================+==================+=======================================================================================================+
      | action          | Yes             | String           | Specifies the operation identifier. Valid value:                                                      |
      |                 |                 |                  |                                                                                                       |
      |                 |                 |                  | -  **create**: indicates to add tags.                                                                 |
      |                 |                 |                  | -  **delete**: indicates to delete tags.                                                              |
      +-----------------+-----------------+------------------+-------------------------------------------------------------------------------------------------------+
      | tags            | Yes             | Array of objects | Specifies the tag list. For more information, see :ref:`Table 3 <dds_api_0033__table19347161295418>`. |
      |                 |                 |                  |                                                                                                       |
      |                 |                 |                  | .. note::                                                                                             |
      |                 |                 |                  |                                                                                                       |
      |                 |                 |                  |    When you delete tags, do not check the character set of this parameter.                            |
      +-----------------+-----------------+------------------+-------------------------------------------------------------------------------------------------------+

   .. _dds_api_0033__table19347161295418:

   .. table:: **Table 3** tags field data structure description

      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name            | Mandatory       | Type            | Description                                                                                                                                                                                               |
      +=================+=================+=================+===========================================================================================================================================================================================================+
      | key             | Yes             | String          | Specifies the tag key. It contains a maximum of 36 Unicode characters. It cannot be null or an empty string or contain spaces. Before verifying and using **key**, spaces are automatically filtered out. |
      |                 |                 |                 |                                                                                                                                                                                                           |
      |                 |                 |                 | Character set: 0-9, A-Z, a-z, "_", "-", and "@".                                                                                                                                                          |
      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | value           | No              | String          | Specifies the tag value. It contains a maximum of 43 Unicode characters, can be an empty string, and cannot contain spaces. Before verifying or using **value**, spaces are automatically filtered out.   |
      |                 |                 |                 |                                                                                                                                                                                                           |
      |                 |                 |                 | Character set: 0-9, A-Z, a-z, "_", "-", and "@".                                                                                                                                                          |
      |                 |                 |                 |                                                                                                                                                                                                           |
      |                 |                 |                 | -  If **action** is set to **create**, this parameter is mandatory.                                                                                                                                       |
      |                 |                 |                 | -  If **action** is set to **delete**, this parameter is optional.                                                                                                                                        |
      |                 |                 |                 |                                                                                                                                                                                                           |
      |                 |                 |                 |    .. note::                                                                                                                                                                                              |
      |                 |                 |                 |                                                                                                                                                                                                           |
      |                 |                 |                 |       If **value** is specified, tags are deleted by key and value. If **value** is not specified, tags are deleted by key.                                                                               |
      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Example request

   POST https://dds.eu-de.otc.t-systems.com/v3/0549b4a43100d4f32f51c01c2fe4acdb/instances/cc6345c64cec47499182467ea0dd432ain02/tags/action

   Add tags.

   .. code-block:: text

      {
        "action": "create",
        "tags": [
          {
            "key": "key1",
            "value": "value1"
          },
          {
            "key": "key",
            "value": "value3"
          }
        ]
      }

   Delete tags.

   .. code-block:: text

      {
        "action": "delete",
        "tags": [
          {
            "key": "key1"
          },
          {
            "key": "key2",
            "value": "value3"
          }
        ]
      }

Responses
---------

.. code-block:: text

   {}

Status Code
-----------

Status Code:200.

For more information, see :ref:`Status Code <dds_status_code>`.

Error Code
----------

For more information, see :ref:`Error Code <dds_error_code>`.
