:original_name: dds_api_0100.html

.. _dds_api_0100:

Obtaining Links for Downloading Audit Logs
==========================================

Function
--------

This API is used to obtain the link for downloading audit logs.

URI
---

-  URI format

   POST https://{Endpoint}/v3/{project_id}/instances/{instance_id}/auditlog-links

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

   .. table:: **Table 2** Parameter description

      +------+-----------+------------------+------------------------------------------------------------------------------------------+
      | Name | Mandatory | Type             | Description                                                                              |
      +======+===========+==================+==========================================================================================+
      | ids  | Yes       | Array of strings | Specifies the list of audit logs. A maximum of 50 audit log IDs are allowed in the list. |
      +------+-----------+------------------+------------------------------------------------------------------------------------------+

-  Request example

   POST https://dds.eu-de.otc.t-systems.com/v3/0549b4a43100d4f32f51c01c2fe4acdb/instances/2870a411522849aa901cd4351c96a3b7in02/auditlog-links

   .. code-block:: text

      {
         "ids": ["10190012aae94b38a10269b8ad025fc1no02_1607681849871", "12390012aae94b38a10269b8ad025fc1no02_1607681849871"]
      }

Responses
---------

-  Parameter description

   .. table:: **Table 3** Parameter description

      +-------+------------------+-----------------------------------------------------------------------------------+
      | Name  | Type             | Description                                                                       |
      +=======+==================+===================================================================================+
      | links | Array of strings | Indicates the list of audit log download links. The validity period is 5 minutes. |
      +-------+------------------+-----------------------------------------------------------------------------------+

-  Response example

   .. code-block:: text

      {
          "links": ["https://obs.domainname.com/ddsbucket.username.1/xxxxxx", "https://obs.domainname.com/ddsbucket.username.2/xxxxxx"]
       }

Status Code
-----------

Status Code:200.

For more information, see :ref:`Status Code <dds_status_code>`.

Error Code
----------

For more information, see :ref:`Error Code <dds_error_code>`.
