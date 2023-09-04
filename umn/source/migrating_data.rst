:original_name: dds_03_0052.html

.. _dds_03_0052:

Migrating Data
==============

**Scenarios**
-------------

DDS is accessible through an EIP in a public network or an ECS in a private network.

MongoDB can export data from a database into a JSON file. Such a JSON file can then be used to import the data to MongoDB databases. This section describes how to import the data from the JSON files to DDS using the mongoimport tool on the ECS or from some other devices that can access DDS.

**Prerequisites**
-----------------

#. An ECS or a device that can access DDS is ready for use.

   -  To connect your DDS DB instance through a private network:

      Create and log in to an ECS. For details, see "Creating and Logging In to a Windows ECS" or "Creating and Logging In to a Linux ECS" in the *Elastic Cloud Server User Guide*.

   -  To connect to your DDS DB instance through an EIP:

      a. Bind an EIP to a node in the DB instance. For details about how to bind an EIP to a node, see "Binding an EIP" in the *Document Database Service Getting Started*.
      b. Ensure that your local device can access the EIP that has been bound to the DB instance.

#. A migration tool has been installed on the prepared ECS.

   For details on how to install the migration tool, see :ref:`How Can I Install a MongoDB Client? <dds_faq_0018>`

   .. note::

      The MongoDB client provides the mongoexport and mongoimport tools.

Exporting Data (Linux example)
------------------------------

#. Log in to the ECS or the device that can access DDS.

#. Use the mongoexport tool to transfer data from the source database to a .json file.

   The SSL connection is used as an example. If you select an unencrypted connection, delete **--ssl --sslAllowInvalidCertificates** from the following command.

   **mongoexport** **--host** *<DB_ADDRESS>* **--\ port** *<DB_PORT>* **--\ ssl** **--sslAllowInvalidCertificates** **--type json** **--authenticationDatabase** *<AUTH_DB*> **-u** *<DB_USER>* **--db** <*DB_NAME*> **--collection** <*DB_COLLECTION*> **--out** <*DB_PATH*>

   -  **DB_ADDRESS** indicates the database address.
   -  **DB_PORT** indicates the database port.
   -  **AUTH_DB** indicates the database for storing DB_USER information. Generally, this value is **admin**.
   -  **DB_USER** indicates the database user.
   -  **DB_NAME** indicates the name of the database from which data will be exported.
   -  **DB_COLLECTION** indicates the collection of the database from which data will be exported.
   -  **DB_PATH** indicates the path where the .json file is located.

   Enter the database administrator password when prompted:

   .. code-block::

      Enter password:

   The following is an example. After the command is executed, the **exportfile.json** file will be generated:

   **mongoexport --host 192.168.1.21 --port 8635 --ssl --sslAllowInvalidCertificates --type json --authenticationDatabase admin -u rwuser --db test02 --collection Test --out /tmp/mongodb/export/exportfile.json**

#. Check the result.

   If information similar to the following is displayed, the data is successfully exported. **x** indicates the number of exported data records.

   .. code-block::

      exported x records

#. Compress the exported .json file.

   **gzip exportfile.json**

   Compressing the file helps reduce the time needed to transmit all the data. The compressed file is **exportfile.json.gz**.

Importing Data
--------------

#. Log in to the ECS or the device that can access DDS.

#. Upload the data to be imported to the ECS or the device that can access DDS.

   Select an uploading method based on the OS you are using. In Linux, for example, run the following command:

   scp *<IDENTITY_FILE>* *<REMOTE_USER>*\ @\ *<REMOTE_ADDRESS>*:*<REMOTE_DIR>*

   -  **IDENTITY_FILE** indicates the directory where the **exportfile.json.gz** file is located. The file access permission is 600.
   -  **REMOTE_USER** indicates the ECS OS user.
   -  **REMOTE_ADDRESS** indicates the ECS address.
   -  **REMOTE_DIR** indicates the directory of the ECS to which the **exportfile.json.gz** file is uploaded.

   In Windows, upload **exportfile.json.gz** to the ECS using file transfer tools.

#. Decompress the package.

   **gzip** **-d** *exportfile.json.gz*

#. Import the JSON file to the DDS database.

   The SSL connection is used as an example. If you select an unencrypted connection, delete **--ssl --sslAllowInvalidCertificates** from the following command.

   **mongoimport --host** <*DB_ADDRESS*> **--port** <*DB_PORT*> **--ssl --sslAllowInvalidCertificates --type json --authenticationDatabase** <*AUTH_DB*> **-u** <*DB_USER*> **--db** <*DB_NAME*> **--collection** <*DB_COLLECTION*> **--file** <*DB_PATH*>

   -  **DB_ADDRESS** indicates the DB instance IP address.
   -  **DB_PORT** indicates the database port.
   -  **AUTH_DB** indicates the database that authenticates DB_USER. Generally, this value is **admin**.
   -  **DB_USER** indicates the account name of the database administrator.
   -  **DB_NAME** indicates the name of the database to which data will be imported.
   -  **DB_COLLECTION** indicates the collection of the database to which data will be imported.
   -  **DB_PATH** indicates the path where the .json file is located.

   Enter the database administrator password when prompted:

   .. code-block::

      Enter password:

   The following is an example:

   **mongoimport --host 192.168.1.21 --port 8635 --ssl --sslAllowInvalidCertificates --type json --authenticationDatabase admin -u rwuser --db test02 --collection Test --file /tmp/mongodb/export/exportfile.json**

#. Check the result.

   If information similar to the following is displayed, the data is successfully imported. **x** indicates the number of imported data records.

   .. code-block::

      imported x records
