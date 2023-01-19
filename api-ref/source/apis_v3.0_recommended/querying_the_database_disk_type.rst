:original_name: dds_api_0039.html

.. _dds_api_0039:

Querying the Database Disk Type
===============================

Function
--------

This API is used to query the database disk type in the current region.

URI
---

-  URI format

   GET https://{Endpoint}/v3/{project_id}/storage-type?engine_name={engine_name}

-  Parameter description

   .. table:: **Table 1** Parameter description

      +-----------------------+-----------------------+---------------------------------------------------+
      | Name                  | Mandatory             | Description                                       |
      +=======================+=======================+===================================================+
      | project_id            | Yes                   | Specifies the project ID of a tenant in a region. |
      +-----------------------+-----------------------+---------------------------------------------------+
      | engine_name           | No                    | Specifies the database type.                      |
      |                       |                       |                                                   |
      |                       |                       | The value is **DDS-Community**.                   |
      +-----------------------+-----------------------+---------------------------------------------------+

Requests
--------

-  Example request

   GET https://dds.eu-de.otc.t-systems.com/v3/0549b4a43100d4f32f51c01c2fe4acdb/storage-type?engine_name=DDS-Community

Responses
---------

-  Parameter description

   .. table:: **Table 2** Parameter description

      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------+
      | Name                  | Type                  | Description                                                                                                                       |
      +=======================+=======================+===================================================================================================================================+
      | storage_type          | Array of objects      | Indicates the database disk information list. For more information, see :ref:`Table 3 <dds_api_0039__table1029958863>`.           |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------+
      | dss_pool_info         | Array of objects      | Indicates the dss_pool specifications information list. For more information, see :ref:`Table 4 <dds_api_0039__table9305198166>`. |
      |                       |                       |                                                                                                                                   |
      |                       |                       | .. note::                                                                                                                         |
      |                       |                       |                                                                                                                                   |
      |                       |                       |    Only Dedicated Cloud (DeC) users are supported.                                                                                |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------+

   .. _dds_api_0039__table1029958863:

   .. table:: **Table 3** storage_type field data structure description

      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------+
      | Name                  | Type                  | Description                                                                             |
      +=======================+=======================+=========================================================================================+
      | name                  | String                | Indicates the storage type. Its value can be:                                           |
      |                       |                       |                                                                                         |
      |                       |                       | **ULTRAHIGH**: indicates the SSD type.                                                  |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------+
      | az_status             | Object                | Indicates the status of specifications in an AZ. Its value can be any of the following: |
      |                       |                       |                                                                                         |
      |                       |                       | -  **normal**: indicates that the specifications are on sale.                           |
      |                       |                       | -  **unsupported**: The disk type is not supported.                                     |
      |                       |                       | -  **sellout**: indicates the specifications are sold out.                              |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------+

   .. _dds_api_0039__table9305198166:

   .. table:: **Table 4** dss_pool_info field data structure description

      +-----------------------+-----------------------+-----------------------------------------------------------------------+
      | Name                  | Type                  | Description                                                           |
      +=======================+=======================+=======================================================================+
      | az_name               | String                | Indicates the name of the AZ where the dss_pool is located.           |
      +-----------------------+-----------------------+-----------------------------------------------------------------------+
      | free_capacity_gb      | String                | Indicates the available capacity of DSS.                              |
      |                       |                       |                                                                       |
      |                       |                       | Unit: GB                                                              |
      +-----------------------+-----------------------+-----------------------------------------------------------------------+
      | dss_pool_volume_type  | String                | Indicates the disk type of DSS storage pool.                          |
      +-----------------------+-----------------------+-----------------------------------------------------------------------+
      | dss_pool_id           | String                | Indicates the DSS pool ID.                                            |
      +-----------------------+-----------------------+-----------------------------------------------------------------------+
      | dss_pool_status       | String                | Indicates the dss_pool status. Its value can be any of the following: |
      |                       |                       |                                                                       |
      |                       |                       | -  **available**                                                      |
      |                       |                       | -  **deploying**                                                      |
      |                       |                       | -  **enlarging**                                                      |
      +-----------------------+-----------------------+-----------------------------------------------------------------------+

   .. note::

      The value of **az_status** is used as an example.

-  Response example

   .. code-block:: text

      {
          "storage_type": [
              {
                   "name": "ULTRAHIGH",
                   "az_status": {
                       "eu-de-01": "normal",
                       "eu-de-02": "normal",
                       "eu-de-03": "unsupported"
                    }
               }
          ],
          "dsspool_info": []
      }

Status Code
-----------

Status Code:200.

For more information, see :ref:`Status Code <dds_status_code>`.

Error Code
----------

For more information, see :ref:`Error Code <dds_error_code>`.
