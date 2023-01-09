:original_name: dds_api_0096.html

.. _dds_api_0096:

Obtaining Links for Downloading Error Logs
==========================================

Function
--------

This API is used to obtain the download link of error logs.

Constraints
-----------

The link for downloading error logs is valid within 15 minutes after being updated.

URI
---

-  URI format

   POST https://{Endpoint}/v3/{project_id}/instances/{instance_id}/errorlog-download

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

   +-----------------+-----------------+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Name            | Mandatory       | Type             | Description                                                                                                                                                                                                            |
   +=================+=================+==================+========================================================================================================================================================================================================================+
   | file_name_list  | No              | Array of strings | Specifies the list of the names of the files to be downloaded.                                                                                                                                                         |
   |                 |                 |                  |                                                                                                                                                                                                                        |
   |                 |                 |                  | .. note::                                                                                                                                                                                                              |
   |                 |                 |                  |                                                                                                                                                                                                                        |
   |                 |                 |                  |    You can upload an empty request body to export error logs of all nodes and return all file names and download links. You can also specify the name of the file to be downloaded based on the preceding information. |
   +-----------------+-----------------+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | node_id_list    | No              | Array of strings | Specifies the node ID list. If this parameter is left blank, all nodes in the instance can be queried.                                                                                                                 |
   |                 |                 |                  |                                                                                                                                                                                                                        |
   |                 |                 |                  | For details, see the **id** value in the **nodes data structure** table in section "Querying Instances" in the *DDS API Reference*.                                                                                    |
   |                 |                 |                  |                                                                                                                                                                                                                        |
   |                 |                 |                  | Nodes that can be queried:                                                                                                                                                                                             |
   |                 |                 |                  |                                                                                                                                                                                                                        |
   |                 |                 |                  | -  mongos, shard, and config nodes in a cluster.                                                                                                                                                                       |
   |                 |                 |                  | -  All nodes in a replica set or single node instance.                                                                                                                                                                 |
   +-----------------+-----------------+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Request example

   1. If the body parameter is not specified, the error log file links of all instance nodes are returned.

   POST https://dds.eu-de.otc.t-systems.com/v3/0483b6b16e954cb88930a360d2c4e663/instances/6ade8143870047b8999aba8f1891b48ein02/errorlog-download

   .. code-block:: text

      {
      }

   2. If the body parameter is specified, the error log file link of the current node is returned.

   POST https://dds.eu-de.otc.t-systems.com/v3/0483b6b16e954cb88930a360d2c4e663/instances/6ade8143870047b8999aba8f1891b48ein02/errorlog-download

   .. code-block:: text

      {
        "file_name_list": [
          "0541c9f81e80d2201fccc00b92ad6ec0_052f8a12dfed43fbb27c2020e3c3c507no02_errorlog_20201117104809"
        ],
        "node_id_list": [
          "052f8a12dfed43fbb27c2020e3c3c507no02"
        ]
      }

Responses
---------

-  Parameter description

   .. table:: **Table 2** Parameter description

      +-----------------------+-----------------------+-------------------------------------------------------------------------------------+
      | Name                  | Type                  | Description                                                                         |
      +=======================+=======================+=====================================================================================+
      | list                  | List                  | Indicates the list of error log download links.                                     |
      |                       |                       |                                                                                     |
      |                       |                       | For details, see :ref:`Table 3 <dds_api_0096__table17888141175915>`.                |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------+
      | status                | String                | Indicates the status of the error log download link.                                |
      |                       |                       |                                                                                     |
      |                       |                       | -  **FINISH**: The download link has been generated.                                |
      |                       |                       | -  **CREATING**: A file is being generated and the download link is to be prepared. |
      |                       |                       | -  **FAILED**: Log files fail to be prepared.                                       |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------+
      | count                 | Integer               | Indicates the number of error log links.                                            |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------+

   .. _dds_api_0096__table17888141175915:

   .. table:: **Table 3** list field data structure description

      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------+
      | Name                  | Type                  | Description                                                                                                                                   |
      +=======================+=======================+===============================================================================================================================================+
      | node_name             | String                | Indicates the node name.                                                                                                                      |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------+
      | file_name             | String                | Indicates the name of the generated file for downloading error logs.                                                                          |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------+
      | status                | String                | Indicates the status of the current link.                                                                                                     |
      |                       |                       |                                                                                                                                               |
      |                       |                       | -  **SUCCESS**: The download link has been generated.                                                                                         |
      |                       |                       | -  **EXPORTING**: A file is being generated and the download link is to be prepared.                                                          |
      |                       |                       | -  **FAILED**: Log files fail to be prepared.                                                                                                 |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------+
      | file_size             | String                | Indicates the file size in KB.                                                                                                                |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------+
      | file_link             | String                | Indicates the download link.                                                                                                                  |
      |                       |                       |                                                                                                                                               |
      |                       |                       | .. note::                                                                                                                                     |
      |                       |                       |                                                                                                                                               |
      |                       |                       |    The download link is valid within 15 minutes after being updated. After the update time expires, the download link will be obtained again. |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------+
      | update_at             | Long                  | Indicates the update time.                                                                                                                    |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------+

-  Response example

   1. If the body parameter is not specified, the following information is returned:

   .. code-block:: text

      {
          "list": [
              {
                  "node_name": "dds-4ff4_replica_node_1",
                  "file_name": "88f9e7914ab149049bbb57bc83b3f296_599fd21891264a348822db4c6fd7e6f7no02_errorlog_20221028152158",
                  "status": "SUCCESS",
                  "file_size": "0",
                  "file_link": "https://obs.cn-datebase-ssh.myhuaweicloud.com:443/dbsbucket.cn.datebase.ssh.a5b2d082b6264f249283eed2b612e934/88f9e7914ab149049bbb57bc83b3f296_599fd21891264a348822db4c6fd7e6f7no02_errorlog_20221028152158?AWSAccessKeyId=IUMLNBNX6IDB9ERZTLBR&Expires=1666942048&response-cache-control=no-cache%2Cno-store&Signature=Ljs5eeelvgzI86sKd1OPbeMjonQ%3D",
                  "updated_at": 1666941725839
              },
              {
                  "node_name": "dds-4ff4_replica_node_2",
                  "file_name": "88f9e7914ab149049bbb57bc83b3f296_8fa3da0256e14f8ab6ca118463f308bfno02_errorlog_20221028152158",
                  "status": "SUCCESS",
                  "file_size": "3.59",
                  "file_link": "https://obs.cn-datebase-ssh.myhuaweicloud.com:443/dbsbucket.cn.datebase.ssh.a5b2d082b6264f249283eed2b612e934/88f9e7914ab149049bbb57bc83b3f296_8fa3da0256e14f8ab6ca118463f308bfno02_errorlog_20221028152158?AWSAccessKeyId=IUMLNBNX6IDB9ERZTLBR&Expires=1666942048&response-cache-control=no-cache%2Cno-store&Signature=6RTLq%2BmyGhzziTBGIK62L9KrWLU%3D",
                  "updated_at": 1666941726237
              },
              {
                  "node_name": "dds-4ff4_replica_node_3",
                  "file_name": "88f9e7914ab149049bbb57bc83b3f296_af6b1afbbc7b4453a2cfb5bcc1d0a587no02_errorlog_20221028152158",
                  "status": "SUCCESS",
                  "file_size": "0",
                  "file_link": "https://obs.cn-datebase-ssh.myhuaweicloud.com:443/dbsbucket.cn.datebase.ssh.a5b2d082b6264f249283eed2b612e934/88f9e7914ab149049bbb57bc83b3f296_af6b1afbbc7b4453a2cfb5bcc1d0a587no02_errorlog_20221028152158?AWSAccessKeyId=IUMLNBNX6IDB9ERZTLBR&Expires=1666942048&response-cache-control=no-cache%2Cno-store&Signature=W0ZB%2BwBEwM1DoDKZEPhSVl%2BDT%2Bo%3D",
                  "updated_at": 1666941738832
              }
          ],
          "status": "FINISH",
          "count": 3
      }

   2. If the body parameter is specified, the following information is returned:

   .. code-block:: text

      {
        "list": [
          {
            "node_name": "node_1",
            "file_name": "054bc9c1f680d55c1f36c006e5a9f67b_errorlog_download_20200515080614589",
            "status": "SUCCESS",
            "file_size": "0",
            "file_link": "https://rdsbucket.opxxx.svc.rds.xxxxx.cnxianhz1.ur.obs.cn-xianhz-1.myhuaweicloud.com:443/054bc9c1f680d55c1f36c006e5a9f67b_errorlog_download_20200515080614589?AWSAccessKeyId=1BQ38TBCQHAVQXBUMUTC&Expires=1589530200&response-cache-control=no-cache%2Cno-store&Signature=Fgi4%2BLOJ9frAXyOkz5hRoW5O%2BUM%3D",
            " updated_at ": 1589529991385
          }
        ],
        "status": "FINISH",
        "count": 1
      }

   3. If the download link expires, you will receive the following response:

   .. code-block:: text

      {
          "list": [
              {
                  "node_name": "dds-4ff4_replica_node_1",
                  "file_name": "88f9e7914ab149049bbb57bc83b3f296_599fd21891264a348822db4c6fd7e6f7no02_errorlog_20221028152158",
                  "status": "EXPORTING",
                  "file_size": null,
                  "file_link": null,
                  "updated_at": 1666941725839
              },
              {
                  "node_name": "dds-4ff4_replica_node_2",
                  "file_name": "88f9e7914ab149049bbb57bc83b3f296_8fa3da0256e14f8ab6ca118463f308bfno02_errorlog_20221028152158",
                  "status": "EXPORTING",
                  "file_size": null,
                  "file_link": null,
                  "updated_at": 1666941726237
              },
              {
                  "node_name": "dds-4ff4_replica_node_3",
                  "file_name": "88f9e7914ab149049bbb57bc83b3f296_af6b1afbbc7b4453a2cfb5bcc1d0a587no02_errorlog_20221028152158",
                  "status": "EXPORTING",
                  "file_size": null,
                  "file_link": null,
                  "updated_at": 1666941738832
              }
          ],
          "status": "CREATING",
          "count": 3
      }

Status Code
-----------

Status Code:200.

For more information, see :ref:`Status Code <dds_status_code>`.

Error Code
----------

For more information, see :ref:`Error Code <dds_error_code>`.
