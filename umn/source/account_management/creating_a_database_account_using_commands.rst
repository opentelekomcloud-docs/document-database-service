:original_name: dds_03_0057.html

.. _dds_03_0057:

Creating a Database Account Using Commands
==========================================

Scenarios
---------

This section describes how to create a database account and change the account password using commands after the DDS DB instances are created.

.. note::

   When creating a database account for a specified DB instance, you are advised to enable the SSL connection to improve data security.

**Prerequisites**
-----------------

A DDS DB instance has been connected.

-  For details on how to connect to a cluster instance, see :ref:`Connecting to a Cluster Instance Over Private Networks <en-us_topic_0044018334>`.
-  For details on how to connect to a replica set instance, see :ref:`Connecting to a Replica Set Instance Over Private Networks <en-us_topic_0105284966>`.
-  For details on how to connect to a single node instance, see :ref:`Connecting to a Single Node Instance Over Private Networks <dds_02_0028>`.

Account Description
-------------------

To manage DDS DB instances, users **root**, **monitor**, and **backup** are automatically created when you create a DDS DB instance. Attempting to delete, rename, change the passwords, or change privileges for these accounts will result in errors.

You can change the password of the database administrator **rwuser** and any accounts you create.

Setting Password Strength for Database Accounts
-----------------------------------------------

-  The administrator password must meet the following password policy:

   -  Contains 8 to 32 characters.
   -  Must be a combination of uppercase letters, lowercase letters, digits, and special characters: ``~!@#%^*-_=+?``

-  The database user created on the client must meet the following password policy:

   -  Contains 8 to 32 characters.
   -  Must be a combination of uppercase letters, lowercase letters, digits, and special characters: ``~@#%-_!*+=^?``

When you create a DB instance, DDS automatically checks your password strength. You can change the password as user **rwuser**. For security reasons, you are advised to set up a strong password.

Creating an Account
-------------------

#. Log in to the DDS.

#. Run the following command to select the admin database:

   **use admin**

#. Run the following command to create a database account (**user1** as an example):

   **db.createUser({user: "user1", pwd: "**\ ``**********``\ **", passwordDigestor:"server", roles:[{role: "root", db: "admin"}]})**

   -  **server**: indicates that the password is encrypted on the server.
   -  **roles** restrict the rights of the account. If an empty array is specified, the account does not have any permission.

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

#. Log in to the DDS.

#. Run the following command to select the admin database:

   **use admin**

#. Uses user **user1** as an example. Run the following command to change its password:

   **db.updateUser("user1", {passwordDigestor:"server",pwd:"**********"})**

   **server**: indicates that the password is encrypted on the server.

#. Check the setting result. The password is successfully changed if the following information is displayed:

   -  Cluster

      .. code-block::

         mongos>

   -  Replica set

      .. code-block::

         replica:PRIMARY>

   -  Single node

      .. code-block::

         replica:PRIMARY>
