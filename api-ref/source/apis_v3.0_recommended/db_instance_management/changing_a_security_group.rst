:original_name: dds_api_0055.html

.. _dds_api_0055:

Changing a Security Group
=========================

Function
--------

This API is used to change the security group associated with a DB instance.

Constraints
-----------

-  Abnormal instances do not support this operation.
-  Please confirm the modified security group policy. This policy may affect the current instance connection, causing the connection interruption.

URI
---

-  URI format

   POST https://{Endpoint}/v3/{project_id}/instances/{instance_id}/modify-security-group

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

      +-------------------+-----------+--------+---------------------------------------------+
      | Name              | Mandatory | Type   | Description                                 |
      +===================+===========+========+=============================================+
      | security_group_id | Yes       | String | Specifies the ID of the new security group. |
      +-------------------+-----------+--------+---------------------------------------------+

-  Example request

   POST https://dds.eu-de.otc.t-systems.com/v3/0549b4a43100d4f32f51c01c2fe4acdb/instances/9136fd2a9fcd405ea4674276ce36dae8in02/modify-security-group

   .. code-block:: text

      {
          "security_group_id": "73bed21a-708b-4985-b697-a96d0e0d2b39"
      }

Responses
---------

-  Parameter description

   .. table:: **Table 3** Parameter description

      ================= ====== ===========================================
      Name              Type   Description
      ================= ====== ===========================================
      job_id            String Indicates the workflow ID.
      security_group_id String Indicates the ID of the new security group.
      ================= ====== ===========================================

-  Response example

   .. code-block:: text

      {
          "job_id":"3711e2ad-5787-49bc-a47f-3f0b066af9f5",
          "security_group_id":"73bed21a-708b-4985-b697-a96d0e0d2b39"
      }

Status Code
-----------

Status Code:200.

For more information, see :ref:`Status Code <dds_status_code>`.

Error Code
----------

For more information, see :ref:`Error Code <dds_error_code>`.
