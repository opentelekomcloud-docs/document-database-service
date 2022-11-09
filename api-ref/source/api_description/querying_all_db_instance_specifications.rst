:original_name: dds_instance_specification.html

.. _dds_instance_specification:

Querying All DB Instance Specifications
=======================================

Function
--------

This API is used to query all DB instance specifications in a specified region.

URI
---

-  URI format

   GET /v3/{project_id}/flavors?region={region}&engine_name={engine_name}

-  Parameter description

   .. table:: **Table 1** Parameter description

      +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name                  | Mandatory             | Description                                                                                                                                                                |
      +=======================+=======================+============================================================================================================================================================================+
      | project_id            | Yes                   | Specifies the project ID of a tenant in a region.                                                                                                                          |
      +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | region                | Yes                   | Specifies the region where the DB instance exists.                                                                                                                         |
      |                       |                       |                                                                                                                                                                            |
      |                       |                       | Valid value:                                                                                                                                                               |
      |                       |                       |                                                                                                                                                                            |
      |                       |                       | The value cannot be empty. For details about how to obtain this parameter value, see `Regions and Endpoints <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__. |
      +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | engine_name           | No                    | Specifies the database type. The value is **DDS-Community**.                                                                                                               |
      +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Requests
--------

-  Request header

   .. note::

      The value of **region** in the following is used as an example.

   .. code-block:: text

      GET https://DDS endpoint/v3/375d8d8fad1f43039e23d3b6c0f60a19/flavors?region=aaa&engine_name=DDS-Community

-  Request body

   N/A

Responses
---------

-  Parameter description

   .. table:: **Table 2** Parameter description

      +---------+------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name    | Type             | Description                                                                                                                                      |
      +=========+==================+==================================================================================================================================================+
      | flavors | Array of objects | Indicates the DB instance specifications information list. For more information, see :ref:`Table 3 <dds_instance_specification__table64140254>`. |
      +---------+------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+

   .. _dds_instance_specification__table64140254:

   .. table:: **Table 3** flavors field data structure description

      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------+
      | Name                  | Type                  | Description                                                                             |
      +=======================+=======================+=========================================================================================+
      | engine_name           | String                | Indicates the engine name.                                                              |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------+
      | type                  | String                | Indicates the node type. DDS contains the following types of nodes:                     |
      |                       |                       |                                                                                         |
      |                       |                       | -  mongos                                                                               |
      |                       |                       | -  shard                                                                                |
      |                       |                       | -  config                                                                               |
      |                       |                       | -  replica                                                                              |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------+
      | vcpus                 | String                | Number of vCPUs.                                                                        |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------+
      | ram                   | String                | Indicates the memory size in gigabyte (GB).                                             |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------+
      | spec_code             | String                | Indicates the resource specifications code.                                             |
      |                       |                       |                                                                                         |
      |                       |                       | Example: dds.mongodb.s2.xlarge.4.shard                                                  |
      |                       |                       |                                                                                         |
      |                       |                       | .. note::                                                                               |
      |                       |                       |                                                                                         |
      |                       |                       |    -  **dds.mongodb**: indicates the DDS service.                                       |
      |                       |                       |    -  **s2.xlarge.4**: indicates the performance specification, which is high memory.   |
      |                       |                       |    -  **shard**: indicates the node type.                                               |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------+
      | az_status             | Object                | Indicates the status of specifications in an AZ. Its value can be any of the following: |
      |                       |                       |                                                                                         |
      |                       |                       | -  normal: indicates that the specifications are on sale.                               |
      |                       |                       | -  unsupported: indicates that the DB instance specifications are not supported.        |
      |                       |                       | -  sellout: indicates the specifications are sold out.                                  |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------+

.. note::

   The value of **az_status** is used as an example.

-  Response example

   .. code-block:: text

      {
         "flavors": [
        {
          "engine_name": "DDS-Community",
          "type": "mongos",
          "vcpus": "1",
          "ram": "4",
          "spec_code": "dds.mongodb.s2.medium.4.mongos",
          "az_status": [
            "eu-de-01": "normal",
            "eu-de-02": "normal",
            "eu-de-03": "normal"
          ]
        },
        {
          "engine_name": "DDS-Community",
          "type": "mongos",
          "vcpus": "2",
          "ram": "8",
          "spec_code": "dds.mongodb.s2.large.4.mongos",
          "az_status": [
            "eu-de-01": "normal",
            "eu-de-02": "normal",
            "eu-de-03": "normal"
          ]
        },
        {
          "engine_name": "DDS-Community",
          "type": "mongos",
          "vcpus": "4",
          "ram": "16",
          "spec_code": "dds.mongodb.s2.xlarge.4.mongos",
          "az_status": [
            "eu-de-01": "normal",
            "eu-de-02": "normal",
            "eu-de-03": "normal"
          ]
        },
        {
          "engine_name": "DDS-Community",
          "type": "mongos",
          "vcpus": "8",
          "ram": "32",
          "spec_code": "dds.mongodb.s2.2xlarge.4.mongos",
          "az_status": [
            "eu-de-01": "normal",
            "eu-de-02": "normal",
            "eu-de-03": "normal"
          ]
        },
        {
          "engine_name": "DDS-Community",
          "type": "mongos",
          "vcpus": "16",
          "ram": "64",
          "spec_code": "dds.mongodb.s2.4xlarge.4.mongos",
          "az_status": [
            "eu-de-01": "normal",
            "eu-de-02": "normal",
            "eu-de-03": "normal"
          ]
        },
        {
          "engine_name": "DDS-Community",
          "type": "shard",
          "vcpus": "1",
          "ram": "4",
          "spec_code": "dds.mongodb.s2.medium.4.shard",
          "az_status": [
            "eu-de-01": "normal",
            "eu-de-02": "normal",
            "eu-de-03": "normal"
          ]
        },
        {
          "engine_name": "DDS-Community",
          "type": "shard",
          "vcpus": "2",
          "ram": "8",
          "spec_code": "dds.mongodb.s2.large.4.shard",
          "az_status": [
            "eu-de-01": "normal",
            "eu-de-02": "normal",
            "eu-de-03": "normal"
          ]
        },
        {
          "engine_name": "DDS-Community",
          "type": "shard",
          "vcpus": "4",
          "ram": "16",
          "spec_code": "dds.mongodb.s2.xlarge.4.shard",
          "az_status": [
            "eu-de-01": "normal",
            "eu-de-02": "normal",
            "eu-de-03": "normal"
          ]
        },
        {
          "engine_name": "DDS-Community",
          "type": "shard",
          "vcpus": "8",
          "ram": "32",
          "spec_code": "dds.mongodb.s2.2xlarge.4.shard",
          "az_status": [
            "eu-de-01": "normal",
            "eu-de-02": "normal",
            "eu-de-03": "normal"
          ]
        },
        {
          "engine_name": "DDS-Community",
          "type": "shard",
          "vcpus": "16",
          "ram": "64",
          "spec_code": "dds.mongodb.s2.4xlarge.4.shard",
          "az_status": [
            "eu-de-01": "normal",
            "eu-de-02": "normal",
            "eu-de-03": "normal"
          ]
        },
        {
          "engine_name": "DDS-Community",
          "type": "config",
          "vcpus": "2",
          "ram": "4",
          "spec_code": "dds.mongodb.s2.large.2.config",
          "az_status": [
            "eu-de-01": "normal",
            "eu-de-02": "normal",
            "eu-de-03": "normal"
          ]
        },
        {
          "engine_name": "DDS-Community",
          "type": "replica",
          "vcpus": "1",
          "ram": "4",
          "spec_code": "dds.mongodb.s2.medium.4.repset",
          "az_status": [
            "eu-de-01": "normal",
            "eu-de-02": "normal",
            "eu-de-03": "normal"
          ]
        },
        {
          "engine_name": "DDS-Community",
          "type": "replica",
          "vcpus": "2",
          "ram": "8",
          "spec_code": "dds.mongodb.s2.large.4.repset",
          "az_status": [
            "eu-de-01": "normal",
            "eu-de-02": "normal",
            "eu-de-03": "normal"
          ]
        },
        {
          "engine_name": "DDS-Community",
          "type": "replica",
          "vcpus": "4",
          "ram": "16",
          "spec_code": "dds.mongodb.s2.xlarge.4.repset",
          "az_status": [
            "eu-de-01": "normal",
            "eu-de-02": "normal",
            "eu-de-03": "normal"
          ]
        },
        {
          "engine_name": "DDS-Community",
          "type": "replica",
          "vcpus": "8",
          "ram": "32",
          "spec_code": "dds.mongodb.s2.2xlarge.4.repset",
          "az_status": [
            "eu-de-01": "normal",
            "eu-de-02": "normal",
            "eu-de-03": "normal"
          ]
        },
        {
          "engine_name": "DDS-Community",
          "type": "replica",
          "vcpus": "16",
          "ram": "64",
          "spec_code": "dds.mongodb.s2.4xlarge.4.repset",
          "az_status": [
            "eu-de-01": "normal",
            "eu-de-02": "normal",
            "eu-de-03": "normal"
          ]
        }
      ]
      }

**Status Code**
---------------

For more information, see :ref:`Status Code <dds_status_code>`.

Error Code
----------

For more information, see :ref:`Error Code <dds_error_code>`.
