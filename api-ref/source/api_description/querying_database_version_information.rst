:original_name: dds_database_version.html

.. _dds_database_version:

Querying Database Version Information
=====================================

Function
--------

This API is used to obtain database version information about a specified type of a DB instance.

URI
---

-  URI format

   GET /v3/{project_id}/datastores/{datastore_name}/versions

-  Parameter description

   .. table:: **Table 1** Parameter description

      +----------------+-----------+--------------------------------------------------------------------------------------------------+
      | Name           | Mandatory | Description                                                                                      |
      +================+===========+==================================================================================================+
      | project_id     | Yes       | Specifies the project ID of a tenant in a region.                                                |
      +----------------+-----------+--------------------------------------------------------------------------------------------------+
      | datastore_name | Yes       | Specifies the database type. DDS Community Edition is supported. The value is **DDS-Community**. |
      +----------------+-----------+--------------------------------------------------------------------------------------------------+

Requests
--------

-  Request header

   .. code-block:: text

      GET https://DDS endpoint/v3/{project_id}/datastores/{datastore_name}/versions

-  Request body

   N/A

Responses
---------

-  Parameter description

   .. table:: **Table 2** Parameter description

      +----------+------------------+--------------------------------------------------------------------------------+
      | Name     | Type             | Description                                                                    |
      +==========+==================+================================================================================+
      | versions | Array of strings | Indicates the database version. Currently, versions 3.2 and 3.4 are supported. |
      +----------+------------------+--------------------------------------------------------------------------------+

-  Response example

   .. code-block:: text

      {
          "versions": [
              "3.2",
              "3.4"
          ]
      }

**Status Code**
---------------

For more information, see :ref:`Status Code <dds_status_code>`.

Error Code
----------

For more information, see :ref:`Error Code <dds_error_code>`.
