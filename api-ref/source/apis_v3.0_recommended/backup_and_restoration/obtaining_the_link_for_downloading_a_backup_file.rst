:original_name: dds_api_0059.html

.. _dds_api_0059:

Obtaining the Link for Downloading a Backup File
================================================

Function
--------

This API is used to obtain the link for downloading a backup file.

Constraints
-----------

The backup download link is valid within 15 minutes after being updated.

URI
---

-  URI format

   GET https://{Endpoint}/v3/{project_id}/backups/download-file?instance_id={instance_id}&backup_id={backup_id}

-  Parameter description

   .. table:: **Table 1** Parameter description

      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name                  | Mandatory             | Description                                                                                                                                                                     |
      +=======================+=======================+=================================================================================================================================================================================+
      | project_id            | Yes                   | Specifies the project ID of a tenant in a region.                                                                                                                               |
      |                       |                       |                                                                                                                                                                                 |
      |                       |                       | For details about how to obtain the project ID, see :ref:`Obtaining a Project ID <dds_projectid>`.                                                                              |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | instance_id           | Yes                   | Specifies the instance ID, which can be obtained by calling the API for querying instances. If you do not have an instance, you can call the API used for creating an instance. |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | backup_id             | Yes                   | Specifies the backup ID.                                                                                                                                                        |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Requests
--------

-  Example request

   GET https://dds.eu-de.otc.t-systems.com/v3/97b026aa9cc4417888c14c84a1ad9860/backups/download-file?instance_id=befb1cfe1f96403780396b0c54f85d11in02&backup_id=bd062e1af2d248b3bb4cd3dbb4183888br02

Responses
---------

-  Parameter description

   .. table:: **Table 2** Parameter description

      +-----------------------+-----------------------+-------------------------------------------------------------------------+
      | Name                  | Type                  | Description                                                             |
      +=======================+=======================+=========================================================================+
      | files                 | Array of objects      | Indicates the list of backup files.                                     |
      |                       |                       |                                                                         |
      |                       |                       | For more information, see :ref:`Table 3 <dds_api_0059__table52869820>`. |
      +-----------------------+-----------------------+-------------------------------------------------------------------------+
      | bucket                | String                | Indicates the name of the bucket where the file is located.             |
      +-----------------------+-----------------------+-------------------------------------------------------------------------+

   .. _dds_api_0059__table52869820:

   .. table:: **Table 3** files field data structure description

      +-------------------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name              | Type   | Description                                                                                                                                                                                                                                                  |
      +===================+========+==============================================================================================================================================================================================================================================================+
      | name              | String | Indicates the file name.                                                                                                                                                                                                                                     |
      +-------------------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | size              | Long   | Indicates the file size in KB.                                                                                                                                                                                                                               |
      +-------------------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | download_link     | String | Indicates the link for downloading the backup file.                                                                                                                                                                                                          |
      +-------------------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | link_expired_time | String | Indicates the link expiration time. The format is "yyyy-mm-ddThh:mm:ssZ". **T** is the separator between the calendar and the hourly notation of time. **Z** indicates the time zone offset. For example, the time zone offset of UTC is shown as **+0000**. |
      +-------------------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Response example

   .. code-block:: text

      {
         "files": [
          {
              "name": "43e4feaab48f11e89039fa163ebaa7e4br02.xxx",
              "size": 2803,
              "download_link":"https://obs.domainname.com/rdsbucket.username.1/xxxxxx",
              "link_expired_time":"2018-08-016T10:15:14+0000"
           }
           ],
          "bucket": "rdsbucket.bucketname"
      }

Status Code
-----------

Status Code:200.

For more information, see :ref:`Status Code <dds_status_code>`.

Error Code
----------

For more information, see :ref:`Error Code <dds_error_code>`.
