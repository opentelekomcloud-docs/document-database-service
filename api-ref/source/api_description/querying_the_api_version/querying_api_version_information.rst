:original_name: dds_api_0019.html

.. _dds_api_0019:

Querying API Version Information
================================

Function
--------

This API is used to query the specified API version.

URI
---

URI format

GET /v3

Requests
--------

-  Request header

   .. code-block:: text

      GET https://DDS endpoint/v3

-  Request body

   N/A

Responses
---------

-  Parameter description

   .. table:: **Table 1** Parameter description

      +---------+--------+---------------------------------------------------------------------------------------------------------------------------------------+
      | Name    | Type   | Description                                                                                                                           |
      +=========+========+=======================================================================================================================================+
      | version | Object | Indicates the list of detailed API version information. For more information, see :ref:`Table 2 <dds_api_0019__table57914909154838>`. |
      +---------+--------+---------------------------------------------------------------------------------------------------------------------------------------+

   .. _dds_api_0019__table57914909154838:

   .. table:: **Table 2** **version** field data structure description

      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------+
      | Name                  | Type                  | Description                                                                                                             |
      +=======================+=======================+=========================================================================================================================+
      | id                    | String                | Indicates the API version.                                                                                              |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------+
      | links                 | Array of objects      | Indicates the API version link information. For more information, see :ref:`Table 3 <dds_api_0019__table630875915440>`. |
      |                       |                       |                                                                                                                         |
      |                       |                       | .. note::                                                                                                               |
      |                       |                       |                                                                                                                         |
      |                       |                       |    If the version is **v3**, the value is **[]**.                                                                       |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------+
      | status                | String                | Indicates the version status. The value **CURRENT** indicates that the version has been released.                       |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------+
      | version               | String                | Indicates the subversion of the API version.                                                                            |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------+
      | min_version           | String                | Indicates the minimum API version.                                                                                      |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------+
      | updated               | String                | Indicates the version update time.                                                                                      |
      |                       |                       |                                                                                                                         |
      |                       |                       | The format is yyyy-mm-ddThh:mm:ssZ.                                                                                     |
      |                       |                       |                                                                                                                         |
      |                       |                       | **T** is the separator between the calendar and the hourly notation of time. **Z** indicates the UTC.                   |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------+

   .. _dds_api_0019__table630875915440:

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
          "version": {
              "id": "v3",
              "links": [],
              "status": "CURRENT",
              "version": "",
              "min_version": "",
              "updated": "2017-02-07T17:34:02Z"
          }
      }

**Status Code**
---------------

For more information, see :ref:`Status Code <dds_status_code>`.

Error Code
----------

For more information, see :ref:`Error Code <dds_error_code>`.
