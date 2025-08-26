:original_name: dds_api_025.html

.. _dds_api_025:

Disassociating an Instance from an LTS Log Stream
=================================================

API Description
---------------

After you have disassociated an instance from an LTS log stream, logs of the instance are not uploaded to the LTS log stream.

URI
---

-  URI format

   DELETE https://{Endpoint}/v3/{project_id}/instances/logs/lts-configs

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

      +-------------+---------------------------------------------------------------------+-----------+----------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter   | Type                                                                | Mandatory | Description                                                                                                                            |
      +=============+=====================================================================+===========+========================================================================================================================================+
      | lts_configs | Array of :ref:`Table 4 <dds_api_025__table134061651112112>` objects | Yes       | List of LTS configurations to be disabled. To disable multiple log configurations for an instance, you need to specify multiple items. |
      +-------------+---------------------------------------------------------------------+-----------+----------------------------------------------------------------------------------------------------------------------------------------+

   .. _dds_api_025__table134061651112112:

   .. table:: **Table 4** lts_configs

      +-------------+--------+-----------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter   | Type   | Mandatory | Description                                                                                                                                                                                     |
      +=============+========+===========+=================================================================================================================================================================================================+
      | instance_id | String | Yes       | DDS Instance ID, which can be obtained by calling the API for querying instances and details. If there are no instances available, create one by calling the API used for creating an instance. |
      +-------------+--------+-----------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | log_type    | String | Yes       | LTS log type. This parameter cannot be left empty. The only supported option is **audit_log**.                                                                                                  |
      +-------------+--------+-----------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Example request

   Disabling audit log reporting to LTS for a DB instance

   DELETE https://{endpoint}/v3/619d3e78f61b4be68bc5aa0b59edcf7b/instances/logs/lts-configs

   .. code-block::

      {
         "lts_configs" : [ {
           "instance_id" : "520c58ba00a3497e97ce0b9604874dd6in02",
           "log_type" : "audit_log"
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
