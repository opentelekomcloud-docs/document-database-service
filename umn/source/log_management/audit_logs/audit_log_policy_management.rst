:original_name: dds_03_0291.html

.. _dds_03_0291:

Audit Log Policy Management
===========================

An audit log records operations performed on your databases and collections. The generated log files are stored in OBS. Auditing logs can enhance your database security and help you analyze the cause of failed operations.

Precautions
-----------

-  The audit policy of a DDS DB instance is disabled by default. You can enable it based on your service requirements. After the function is enabled, the system records audit information about read and write operations, which may deteriorate the performance by 15% to 20%.
-  DDS checks generated audit logs. If the retention period of logs exceeds the period you set, DDS will delete the logs. It is recommended that audit logs be stored for more than 180 days for tracing and problem analysis.
-  After the audit policy is modified, DDS audits logs according to the new policy and the retention period of the original audit logs is subject to the modified retention period.
-  By default, audit logs are generated every hour. If the size of an audit log exceeds 10 MB, a new audit log is generated.
-  Your data must be encoded in UTF-8 format. For data in other format, the auditing result of the corresponding statement may be missing or contain garbled characters.
-  Audit log files stored on OBS are invisible to you. They are only visible in the DDS backend management system.

Configuring the Audit Policy
----------------------------

#. Log in to the management console.
#. Click |image1| in the upper left corner and select a region and a project.
#. Click **Service List**. Under **Database**, click **Document Database Service** to go to the DDS console.
#. On the **Instances** page, click the instance name.
#. In the navigation pane on the left, choose **Audit Logs**.
#. On the **Audit Logs** page, click **Set Audit Policy**.
#. On the displayed page, click |image2|.
#. Configure required parameters and click **OK** to enable the audit policy.

   .. table:: **Table 1** Parameter description

      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                                                        |
      +===================================+====================================================================================================================================================================================================================================================+
      | All                               | Audit all collections in the instance.                                                                                                                                                                                                             |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Custom                            | Audit specified databases or collections in the instance.                                                                                                                                                                                          |
      |                                   |                                                                                                                                                                                                                                                    |
      |                                   | The database or collection name cannot contain spaces or the following special characters: /\\' : "[]{}() The dollar sign ($) can be used only as an escape character.                                                                             |
      |                                   |                                                                                                                                                                                                                                                    |
      |                                   | The database name can contain a maximum of 64 characters.                                                                                                                                                                                          |
      |                                   |                                                                                                                                                                                                                                                    |
      |                                   | If you enter a combined database and collection name, the total name length is 120 characters with the database name length of no more than 64 characters and the collection name cannot be blank, contain **null**, or use **system.** in prefix. |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Statement Type                    | You can query audit logs of specified statements in a collection, including auth, insert, update, delete, command and query statements.                                                                                                            |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Retention Days                    | The number of days to retain audit logs. Range: 7 to 732                                                                                                                                                                                           |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   -  After the audit policy is enabled, you can modify it as required. After the modification, logs are generated according to the new policy and the retention period of the original logs is subject to the modified retention period.

      To modify the audit policy, click **Set Audit Policy**. In the dialog box that is displayed, modify the audit policy.

   -  Disable the audit policy.

      .. note::

         After the audit policy is disabled, no audit log is generated.

      To disable the audit policy, click |image3|.

      You can determine whether to delete all audit logs:

      -  If you do not select **Delete audit logs**, all audit logs within the retention period will be retained. You can manually delete them later.
      -  If you select **Delete audit logs**, all audit logs within the retention period will be deleted.

      Click **OK**.

.. |image1| image:: /_static/images/en-us_image_0000002207066505.png
.. |image2| image:: /_static/images/en-us_image_0000002171625914.png
.. |image3| image:: /_static/images/en-us_image_0000002171625918.png
