:original_name: dds_api_0017.html

.. _dds_api_0017:

Example
=======

This section describes how to create a cluster instance by calling APIs.

.. note::

   The validity period of a token obtained from IAM is 24 hours. If you want to use a token for authentication, cache it to avoid frequent IAM API calling.

Involved APIs
-------------

If you use a token for authentication, you must obtain the user's token and add **X-Auth-Token** to the request message header of the service API when making an API call.

-  API for obtaining tokens from IAM
-  Creating a DDS DB instance using an open API

Procedure
---------

#. Obtain the token by following instructions in section :ref:`Authentication <dds_api_0010>`.

#. Send **POST https://DDS endpoint/v3/{project_id}/instances**.

#. Add **X-Auth-Token** to the request header.

#. Specify the following parameters in the request body:

   .. note::

      The values of **region** and **availability_zone** are used as examples.

      For details about the API used for creating DB instances, see :ref:`Creating a DB Instance <dds_api_0020>`.

   .. code-block:: text

      {
        "name": "test-cluster", //DB instance name
        "datastore": {
          "type": "DDS-Community", // Database type and version
           "version": "4.0", //Database version
           "storage_engine": "wiredTiger" //Storage engine
        },
          "region": "aaa", //Region name
          "availability_zone": "bbb", //AZ name
          "vpc_id": "674e9b42-cd8d-4d25-a2e6-5abcc565b961", //VPC ID
          "subnet_id": "f1df08c5-71d1-406a-aff0-de435a51007b", //Subnet ID
         "security_group_id": "7aa51dbf-5b63-40db-9724-dad3c4828b58", //Security group ID
        "password": "******", //Administrator password
         "disk_encryption_id": "d4825f1b-5e47-4ff7-8ca9-0960da1770b1", //Key ID for encrypting disks
         "mode": "Sharding", //Sharded-cluster instance type
        "flavor": [
          {
             "type":"mongos", //mongos node
            "num": 2, //Quantity
            "spec_code": "dds.mongodb.s2.medium.4.mongos" //Node resource code
          },
          {
             "type":"shard", //shard node
            "num": 2, //Quantity
            "storage": "ULTRAHIGH", //Disk type
            "size": 20, //Disk size
            "spec_code": "dds.mongodb.s2.medium.4.shard" //Node resource code
          },
          {
             "type":"config", //config node
            "num": 1, //Quantity
            "storage": "ULTRAHIGH", //Disk type
            "size": 20, //Disk size
            "spec_code": "dds.mongodb.s2.large.2.config" //Node resource type
          }
        ],
        "backup_strategy": {
          "start_time": "23:00-00:00", //Backup period
          "keep_days": "8"  //Retention days of backup files
        },
        "ssl_option":"1"
      }

   If the following information is displayed, the request is successful:

   .. code-block:: text

      {
        "id": "46125c43ca4d424a9f5c97354223c4e0in02",
        "name": "test-cluster",
        "datastore": {
          "type": "DDS-Community",
          "version": "4.0",
          "storage_engine": "wiredTiger"
        },
        "created": "2019-01-14 08:50:27",
        "status": "creating",
        "region": "aaa",
        "availability_zone": "bbb",
        "vpc_id": "674e9b42-cd8d-4d25-a2e6-5abcc565b961",
        "subnet_id": "f1df08c5-71d1-406a-aff0-de435a51007b",
        "security_group_id": "7aa51dbf-5b63-40db-9724-dad3c4828b58",
        "disk_encryption_id": "d4825f1b-5e47-4ff7-8ca9-0960da1770b1",
        "mode": "Sharding",
        "flavor": [
          {
            "type": "mongos",
            "num": 2,
            "spec_code": "dds.mongodb.s2.medium.4.mongos"
          },
          {
            "type": "shard",
            "num": 2,
            "size": 20,
            "spec_code": "dds.mongodb.s2.medium.4.shard"
          },
          {
            "type": "config",
            "num": 1,
            "size": 20,
            "spec_code": "dds.mongodb.s2.large.2.config"
          }
        ],
        "backup_strategy": {
          "start_time": "23:00-00:00",
          "keep_days": "8"
        },
        "enterprise_project_id": "",
        "ssl_option":"1",
        "job_id": "c0c606b6-470a-48c7-97a2-6c7f146014d4"
      }

   If the request fails, an error code and error information are returned. For details, see section :ref:`Error Code <dds_error_code>`.
