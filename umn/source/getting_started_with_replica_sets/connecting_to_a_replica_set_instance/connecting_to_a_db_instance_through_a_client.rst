:original_name: en-us_topic_0105284966.html

.. _en-us_topic_0105284966:

Connecting to a DB Instance Through a Client
============================================

**Scenarios**
-------------

This section guides you on how to connect to DB instances through a database client using a common connection or an SSL connection. You are advised to use SSL to encrypt connections to ensure data security.

Based on the application scenario, you can determine whether to access a DB instance through an EIP. For details, see :ref:`Scenarios <dds_02_0015__section055104935914>`.

You can directly perform operations on the primary and secondary nodes. Primary nodes are used for processing read and write requests. Secondary nodes replicate data from the primary and are used for processing read requests only.

This section uses the Linux OS as an example to describe how to connect to a replica set instance.

Restrictions
------------

For details about restrictions on connecting to a DB instance, see :ref:`Restrictions <dds_02_0011>`.

**Prerequisites**
-----------------

#. An ECS or a device that can access DDS is ready for use.

   -  To connect to a DDS DB instance from an ECS, you need to create and log in to the ECS. For details, see :ref:`How Can I Create and Log In to an ECS? <dds_faq_0034>`
   -  To connect to a DB instance through an EIP:

      a. Bind an EIP to a DB instance node. For details, see section :ref:`Binding an EIP <dds_02_0015__section0350133891310>`.
      b. Ensure that your local device can access the EIP that has been bound to the DB instance.

#. A MongoDB client has been installed on the prepared ECS or the device.

   For details on how to install a MongoDB client, see :ref:`How Can I Install a MongoDB Client? <dds_faq_0018>`

.. _en-us_topic_0105284966__section3730754113815:

SSL Connection
--------------

#. On the **Instance Management** page, click the target DB instance.

#. In the navigation pane on the left, choose **Connections**.

#. In the **Basic Information** area, click |image1| next to the **SSL** field to download the root certificate.

#. Upload the root certificate to the ECS that connects to the DB instance or save the root certificate to a local device that can access DDS.

   The following describes how to upload the certificate to a Linux and Window ECS:

   -  In Linux, run the following command:

      **scp** *<IDENTITY_FILE>* *<REMOTE_USER>*\ **@**\ *<REMOTE_ADDRESS>*\ **:**\ *<REMOTE_DIR>*

      .. note::

         -  **IDENTITY_FILE** indicates the directory where the root certificate locates. The file access permission is 600.
         -  **REMOTE_USER** indicates the ECS OS user.
         -  **REMOTE_ADDRESS** indicates the ECS address.
         -  **REMOTE_DIR** indicates the directory of the ECS to which the root certificate is uploaded.

   -  In Windows, upload the root certificate using file transfer tools.

#. Connect to a DDS DB instance.

   The Linux OS is used as an example.

   **./mongo --host** <*DB_HOST*> **--port** <*DB_PORT*> **-u** <*DB_USER*> **-p** **--authenticationDatabase** **admin** **--ssl --sslCAFile** <*FILE_PATH*> **--sslAllowInvalidHostnames**

   Enter the database account password when prompted:

   .. code-block::

      Enter password:

   .. note::

      -  A replica set instance uses the management IP address to generate SSL certificate. **--sslAllowInvalidHostnames** is needed for the SSL connection.
      -  **DB_HOST** indicates the IP address of the remotely connected DB instance. Obtain the value from the **Private IP Address** column in the node list on the **Connections** page. If a device can access the DB instance through an EIP, set this parameter to the EIP displayed in **EIP** column in the node list on the **Connections** page.
      -  **DB_PORT** indicates the port number. Obtain the value from **Database Port** in the **Basic Information** area on the **Connections** page.
      -  **DB_USER** indicates the database account name. The default value is **rwuser**.
      -  **FILE_PATH** indicates the path where the root certificate is stored.

   Example:

   **./mongo --host 192.168.1.6 --port 8635 -u rwuser -p --authenticationDatabase admin --ssl --sslCAFile /tmp/ca.crt** **--sslAllowInvalidHostnames**

#. Check the connection result. If the following information is displayed, the connection is successful.

   -  Result from connecting the primary node in a replica set:

      .. code-block::

         replica:PRIMARY>

   -  Result from connecting the secondary node in a replica set:

      .. code-block::

         replica:SECONDARY>

.. _en-us_topic_0105284966__en-us_topic_0085335422_sfc3bfb212a8440799f49320d91fc096c:

Common Connection
-----------------

.. important::

   To use the common connection mode, you need to disable the SSL connection. For details, see section :ref:`Disabling SSL <dds_02_0016__section584914451250>`.

#. Log in to the prepared ECS or the device that can access the document database.

#. Connect to a DDS DB instance.

   **./mongo --host** <*DB_HOST*> **--port** <*DB_PORT*> **-u** <*DB_USER*> **-p** **--authenticationDatabase** **admin**

   Enter the database account password when prompted:

   .. code-block::

      Enter password:

   .. note::

      -  **DB_HOST** indicates the IP address of the remotely connected DB instance. Obtain the value from the **Private IP Address** column in the node list on the **Connections** page. If a device can access the DB instance through an EIP, set this parameter to the EIP displayed in **EIP** column in the node list on the **Connections** page.
      -  **DB_PORT** indicates the port number. Obtain the value from **Database Port** in the **Basic Information** area on the **Connections** page.
      -  **DB_USER** indicates the database account name. The default value is **rwuser**.

   Example:

   **./mongo --host 192.168.1.6 --port 8635 -u rwuser -p --authenticationDatabase admin**

#. Check the connection result. If the following information is displayed, the connection is successful.

   -  Result from connecting the primary node in a replica set:

      .. code-block::

         replica:PRIMARY>

   -  Result from connecting the secondary node in a replica set:

      .. code-block::

         replica:SECONDARY>

.. |image1| image:: /_static/images/en-us_image_0284275232.png
