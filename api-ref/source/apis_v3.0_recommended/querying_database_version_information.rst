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

   GET https://{Endpoint}/v3/{project_id}/datastores/{datastore_name}/versions

-  Parameter description

   .. table:: **Table 1** Parameter description

      +----------------+-----------+--------------------------------------------------------------+
      | Name           | Mandatory | Description                                                  |
      +================+===========+==============================================================+
      | project_id     | Yes       | Specifies the project ID of a tenant in a region.            |
      +----------------+-----------+--------------------------------------------------------------+
      | datastore_name | Yes       | Specifies the database type. The value is **DDS-Community**. |
      +----------------+-----------+--------------------------------------------------------------+

Requests
--------

-  Example request

   GET https://dds.eu-de.otc.t-systems.com/v3/0549b4a43100d4f32f51c01c2fe4acdb/datastores/DDS-Community/versions

Responses
---------

-  Parameter description

   .. table:: **Table 2** Parameter description

      +----------+------------------+-------------------------------------------------------------------------------------------+
      | Name     | Type             | Description                                                                               |
      +==========+==================+===========================================================================================+
      | versions | Array of strings | Indicates the database version. Currently, versions 3.2, 3.4, 4.0, and 4.2 are supported. |
      +----------+------------------+-------------------------------------------------------------------------------------------+

-  Response example

   .. code-block:: text

      {
          "versions": [
              "3.2",
              "3.4",
              "4.0",
              "4.2"
          ]
      }

Status Code
-----------

Status Code:200.

For more information, see :ref:`Status Code <dds_status_code>`.

Error Code
----------

For more information, see :ref:`Error Code <dds_error_code>`.
