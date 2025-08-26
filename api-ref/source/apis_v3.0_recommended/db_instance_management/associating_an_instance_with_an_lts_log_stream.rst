:original_name: dds_api_024.html

.. _dds_api_024:

Associating an Instance with an LTS Log Stream
==============================================

API Description
---------------

After you have associated an instance with a Log Tank Service (LTS) log stream, logs of the instance are automatically uploaded to the associated LTS log stream. You will be billed for log reporting. For details, see LTS pricing details. After a specific log stream is selected, the system creates a structuring rule of the required log type for it.

Restrictions
------------

-  This operation cannot be performed on instances in the creating, deleted, or frozen state.
-  A maximum of 100 data records are supported.

URI
---

-  URI format

   POST https://{Endpoint}/v3/{project_id}/instances/logs/lts-configs

   .. table:: **Table 1** Path parameters

      +------------+-----------+--------+------------------------------------------------------------------------------------------------------------------+
      | Parameter  | Mandatory | Type   | Description                                                                                                      |
      +============+===========+========+==================================================================================================================+
      | project_id | Yes       | String | Project ID of a tenant in a region. To obtain the project ID, see :ref:`Obtaining a Project ID <dds_projectid>`. |
      +------------+-----------+--------+------------------------------------------------------------------------------------------------------------------+

   .. table:: **Table 2** Request parameters

      ============ ========= ====== =============================
      Parameter    Mandatory Type   Description
      ============ ========= ====== =============================
      X-Auth-Token Yes       String User token obtained from IAM.
      ============ ========= ====== =============================

Requests
--------

-  Parameter description

   .. table:: **Table 3** Request body parameters

      +-------------+---------------------------------------------------------------------+-----------+------------------------------------------------------------+
      | Parameter   | Type                                                                | Mandatory | Description                                                |
      +=============+=====================================================================+===========+============================================================+
      | lts_configs | Array of :ref:`Table 4 <dds_api_024__table134061651112112>` objects | Yes       | Each item indicates an LTS configuration for the instance. |
      +-------------+---------------------------------------------------------------------+-----------+------------------------------------------------------------+

   .. _dds_api_024__table134061651112112:

   .. table:: **Table 4** lts_configs

      +---------------+--------+-----------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter     | Type   | Mandatory | Description                                                                                                                                                                                     |
      +===============+========+===========+=================================================================================================================================================================================================+
      | instance_id   | String | Yes       | DDS Instance ID, which can be obtained by calling the API for querying instances and details. If there are no instances available, create one by calling the API used for creating an instance. |
      +---------------+--------+-----------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | log_type      | String | Yes       | LTS log type. This parameter cannot be left empty. The only supported option is **audit_log**.                                                                                                  |
      +---------------+--------+-----------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | lts_group_id  | String | Yes       | LTS log group ID. You can obtain the value using the LTS API for querying all log groups under an account.                                                                                      |
      +---------------+--------+-----------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | lts_stream_id | String | Yes       | LTS log stream ID. You can obtain the value using the LTS API for querying all log streams in a specified log group.                                                                            |
      +---------------+--------+-----------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Example request

   Enabling audit log reporting to LTS for a DB instance

   POST https://{endpoint}/v3/619d3e78f61b4be68bc5aa0b59edcf7b/instances/logs/lts-configs

   .. code-block::

      {
        "lts_configs" : [ {
          "instance_id" : "520c58ba00a3497e97ce0b9604874dd6in02",
          "log_type" : "audit_log",
          "lts_group_id" : "ec6dc499-1a63-4229-a0c2-a2afa8bcfc95",
          "lts_stream_id" : "cae69d2e-378b-41dd-b3c9-3ca1cd5335bc"
        } ]
      }

Responses
---------

-  Parameter description

   None

-  Example response

   None

Status Code
-----------

=========== =======================
Status Code Description
=========== =======================
202         Accepted.
default     Client or server error.
=========== =======================

Error Code
----------

For details, see :ref:`Error Code <dds_error_code>`.
