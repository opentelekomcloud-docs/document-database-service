:original_name: en-us_topic_0105284966.html

.. _en-us_topic_0105284966:

Connecting to a Replica Set Instance Over Private Networks
==========================================================

Scenarios
---------

This section describes how to connect to a replica set instance using the MongoDB client over private networks.DDS is compatible with MongoDB.

You can directly perform operations on the primary and secondary nodes. Primary nodes are used for processing read and write requests. Secondary nodes replicate data from the primary and are used for processing read requests only.

The MongoDB client can connect to a DB instance with an unencrypted connection or an encrypted connection (SSL). To improve data transmission security, you are advised to connect to DB instances using the SSL connection.

**Different OS scenarios**: The following uses Linux ECS and Window client as an example.

Constraints
-----------

For details about constraints on connecting to a replica set instance over private networks, see :ref:`Constraints and Recommendations <dds_01_0022>`.

Prerequisites
-------------

#. For details on how to create and log in to an ECS, see "Creating and Logging In to a Windows ECS" or "Creating and Logging In to a Linux ECS" in the *Elastic Cloud Server User Guide*.

#. Install the MongoDB client on the ECS.

   For details on how to install a MongoDB client, see :ref:`How Can I Install a MongoDB Client? <dds_faq_0018>`

Connecting to a DB Instance Using the MongoDB Client (SSL)
----------------------------------------------------------

.. important::

   If you connect to a DB instance using this method, enable the SSL connection. For details, see section :ref:`Enabling SSL <dds_03_0074__en-us_topic_0049044698_section45421719172826>`.

#. On the **Instance Management** page, click the target DB instance.

#. In the navigation pane on the left, choose **Connections**.

#. In the **Basic Information** area, click |image1| next to the **SSL** field.

#. Upload the root certificate to the ECS to be connected to the DB instance.

   The following describes how to upload the certificate to a Linux and Window ECS:

   -  In Linux, run the following command:

      **scp** *<IDENTITY_FILE>* *<REMOTE_USER>*\ **@**\ *<REMOTE_ADDRESS>*\ **:**\ *<REMOTE_DIR>*

      .. note::

         -  **IDENTITY_FILE** indicates the directory where the root certificate resides. The file access permission is 600.
         -  **REMOTE_USER** indicates the ECS OS user.
         -  **REMOTE_ADDRESS** indicates the ECS address.
         -  **REMOTE_DIR** indicates the directory of the ECS to which the root certificate is uploaded.

   -  In Windows, upload the root certificate using the remote connection tool.

#. Connect to a DDS DB instance.

   -  Method 1: Using standard parameters

      .. code-block:: text

         mongo --host <DB_HOST> --port <DB_PORT> -u <DB_USER> -p --authenticationDatabase admin --ssl --sslCAFile <FILE_PATH> --sslAllowInvalidHostnames

      Enter the database account password when prompted:

      .. code-block::

         Enter password:

   -  Method 2: Using standard URI format

      .. code-block:: text

         mongo "mongodb://rwuser:<password>@<DB_HOST1>:<DB_PORT1>,<DB_HOST2>:<DB_PORT2>/test?authSource=admin&replicaSet=replica" --ssl --sslCAFile <FILE_PATH> --sslAllowInvalidHostnames

      If the DB instance is connected using the connection address, add double quotation marks before and after the connection information. The connection information can be obtained in the **Address** column on the **Instance Management** page.

   .. note::

      -  A replica set instance uses the management IP address to generate SSL certificate. **--sslAllowInvalidHostnames** is needed for the SSL connection through a private network.
      -  **DB_HOST** indicates the IP address of the remotely connected DB instance. Obtain the value from the **Private IP Address** column in the node list on the **Connections** page.
      -  **DB_PORT** indicates the port number. Obtain the value from **Database Port** in the **Basic Information** area on the **Connections** page.
      -  **DB_HOST** and **DB_PORT** can also be obtained from the Node Information area on the Basic Information page.
      -  **DB_USER** indicates the database account name. The default value is **rwuser**.
      -  **<password>** indicates the password of the database account. If the password contains at signs (@),exclamation marks (!), or percent signs (%), replace them with hexadecimal URL codes %40, %21, and %25 respectively.
      -  If user inputs this command then the password will be stored in logfiles and can be found in linux history, and in process list. So please note that plaintext passwords are risky.
      -  **FILE_PATH** indicates the path where the root certificate is stored.

   -  Connect to the instance using standard parameters. The following is an example command:

      .. code-block:: text

         mongo --host 192.168.1.6 --port 8635 -u rwuser -p --authenticationDatabase admin --ssl --sslCAFile /tmp/ca.crt --sslAllowInvalidHostnames

   -  Connect to the DB instance using standard URI format. The following is an example command:

      .. code-block:: text

         mongo "mongodb://rwuser:<password>@192.168.1.6:8635,192.168.1.80:8635/test?authSource=admin&replicaSet=replica" --ssl --sslCAFile /tmp/ca.crt --sslAllowInvalidHostnames

#. Check the connection result. If the following information is displayed, the connection is successful.

   -  Result from connecting to the primary node in a replica set or connecting to the whole replica set:

      .. code-block::

         replica:PRIMARY>

   -  Result from connecting the secondary node in a replica set:

      .. code-block::

         replica:SECONDARY>

Connecting to a DB Instance Using the MongoDB Client (Non-SSL)
--------------------------------------------------------------

.. important::

   If you connect to a DB instance using this method, disable the SSL connection. For details, see section :ref:`Disabling SSL <dds_03_0074__section4225593518277>`.

#. Connect to a DDS DB instance.

   -  Method 1: Using standard parameters

      .. code-block:: text

         mongo --host <DB_HOST> --port <DB_PORT> -u <DB_USER> -p --authenticationDatabase admin

      Enter the database account password when prompted:

      .. code-block::

         Enter password:

   -  Method 2: Using unencrypted connection

      .. code-block:: text

         mongo "mongodb://rwuser:<password>@<DB_HOST1>:<DB_PORT1>,<DB_HOST2>:<DB_PORT2>/test?authSource=admin&replicaSet=replica"

      If the DB instance is connected using the connection address, add double quotation marks before and after the connection information. The connection information can be obtained in the **Address** column on the **Instance Management** page.

   .. note::

      -  **DB_HOST** indicates the IP address of the remotely connected DB instance. Obtain the value from the **Private IP Address** column in the node list on the **Connections** page.
      -  **DB_PORT** indicates the port number. Obtain the value from **Database Port** in the **Basic Information** area on the **Connections** page.
      -  **DB_HOST** and **DB_PORT** can also be obtained from the Node Information area on the Basic Information page.
      -  **DB_USER** indicates the database account name. The default value is **rwuser**.
      -  **<password>** indicates the password of the database account. If the password contains at signs (@),exclamation marks (!), or percent signs (%), replace them with hexadecimal URL codes %40, %21, and %25 respectively.
      -  If user inputs this command then the password will be stored in logfiles and can be found in linux history, and in process list. So please note that plaintext passwords are risky.

   -  Connect to the instance using standard parameters. The following is an example command:

      .. code-block:: text

         mongo --host 192.168.1.6 --port 8635 -u rwuser -p --authenticationDatabase admin

   -  Connect to the DB instance using standard URI format. The following is an example command:

      .. code-block:: text

         mongo "mongodb://rwuser:<password>@192.168.1.6:8635,192.168.1.80:8635/test?authSource=admin&replicaSet=replica"

#. Check the connection result. If the following information is displayed, the connection is successful.

   -  Result from connecting to the primary node in a replica set or connecting to the whole replica set:

      .. code-block::

         replica:PRIMARY>

   -  Result from connecting the secondary node in a replica set:

      .. code-block::

         replica:SECONDARY>

.. |image1| image:: /_static/images/en-us_image_0000001096133868.png
