:original_name: en-us_topic_reset_password.html

.. _en-us_topic_reset_password:

Resetting the Administrator Password
====================================

**Scenarios**
-------------

You are advised to change administrator passwords periodically to prevent password cracking, ensuring system security. You cannot reset the administrator password under the following circumstances:

-  Restarting
-  Adding node
-  Switching SSL
-  Changing port
-  Changing instance class
-  Deleting node

Method 1
--------

#. :ref:`Log in to the DDS console. <dds_02_0043>`

#. On the **Instance Management** page, locate the target DB instance and choose **More** > **Reset Password** in the **Operation** column.

#. Enter and confirm the new administrator password and click **OK**.

   The password is a string of 8 to 32 characters. It must be a combination of uppercase letters, lowercase letters, digits, and special characters. You can also use the following special characters: ``~!@#%^*-_=+?``

Method 2
--------

#. :ref:`Log in to the DDS console. <dds_02_0043>`

#. On the **Instance Management** page, click the target DB instance.

#. In the **DB Information** area on the **Basic Information** page, click **Reset Password** to the right of the **Administrator** field.

#. Enter and confirm the new administrator password and click **OK**.

   The password is a string of 8 to 32 characters. It must be a combination of uppercase letters, lowercase letters, digits, and special characters. You can also use the following special characters: ``~!@#%^*-_=+?``
