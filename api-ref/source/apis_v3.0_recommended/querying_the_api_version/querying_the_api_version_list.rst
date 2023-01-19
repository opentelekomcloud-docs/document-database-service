:original_name: dds_api_0018.html

.. _dds_api_0018:

Querying the API Version List
=============================

Function
--------

This API is used to query the currently supported API version list.

URI
---

-  URI format

   GET https://{Endpoint}/

-  Parameter description

   N/A

Requests
--------

None

Responses
---------

-  Parameter description

   .. table:: **Table 1** Parameter description

      +----------+------------------+---------------------------------------------------------------------------------------------------------------------------------------+
      | Name     | Type             | Description                                                                                                                           |
      +==========+==================+=======================================================================================================================================+
      | versions | Array of objects | Indicates the list of detailed API version information. For more information, see :ref:`Table 2 <dds_api_0018__table37479565104653>`. |
      +----------+------------------+---------------------------------------------------------------------------------------------------------------------------------------+

   .. _dds_api_0018__table37479565104653:

   .. table:: **Table 2** versions field data structure description

      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------+
      | Name                  | Type                  | Description                                                                                                     |
      +=======================+=======================+=================================================================================================================+
      | id                    | String                | Indicates the API version.                                                                                      |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------+
      | links                 | Array of objects      | Indicates the API link information. For more information, see :ref:`Table 3 <dds_api_0018__table630875915440>`. |
      |                       |                       |                                                                                                                 |
      |                       |                       | .. note::                                                                                                       |
      |                       |                       |                                                                                                                 |
      |                       |                       |    If the version is **v3**, the value is **[]**.                                                               |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------+
      | status                | String                | Indicates the version status.                                                                                   |
      |                       |                       |                                                                                                                 |
      |                       |                       | The value CURRENT indicates that the version has been released.                                                 |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------+
      | version               | String                | Indicates the subversion of the API version.                                                                    |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------+
      | min_version           | String                | Indicates the minimum API version.                                                                              |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------+
      | updated               | String                | Indicates the version update time.                                                                              |
      |                       |                       |                                                                                                                 |
      |                       |                       | The format is yyyy-mm-ddThh:mm:ssZ.                                                                             |
      |                       |                       |                                                                                                                 |
      |                       |                       | **T** is the separator between the calendar and the hourly notation of time. **Z** indicates the UTC.           |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------+

   .. _dds_api_0018__table630875915440:

   .. table:: **Table 3** links field data structure description

      ==== ====== ===========================================================
      Name Type   Description
      ==== ====== ===========================================================
      href String Indicates the API URL and the value is **""**.
      rel  String Its value is **self**, indicating that URL is a local link.
      ==== ====== ===========================================================

-  Response example

   .. code-block:: text

      {
          "versions": [
              {
                  "id": "v3",
                  "links": [],
                  "status": "CURRENT",
                  "version": "",
                  "min_version": "",
                  "updated": "2017-02-07T17:34:02Z"
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
