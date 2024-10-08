:original_name: dds_instance_specification.html

.. _dds_instance_specification:

Querying Database Specifications
================================

Function
--------

This API is used to query all instance specifications under a specified condition.

URI
---

-  URI format

   GET https://{Endpoint}/v3.1/{project_id}/flavors?engine_name={engine_name}&engine_version={engine_version}&offset={offset}&limit={limit}

-  Parameter description

   .. table:: **Table 1** Parameter description

      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name                  | Mandatory             | Description                                                                                                                                                                    |
      +=======================+=======================+================================================================================================================================================================================+
      | project_id            | Yes                   | Specifies the project ID of a tenant in a region.                                                                                                                              |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | engine_name           | No                    | Specifies the database type. The value is **DDS-Community**.                                                                                                                   |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | engine_version        | No                    | DB version number. To obtain this value, see :ref:`Querying Database Version Information <dds_database_version>`.                                                              |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | offset                | No                    | Index offset.                                                                                                                                                                  |
      |                       |                       |                                                                                                                                                                                |
      |                       |                       | -  If offset is set to *N*, the resource query starts from the *N+1* piece of data. The default value is **0**, indicating that the query starts from the first piece of data. |
      |                       |                       | -  The value must be a positive integer.                                                                                                                                       |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | limit                 | No                    | Maximum number of specifications that can be queried                                                                                                                           |
      |                       |                       |                                                                                                                                                                                |
      |                       |                       | -  Value range: 1-100                                                                                                                                                          |
      |                       |                       | -  If this parameter is not transferred, the first 100 pieces of specification information can be queried by default.                                                          |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Requests
--------

-  Example request

   GET https://dds.eu-de.otc.t-systems.com/v3.1/0549b4a43100d4f32f51c01c2fe4acdb/flavors?engine_name=DDS-Community&engine_version=3.4&offset=1&limit=20

Responses
---------

-  Parameter description

   .. table:: **Table 2** Parameter description

      +-------------+------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name        | Type             | Description                                                                                                                                      |
      +=============+==================+==================================================================================================================================================+
      | flavors     | Array of objects | Indicates the DB instance specifications information list. For more information, see :ref:`Table 3 <dds_instance_specification__table64140254>`. |
      +-------------+------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
      | total_count | Integer          | Total number of records                                                                                                                          |
      +-------------+------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+

   .. _dds_instance_specification__table64140254:

   .. table:: **Table 3** flavors field data structure description

      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name                  | Type                  | Description                                                                                                                                                                                   |
      +=======================+=======================+===============================================================================================================================================================================================+
      | engine_name           | String                | Indicates the engine name.                                                                                                                                                                    |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | type                  | String                | Indicates the node type. DDS contains the following types of nodes:                                                                                                                           |
      |                       |                       |                                                                                                                                                                                               |
      |                       |                       | -  mongos                                                                                                                                                                                     |
      |                       |                       | -  shard                                                                                                                                                                                      |
      |                       |                       | -  config                                                                                                                                                                                     |
      |                       |                       | -  replica                                                                                                                                                                                    |
      |                       |                       | -  single                                                                                                                                                                                     |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | vcpus                 | String                | Indicates the number of vCPUs.                                                                                                                                                                |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | ram                   | String                | Indicates the memory size in gigabyte (GB).                                                                                                                                                   |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | spec_code             | String                | Indicates the resource specification code.                                                                                                                                                    |
      |                       |                       |                                                                                                                                                                                               |
      |                       |                       | Example: dds.mongodb.s2.xlarge.4.shard                                                                                                                                                        |
      |                       |                       |                                                                                                                                                                                               |
      |                       |                       | .. note::                                                                                                                                                                                     |
      |                       |                       |                                                                                                                                                                                               |
      |                       |                       |    -  **dds.mongodb**: indicates the DDS service.                                                                                                                                             |
      |                       |                       |    -  **s2.xlarge.4**: indicates the performance specification, which is high memory.                                                                                                         |
      |                       |                       |    -  **shard**: indicates the node type.                                                                                                                                                     |
      |                       |                       |    -  When querying the specifications, check whether the specifications are of the same series. The specification series includes general-purpose (s6), enhanced (c3), and enhanced II (c6). |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | az_status             | Object                | Indicates the status of specifications in an AZ. Its value can be any of the following:                                                                                                       |
      |                       |                       |                                                                                                                                                                                               |
      |                       |                       | -  **normal**: indicates that the specifications are on sale.                                                                                                                                 |
      |                       |                       | -  **unsupported**: indicates that the DB instance specifications are not supported.                                                                                                          |
      |                       |                       | -  **sellout**: indicates the specifications are sold out.                                                                                                                                    |
      |                       |                       |                                                                                                                                                                                               |
      |                       |                       | .. note::                                                                                                                                                                                     |
      |                       |                       |                                                                                                                                                                                               |
      |                       |                       |    ReplicaSet flavors supports cross AZ creation in case "eu-de-01,eu-de-02,eu-de-03": "normal".                                                                                              |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | engine_versions       | Array of strings      | Database versions                                                                                                                                                                             |
      |                       |                       |                                                                                                                                                                                               |
      |                       |                       | For example, DDS mongos node, {"3.4", "4.0", "4.2", "4.4"}                                                                                                                                    |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. note::

   The value of **az_status** is used as an example.

-  Response example

   .. code-block:: text

      {
          "total_count":21,
          "flavors": [
              {
                  "engine_name": "DDS-Community",
                  "type": "mongos",
                  "vcpus": "1",
                  "ram": "4",
                  "spec_code": "dds.mongodb.s2.medium.4.mongos",
                  "engine_versions":["3.4","4.0"],
                  "az_status": {
                      "eu-de-01": "normal",
                      "eu-de-02": "normal",
                      "eu-de-03": "normal"
                  }
              },
              {
                  "engine_name": "DDS-Community",
                  "type": "mongos",
                  "vcpus": "2",
                  "ram": "8",
                  "spec_code": "dds.mongodb.s2.large.4.mongos",
                  "engine_versions":["3.4","4.0"],
                  "az_status": {
                      "eu-de-01": "normal",
                      "eu-de-02": "normal",
                      "eu-de-03": "normal"
                  }
              },
              {
                  "engine_name": "DDS-Community",
                  "type": "mongos",
                  "vcpus": "4",
                  "ram": "16",
                  "spec_code": "dds.mongodb.s2.xlarge.4.mongos",
                  "engine_versions":["3.4","4.0"],
                  "az_status": {
                      "eu-de-01": "normal",
                      "eu-de-02": "normal",
                      "eu-de-03": "normal"
                  }
              },
              {
                  "engine_name": "DDS-Community",
                  "type": "mongos",
                  "vcpus": "8",
                  "ram": "32",
                  "spec_code": "dds.mongodb.s2.2xlarge.4.mongos",
                  "engine_versions":["3.4","4.0"],
                  "az_status": {
                      "eu-de-01": "normal",
                      "eu-de-02": "normal",
                      "eu-de-03": "normal"
                  }
              },
              {
                  "engine_name": "DDS-Community",
                  "type": "mongos",
                  "vcpus": "16",
                  "ram": "64",
                  "spec_code": "dds.mongodb.s2.4xlarge.4.mongos",
                  "engine_versions":["3.4","4.0"],
                  "az_status": {
                      "eu-de-01": "normal",
                      "eu-de-02": "normal",
                      "eu-de-03": "normal"
                  }
              },
              {
                  "engine_name": "DDS-Community",
                  "type": "shard",
                  "vcpus": "1",
                  "ram": "4",
                  "spec_code": "dds.mongodb.s2.medium.4.shard",
                  "engine_versions":["3.4","4.0"],
                  "az_status": {
                      "eu-de-01": "normal",
                      "eu-de-02": "normal",
                      "eu-de-03": "normal"
                  }
              },
              {
                  "engine_name": "DDS-Community",
                  "type": "shard",
                  "vcpus": "2",
                  "ram": "8",
                  "spec_code": "dds.mongodb.s2.large.4.shard",
                  "engine_versions":["3.4","4.0"],
                  "az_status": {
                      "eu-de-01": "normal",
                      "eu-de-02": "normal",
                      "eu-de-03": "normal"
                  }
              },
              {
                  "engine_name": "DDS-Community",
                  "type": "shard",
                  "vcpus": "4",
                  "ram": "16",
                  "spec_code": "dds.mongodb.s2.xlarge.4.shard",
                  "engine_versions":["3.4","4.0"],
                  "az_status": {
                      "eu-de-01": "normal",
                      "eu-de-02": "normal",
                      "eu-de-03": "normal"
                  }
              },
              {
                  "engine_name": "DDS-Community",
                  "type": "shard",
                  "vcpus": "8",
                  "ram": "32",
                  "spec_code": "dds.mongodb.s2.2xlarge.4.shard",
                  "engine_versions":["3.4","4.0"],
                  "az_status": {
                      "eu-de-01": "normal",
                      "eu-de-02": "normal",
                      "eu-de-03": "normal"
                  }
              },
              {
                  "engine_name": "DDS-Community",
                  "type": "shard",
                  "vcpus": "16",
                  "ram": "64",
                  "spec_code": "dds.mongodb.s2.4xlarge.4.shard",
                  "engine_versions":["3.4","4.0"],
                  "az_status": {
                      "eu-de-01": "normal",
                      "eu-de-02": "normal",
                      "eu-de-03": "normal"
                  }
              },
              {
                  "engine_name": "DDS-Community",
                  "type": "config",
                  "vcpus": "2",
                  "ram": "4",
                  "spec_code": "dds.mongodb.s2.large.2.config",
                  "engine_versions":["3.4","4.0"],
                  "az_status": {
                      "eu-de-01": "normal",
                      "eu-de-02": "normal",
                      "eu-de-03": "normal"
                  }
              },
              {
                  "engine_name": "DDS-Community",
                  "type": "replica",
                  "vcpus": "1",
                  "ram": "4",
                  "spec_code": "dds.mongodb.s2.medium.4.repset",
                  "engine_versions":["3.4","4.0"],
                  "az_status": {
                      "eu-de-01": "normal",
                      "eu-de-02": "normal",
                      "eu-de-03": "normal",
                      "eu-de-01,eu-de-02,eu-de-03": "normal"
                  }
              },
              {
                  "engine_name": "DDS-Community",
                  "type": "replica",
                  "vcpus": "2",
                  "ram": "8",
                  "spec_code": "dds.mongodb.s2.large.4.repset",
                  "engine_versions":["3.4","4.0"],
                  "az_status": {
                      "eu-de-01": "normal",
                      "eu-de-02": "normal",
                      "eu-de-03": "normal",
                      "eu-de-01,eu-de-02,eu-de-03": "normal"
                  }
              },
              {
                  "engine_name": "DDS-Community",
                  "type": "replica",
                  "vcpus": "4",
                  "ram": "16",
                  "spec_code": "dds.mongodb.s2.xlarge.4.repset",
                  "engine_versions":["3.4","4.0"],
                  "az_status": {
                      "eu-de-01": "normal",
                      "eu-de-02": "normal",
                      "eu-de-03": "normal",
                      "eu-de-01,eu-de-02,eu-de-03": "normal"
                  }
              },
              {
                  "engine_name": "DDS-Community",
                  "type": "replica",
                  "vcpus": "8",
                  "ram": "32",
                  "spec_code": "dds.mongodb.s2.2xlarge.4.repset",
                  "engine_versions":["3.4","4.0"],
                  "az_status": {
                      "eu-de-01": "normal",
                      "eu-de-02": "normal",
                      "eu-de-03": "normal",
                      "eu-de-01,eu-de-02,eu-de-03": "normal"
                  }
              },
              {
                  "engine_name": "DDS-Community",
                  "type": "replica",
                  "vcpus": "16",
                  "ram": "64",
                  "spec_code": "dds.mongodb.s2.4xlarge.4.repset",
                  "engine_versions":["3.4","4.0"],
                  "az_status": {
                      "eu-de-01": "normal",
                      "eu-de-02": "normal",
                      "eu-de-03": "normal",
                      "eu-de-01,eu-de-02,eu-de-03": "normal"
                  }
              },
              {
                  "engine_name": "DDS-Community",
                  "type": "single",
                  "vcpus": "1",
                  "ram": "4",
                  "spec_code": "dds.mongodb.s2.medium.4.single",
                  "engine_versions":["3.4","4.0"],
                  "az_status": {
                      "eu-de-01": "normal",
                      "eu-de-02": "normal",
                      "eu-de-03": "normal"
                  }
              },
              {
                  "engine_name": "DDS-Community",
                  "type": "single",
                  "vcpus": "2",
                  "ram": "8",
                  "spec_code": "dds.mongodb.s2.large.4.single",
                  "engine_versions":["3.4","4.0"],
                  "az_status": {
                      "eu-de-01": "normal",
                      "eu-de-02": "normal",
                      "eu-de-03": "normal"
                  }
              },
              {
                  "engine_name": "DDS-Community",
                  "type": "single",
                  "vcpus": "4",
                  "ram": "16",
                  "spec_code": "dds.mongodb.s2.xlarge.4.single",
                  "engine_versions":["3.4","4.0"],
                  "az_status": {
                      "eu-de-01": "normal",
                      "eu-de-02": "normal",
                      "eu-de-03": "normal"
                  }
              },
              {
                  "engine_name": "DDS-Community",
                  "type": "single",
                  "vcpus": "8",
                  "ram": "32",
                  "spec_code": "dds.mongodb.s2.2xlarge.4.single",
                  "engine_versions":["3.4","4.0"],
                  "az_status": {
                      "eu-de-01": "normal",
                      "eu-de-02": "normal",
                      "eu-de-03": "normal"
                  }
              },
              {
                  "engine_name": "DDS-Community",
                  "type": "single",
                  "vcpus": "16",
                  "ram": "64",
                  "spec_code": "dds.mongodb.s2.4xlarge.4.single",
                  "engine_versions":["3.4","4.0"],
                  "az_status": {
                      "eu-de-01": "normal",
                      "eu-de-02": "normal",
                      "eu-de-03": "normal"
                  }
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
