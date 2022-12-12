:original_name: dds_03_0057.html

.. _dds_03_0057:

Managing Database Accounts
==========================

Scenarios
---------

This section guides you through how to create a database account and change the account password to manage the instances you created.

.. note::

   When creating a database account for a specified DB instance, you are advised to enable the SSL connection to improve data security.

**Prerequisites**
-----------------

A DDS DB instance has been connected.

-  For details on how to connect to a cluster instance, see :ref:`Connecting to a DB Instance Through a Client <en-us_topic_0044018334>`.
-  For details on how to connect to a replica set instance, see :ref:`Connecting to a DB Instance Through a Client <en-us_topic_0105284966>`.

Account Description
-------------------

To provide management services for DDS DB instances, users **root**, **monitor**, and **backup** are created when you create a DDS DB instance. Attempting to delete, rename, change the passwords, or change privileges for these accounts will result in errors.

You can change the password of the database administrator **rwuser** and any accounts you create.

Setting Password Strength for Database Accounts
-----------------------------------------------

-  The administrator password must meet the following password policy:

   -  8 to 32 characters in length
   -  A combination of uppercase letters, lowercase letters, digits, and special characters: ``~!@#%^*-_=+?``

-  The DDS instance database uses comprehensive password security policies. The password of a DDS instance database account must meet the following conditions:

   -  8 to 32 characters in length
   -  A combination of uppercase letters, lowercase letters, digits, and special characters: ``~!@#%^*-_=+?``

When you create a DB instance, the system automatically checks your password strength. You can change the password as user **rwuser**. For security reasons, you are advised to set up a strong password.

Creating an Account
-------------------

#. Run the following command to select the admin database:

   **use admin**

#. Run the following command to create a database account (**user1** as an example):

   **db.createUser({user: "user1", pwd: "**\ *Test_12345*\ **", passwordDigestor:"server", roles:[{role: "root", db: "admin"}]})**

   -  **server**: indicates that the password is encrypted on the server.
   -  **Test_12345**: indicates the example new password. The password must be 8 to 32 characters in length and contain uppercase letters, lowercase letters, digits, and special characters, such as ``~@#%-_!*+=^?``
   -  **roles** restricts the rights of the account. If an empty array is specified, the account does not have any permission.

#. Check the result:

   The account is successfully created if the following information is displayed:

   .. code-block::

      Successfully added user: {
              "user" : "user1",
              "passwordDigestor" : "server",
              "roles" : [
                      {
                              "role" : "root",
                              "db" : "admin"
                      }
              ]
      }

Changing a Password
-------------------

#. Run the following command to select the admin database:

   **use admin**

#. Uses user **user1** as an example. Run the following command to change its password:

   **db.updateUser("user1", {passwordDigestor:"server",pwd:"newPasswd12#"})**

   -  **server**: indicates that the password is encrypted on the server.
   -  **newPasswd12#**: indicates the example new password. The password must be 8 to 32 characters in length and contain uppercase letters, lowercase letters, digits, and special characters, such as ``~@#%-_!*+=^?``

#. Check the setting result. The password is successfully changed if the following information is displayed:

   -  Cluster

      .. code-block::

         mongos>

   -  Replica set

      .. code-block::

         replica:PRIMARY>
