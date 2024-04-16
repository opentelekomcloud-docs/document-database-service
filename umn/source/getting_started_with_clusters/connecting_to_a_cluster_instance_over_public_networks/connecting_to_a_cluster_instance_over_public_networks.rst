:original_name: dds_02_0006.html

.. _dds_02_0006:

Connecting to a Cluster Instance Over Public Networks
=====================================================

Scenarios
---------

This section describes how to connect to a cluster instance using the MongoDB client and Robo 3T over public networks.DDS is compatible with MongoDB.

The MongoDB client and Robo 3T can connect to a DB instance with an unencrypted connection or an encrypted connection (SSL). To improve data transmission security, you are advised to connect to DB instances using the SSL connection.

**Different OS scenarios**: Examples include Linux and Windows clients.

Prerequisites
-------------

#. :ref:`Bind an EIP <dds_02_0046>` to the cluster instance and :ref:`set security group rules <dds_02_0019>` to ensure that the EIP can be accessed with the DB client application.

#. Install the MongoDB client or Robo 3T.

   **MongoDB client**

   a. For details on how to create and log in to an ECS, see "Creating and Logging In to a Windows ECS" or "Creating and Logging In to a Linux ECS" in the *Elastic Cloud Server User Guide*.

   b. Install the MongoDB client on the ECS.

      For details on how to install a MongoDB client, see :ref:`How Can I Install a MongoDB Client? <dds_faq_0018>`

      .. note::

         If you use a :ref:`connection address <dds_02_0006__li122297367491>` to connect to a cluster instance, download the MongoDB client of version later than 3.4.

   **Robo 3T**

   For details on how to install Robo 3T, see :ref:`How Do I Install Robo 3T? <dds_faq_0039>`

#. If SSL is enabled, download the SSL certificate on the DDS console.

   a. On the **Instance Management** page, click the target DB instance.
   b. In the navigation pane on the left, choose **Connections**.
   c. In the **Basic Information** area, click |image1| next to the **SSL** field.

   .. note::

      The certificate can also be downloaded from the **Node Information** area on the **Basic Information** page.

Connecting to a DB Instance Using Robo 3T (SSL)
-----------------------------------------------

.. important::

   If you connect to a DB instance using this method, enable the SSL connection. For details, see section :ref:`Enabling SSL <dds_03_0074__en-us_topic_0049044698_section45421719172826>`.

#. Run the installed Robo 3T. On the displayed dialog box, click **Create**.


   .. figure:: /_static/images/en-us_image_0000001095974050.png
      :alt: **Figure 1** Connections

      **Figure 1** Connections

#. In the **Connection Settings** dialog box, set the parameters of the new connection.

   a. On the **Connection** tab, enter the name of the new connection in the **Name** text box and enter the EIP and database port that are bound to the DDS DB instance in the **Address** text box.


      .. figure:: /_static/images/en-us_image_0000001143133815.png
         :alt: **Figure 2** Connection

         **Figure 2** Connection

   b. On the **Authentication** tab, set **Database** to **admin**, **User Name** to **rwuser**, and **Password** to the administrator password you set during the creation of the cluster instance.


      .. figure:: /_static/images/en-us_image_0000001142773917.png
         :alt: **Figure 3** Authentication

         **Figure 3** Authentication

   c. On the **SSL** tab, upload the SSL certificate and select **Allowed** for **Invalid Hostnames**.


      .. figure:: /_static/images/en-us_image_0000001142773909.png
         :alt: **Figure 4** SSL

         **Figure 4** SSL

   d. Click **Save**.

#. On the **MongoDB Connections** page, click **Connect** to connect to the cluster instance.


   .. figure:: /_static/images/en-us_image_0000001096453848.png
      :alt: **Figure 5** Connections

      **Figure 5** Connections

#. If the cluster instance is successfully connected, the page shown in :ref:`Figure 6 <dds_02_0006__fig156158172016>` is displayed.

   .. _dds_02_0006__fig156158172016:

   .. figure:: /_static/images/en-us_image_0000001096293856.png
      :alt: **Figure 6** Connection succeeded

      **Figure 6** Connection succeeded

Connecting to a DB Instance Using Robo 3T (Non-SSL)
---------------------------------------------------

.. important::

   If you connect to a DB instance using this method, disable the SSL connection. For details, see section :ref:`Disabling SSL <dds_03_0074__section4225593518277>`.

#. Run the installed Robo 3T. On the displayed dialog box, click **Create**.


   .. figure:: /_static/images/en-us_image_0000001143053817.png
      :alt: **Figure 7** Connections

      **Figure 7** Connections

#. In the **Connection Settings** dialog box, set the parameters of the new connection.

   a. On the **Connection** tab, enter the name of the new connection in the **Name** text box and enter the EIP and database port that are bound to the DDS DB instance in the **Address** text box.


      .. figure:: /_static/images/en-us_image_0000001142773911.png
         :alt: **Figure 8** Connection

         **Figure 8** Connection

   b. On the **Authentication** tab, set **Database** to **admin**, **User Name** to **rwuser**, and **Password** to the administrator password you set during the creation of the cluster instance.


      .. figure:: /_static/images/en-us_image_0000001143053819.png
         :alt: **Figure 9** Authentication

         **Figure 9** Authentication

   c. Click **Save**.

#. On the **MongoDB Connections** page, click **Connect** to connect to the cluster instance.


   .. figure:: /_static/images/en-us_image_0000001143053813.png
      :alt: **Figure 10** Connections

      **Figure 10** Connections

#. If the cluster instance is successfully connected, the page shown in :ref:`Figure 11 <dds_02_0006__fig6991458155017>` is displayed.

   .. _dds_02_0006__fig6991458155017:

   .. figure:: /_static/images/en-us_image_0000001142893865.png
      :alt: **Figure 11** Connection succeeded

      **Figure 11** Connection succeeded

Connecting to a DB Instance Using the MongoDB Client (SSL)
----------------------------------------------------------

.. important::

   If you connect to a DB instance using this method, enable the SSL connection. For details, see section :ref:`Enabling SSL <dds_03_0074__en-us_topic_0049044698_section45421719172826>`.

#. On the **Instance Management** page, click the target DB instance.

#. In the navigation pane on the left, choose **Connections**.

#. In the **Basic Information** area, click |image2| next to the **SSL** field.

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

      **mongo --host** <*DB_HOST*> **--port** <*DB_PORT*> **-u** <*DB_USER*> **-p** **--authenticationDatabase** **admin** **--ssl --sslCAFile** <*FILE_PATH*> **--sslAllowInvalidHostnames**

      Enter the database account password when prompted:

      .. code-block::

         Enter password:

   -  Method 2: Using standard URI format

      **mongo mongodb://rwuser:<password>@**\ *<DB_HOST>*\ **:**\ *<DB_PORT>*\ **/test?authSource=admin** **--ssl --sslCAFile** *<FILE_PATH>* **--sslAllowInvalidHostnames**

      To obtain the public connection address, click the instance name and choose **Connections**. The address is displayed in **Public Network Connection Address** field on the **Public Connection** tab.

   .. note::

      -  A cluster instance uses the management IP address to generate SSL certificate. **--sslAllowInvalidHostnames** is needed for the SSL connection in a public network.
      -  **DB_HOST** indicates the IP address of the remotely connected DB instance. Obtain the value from the **EIP** column in the node list on the **Connections** page.
      -  **DB_PORT** indicates the port number. Obtain the value from **Database Port** in the **Basic Information** area on the **Connections** page.
      -  **DB_HOST** and **DB_PORT** can also be obtained from the Node Information area on the Basic Information page.
      -  **DB_USER** indicates the database account name. The default value is **rwuser**.
      -  **<password>** indicates the password of the database account. If the password contains at signs (@),exclamation marks (!), or percent signs (%), replace them with hexadecimal URL codes %40, %21, and %25 respectively.
      -  If user inputs this command then the password will be stored in logfiles and can be found in linux history, and in process list. So please note that plaintext passwords are risky.
      -  **FILE_PATH** indicates the path where the root certificate is stored.

   -  Connect to the instance using standard parameters. The following is an example command:

      **mongo --host 192.168.1.6 --port 8635 -u rwuser -p --authenticationDatabase admin --ssl --sslCAFile /tmp/ca.crt** **--sslAllowInvalidHostnames**

   -  Using standard URI format:

      **mongo** **mongodb://rwuser:<password>@\ 192.168.1.80:8635/test?authSource=admin** **--ssl --sslCAFile /tmp/ca.crt --sslAllowInvalidHostnames**

#. Check the connection result. If the following information is displayed, the connection is successful.

   .. code-block::

      mongos>

Connecting to a DB Instance Using the MongoDB Client (Non-SSL)
--------------------------------------------------------------

.. important::

   If you connect to a DB instance using this method, disable the SSL connection. For details, see section :ref:`Disabling SSL <dds_03_0074__section4225593518277>`.

#. Connect to the DB instance in the directory where the MongoDB client is located.

   -  Method 1: Using standard parameters

      **mongo --host** <*DB_HOST*> **--port** <*DB_PORT*> **-u** <*DB_USER*> **-p** **--authenticationDatabase** **admin**

      Enter the database account password when prompted:

      .. code-block::

         Enter password:

   -  .. _dds_02_0006__li122297367491:

      Method 2: Using standard URI format

      **./mongo** **mongodb://rwuser:**\ <password>\ **@**\ *<DB_HOST>*\ **:**\ *<DB_PORT>*\ **/test?authSource=admin**

      To obtain the public connection address, click the instance name and choose **Connections**. The address is displayed in **Public Network Connection Address** field on the **Public Connection** tab.

   .. note::

      -  **DB_HOST** indicates the IP address of the remotely connected DB instance. Obtain the value from the **EIP** column in the node list on the **Connections** page.
      -  **DB_PORT** indicates the port number. Obtain the value from **Database Port** in the **Basic Information** area on the **Connections** page.
      -  **DB_HOST** and **DB_PORT** can also be obtained from the **Node Information** area on the **Basic Information** page.
      -  **DB_USER** indicates the database account name. The default value is **rwuser**.
      -  **<password>** indicates the password of the database account. If the password contains at signs (@),exclamation marks (!), or percent signs (%), replace them with hexadecimal URL codes %40, %21, and %25 respectively.
      -  If user inputs this command then the password will be stored in logfiles and can be found in linux history, and in process list. So please note that plaintext passwords are risky.

   -  Connect to the instance using standard parameters. The following is an example command:

      **mongo --host 192.168.1.6 --port 8635 -u rwuser -p --authenticationDatabase admin**

   -  Using standard URI format:

      **mongo** **mongodb://rwuser:<password>@\ 192.168.1.80:8635/test?authSource=admin**

#. Check the connection result. If the following information is displayed, the connection is successful.

   .. code-block::

      mongos>

.. |image1| image:: /_static/images/en-us_image_0000001143133809.png
.. |image2| image:: /_static/images/en-us_image_0000001096453856.png
