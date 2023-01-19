:original_name: dds_api_0032.html

.. _dds_api_0032:

Querying Resources by Tag
=========================

Function
--------

This API is used to query the specified DB instances by tag.

Constraints
-----------

A maximum of 20 tags can be added to a DB instance. The tag key must be unique.

URI
---

-  URI format

   POST https://{Endpoint}/v3/{project_id}/instances/action

-  Parameter description

   .. table:: **Table 1** Parameter description

      ========== ========= =================================================
      Name       Mandatory Description
      ========== ========= =================================================
      project_id Yes       Specifies the project ID of a tenant in a region.
      ========== ========= =================================================

Requests
--------

-  Parameter description

   .. table:: **Table 2** Parameter description

      +-----------------+-----------------+------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name            | Mandatory       | Type             | Description                                                                                                                                                              |
      +=================+=================+==================+==========================================================================================================================================================================+
      | offset          | No              | String           | Specifies the index position. The query starts from the next piece of data indexed by this parameter.                                                                    |
      |                 |                 |                  |                                                                                                                                                                          |
      |                 |                 |                  | -  If **action** is set to **count**, this parameter is not transferred.                                                                                                 |
      |                 |                 |                  | -  If **action** is set to **filter**, this parameter must be a positive integer. The default value is 0, indicating that the query starts from the first piece of data. |
      +-----------------+-----------------+------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | limit           | No              | String           | Specifies the number of resources to be queried.                                                                                                                         |
      |                 |                 |                  |                                                                                                                                                                          |
      |                 |                 |                  | -  If **action** is set to **count**, this parameter is not transferred.                                                                                                 |
      |                 |                 |                  | -  If **action** is set to **filter**, the value range is from 1 to 100. If this parameter is not transferred, the first 100 DB instances are queried by default.        |
      +-----------------+-----------------+------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | action          | Yes             | String           | Specifies the operation identifier.                                                                                                                                      |
      |                 |                 |                  |                                                                                                                                                                          |
      |                 |                 |                  | -  If **action** is set to **filter**, instances are queried by tag filtering criteria.                                                                                  |
      |                 |                 |                  | -  If **action** is set to **count**, only the total number of records is returned.                                                                                      |
      +-----------------+-----------------+------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | matches         | No              | Array of objects | Specifies the search field.                                                                                                                                              |
      |                 |                 |                  |                                                                                                                                                                          |
      |                 |                 |                  | -  If the value is left blank, the query is not based on the instance name or instance ID.                                                                               |
      |                 |                 |                  | -  If the value is not empty, see :ref:`Table 4 <dds_api_0032__table86147511997>`.                                                                                       |
      +-----------------+-----------------+------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | tags            | No              | Array of objects | Specifies the included tags. Each tag contains a maximum of 20 keys. For more information, see :ref:`Table 3 <dds_api_0032__teb132a9896b14904b643d3159d0c06eb>`.         |
      +-----------------+-----------------+------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. _dds_api_0032__teb132a9896b14904b643d3159d0c06eb:

   .. table:: **Table 3** tags field data structure description

      +-----------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name            | Mandatory       | Type             | Description                                                                                                                                                                                                                |
      +=================+=================+==================+============================================================================================================================================================================================================================+
      | key             | Yes             | String           | Specifies the tag key. It contains a maximum of 36 Unicode characters. **key** cannot be empty, an empty string, or spaces. Before using **key**, delete spaces of single-byte character (SBC) before and after the value. |
      |                 |                 |                  |                                                                                                                                                                                                                            |
      |                 |                 |                  | .. note::                                                                                                                                                                                                                  |
      |                 |                 |                  |                                                                                                                                                                                                                            |
      |                 |                 |                  |    The character set of this parameter is not verified in the search process.                                                                                                                                              |
      +-----------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | values          | Yes             | Array of strings | Lists the tag values. Each value contains a maximum of 43 Unicode characters and cannot contain spaces. Before using **values**, delete SBC spaces before and after the value.                                             |
      |                 |                 |                  |                                                                                                                                                                                                                            |
      |                 |                 |                  | If the values are null, it indicates querying any value. The values are in OR relationship.                                                                                                                                |
      +-----------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. _dds_api_0032__table86147511997:

   .. table:: **Table 4** matches field description

      +-------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name  | Mandatory | Type   | Description                                                                                                                                                                                                                         |
      +=======+===========+========+=====================================================================================================================================================================================================================================+
      | key   | Yes       | String | Specifies the query criteria. The value can be **instance_name** or **instance_id**, indicating that the query is based on the instance name or instance ID.                                                                        |
      +-------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | value | Yes       | String | Specifies the name or ID of the DB instance to be matched. You can call the API for querying DB instances to obtain the DB instance name or ID. If you do not have an instance, you can call the API used for creating an instance. |
      +-------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Example request

   POST https://dds.eu-de.otc.t-systems.com/v3/0549b4a43100d4f32f51c01c2fe4acdb/instances/action

   Query specified DB instances by tag.

   .. code-block:: text

      {
        "offset": "100",
        "limit": "100",
        "action": "filter",
        "matches": [
          {
            "key": "instance_name",
            "value": "test-single"
          }
        ],
        "tags": [
          {
            "key": "key1",
            "values": [
              "value1",
              "value2"
            ]
          }
        ]
      }

   Query the total number of resources.

   .. code-block:: text

      {
        "action": "count",
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
        ],
        "matches": [
          {
            "key": "instance_name",
            "value": "test-single"
          },
           {
            "key": "instance_id",
            "value": "958693039f284d6ebfb177375711072ein02"
          }
        ]
      }

Responses
---------

-  Parameter description

   .. table:: **Table 5** Parameter description

      +-------------+------------------+----------------------------------------------------------------------------------------------------+
      | Name        | Type             | Description                                                                                        |
      +=============+==================+====================================================================================================+
      | instances   | Array of objects | Indicates the instance list. For details, see :ref:`Table 6 <dds_api_0032__table172571623182113>`. |
      +-------------+------------------+----------------------------------------------------------------------------------------------------+
      | total_count | Integer          | Indicates the total number of queried records.                                                     |
      +-------------+------------------+----------------------------------------------------------------------------------------------------+

   .. _dds_api_0032__table172571623182113:

   .. table:: **Table 6** instance field data structure description

      +---------------+------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name          | Type             | Description                                                                                                                                                                     |
      +===============+==================+=================================================================================================================================================================================+
      | instance_id   | String           | Indicates the instance ID, which can be obtained by calling the API for querying instances. If you do not have an instance, you can call the API used for creating an instance. |
      +---------------+------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | instance_name | String           | Indicates the DB instance name.                                                                                                                                                 |
      +---------------+------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | tags          | Array of objects | Indicates the tag list. If there is no tag in the list, **tags** is taken as an empty array. For more information, see :ref:`Table 7 <dds_api_0032__table42343062217>`.         |
      +---------------+------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. _dds_api_0032__table42343062217:

   .. table:: **Table 7** tags field data structure description

      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------+
      | Name                  | Type                  | Description                                                                                                     |
      +=======================+=======================+=================================================================================================================+
      | key                   | String                | Indicates the tag key. The value contains 36 Unicode characters and cannot be blank.                            |
      |                       |                       |                                                                                                                 |
      |                       |                       | Character set: 0-9, A-Z, a-z, "_", "-", and "@".                                                                |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------+
      | value                 | String                | Indicates the tag value. The value contains a maximum of 43 Unicode characters and can also be an empty string. |
      |                       |                       |                                                                                                                 |
      |                       |                       | Character set: 0-9, A-Z, a-z, "_", "-", and "@".                                                                |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------+

-  Response example

   1. Return specified DB instances by tag.

   .. code-block:: text

      {
        "instances": [
          {
            "instance_id": "2acbf2223caf3bac3c33c6153423c3ccin02",
            "instance_name": "test-single",
            "tags": [
              {
                "key": "key1",
                "value": "value1"
              },
              {
                "key": "key2",
                "value": "value1"
              }
            ]
          }
        ]
      }

   2. Number of returned records.

   .. code-block:: text

      {
        "total_count": 4
      }

Status Code
-----------

Status Code:200.

For more information, see :ref:`Status Code <dds_status_code>`.

Error Code
----------

For more information, see :ref:`Error Code <dds_error_code>`.
