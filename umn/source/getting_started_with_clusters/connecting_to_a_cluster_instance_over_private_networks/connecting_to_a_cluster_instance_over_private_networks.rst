:original_name: en-us_topic_0044018334.html

.. _en-us_topic_0044018334:

Connecting to a Cluster Instance Over Private Networks
======================================================

Scenarios
---------

This section describes how to connect to a cluster instance using the MongoDB client over private networks.

The MongoDB client can connect to a DB instance with an unencrypted connection or an encrypted connection (SSL). To improve data transmission security, you are advised to connect to DB instances using the SSL connection.

**Different OS scenarios**: Examples include Linux and Windows clients.

Constraints
-----------

For details about constraints on connecting to a DB instance, see :ref:`Constraints and Recommendations <dds_01_0022>`.

Prerequisites
-------------

#. For details on how to create and log in to an ECS, see "Creating and Logging In to a Windows ECS" or "Creating and Logging In to a Linux ECS" in the *Elastic Cloud Server User Guide*.

#. Install the MongoDB client on the ECS.

   For details on how to install a MongoDB client, see :ref:`How Can I Install a MongoDB Client? <dds_faq_0018>`

   .. note::

      If you use a :ref:`connection address <en-us_topic_0044018334__li122297367491>` to connect to a cluster instance, download the MongoDB client of version later than 3.4.

Connecting to a DB Instance Using the MongoDB Client (SSL)
----------------------------------------------------------

.. important::

   If you connect to a DB instance using this method, enable the SSL connection. For details, see section :ref:`Enabling SSL <dds_03_0074__en-us_topic_0049044698_section45421719172826>`.

#. On the **Instance Management** page, click the target DB instance.

#. In the navigation pane on the left, choose **Connections**.

#. In the **Basic Information** area, click |image1| next to the **SSL** field.

   .. note::

      The certificate can also be downloaded from the **Node Information** area on the **Basic Information** page.

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

#. Connect to the DB instance in the directory where the MongoDB client is located.

   -  Method 1: Using standard parameters

      .. code-block:: text

         mongo --host <DB_HOST> --port <DB_PORT> -u <DB_USER> -p --authenticationDatabase admin --ssl --sslCAFile <FILE_PATH> --sslAllowInvalidHostnames

      Enter the database account password when prompted:

      .. code-block::

         Enter password:

   -  Method 2: Using standard URI format.

      .. code-block:: text

         mongo mongodb://rwuser:<password>@<DB_HOST>:<DB_PORT>,<DB_HOST>:<DB_PORT>/test?authSource=admin --ssl --sslCAFile <FILE_PATH> --sslAllowInvalidHostnames

      The connection information can be obtained in the **Address** column on the **Instance Management** page.

      A connection address indicates that one of the dds mongos nodes will be randomly connected. If you use this method to connect to a DB instance, use the MongoDB client of version later than 3.4.

   .. note::

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

   -  Using standard URI format

      .. code-block:: text

         mongo mongodb://rwuser:<password>@192.168.1.6:8635/test?authSource=admin --ssl --sslCAFile /tmp/ca.crt --sslAllowInvalidHostnames

#. Check the connection result. If the following information is displayed, the connection is successful.

   .. code-block::

      mongos>

Connecting to a DB Instance Using the MongoDB Client (Non-SSL)
--------------------------------------------------------------

.. important::

   If you connect to a DB instance using this method, disable the SSL connection. For details, see section :ref:`Disabling SSL <dds_03_0074__section4225593518277>`.

#. Connect to the DB instance in the directory where the MongoDB client is located.

   -  Method 1: Using standard parameters

      .. code-block:: text

         mongo --host <DB_HOST> --port <DB_PORT> -u <DB_USER> -p --authenticationDatabase admin

      Enter the database account password when prompted:

      .. code-block::

         Enter password:

   -  .. _en-us_topic_0044018334__li122297367491:

      Method 2: Using standard URI format

      .. code-block:: text

         mongo mongodb://rwuser:<password>@<DB_HOST1>:<DB_PORT1>,<DB_HOST2>:<DB_PORT2>/test?authSource=admin

      The connection information can be obtained in the **Address** column on the **Instance Management** page.

      A connection address indicates that one of the dds mongos nodes will be randomly connected. If you use this method to connect to a DB instance, use the MongoDB client of version later than 3.4.

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

   -  Using standard URI format:

      .. code-block:: text

         mongo mongodb://rwuser:<password>@192.168.1.6:8635/test?authSource=admin

#. Check the connection result. If the following information is displayed, the connection is successful.

   .. code-block::

      mongos>

.. |image1| image:: /_static/images/en-us_image_0000001095974032.png
