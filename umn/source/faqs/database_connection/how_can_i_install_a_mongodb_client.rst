:original_name: dds_faq_0018.html

.. _dds_faq_0018:

How Can I Install a MongoDB Client?
===================================

MongoDB official website provides client installation packages for different OSs. Download the official package at https://www.mongodb.com/try/download/community-edition/releases/archive.

.. important::

   -  The following uses **RedHat/CentOS 8.0 x64** and MongoDB 4.2.25 as examples to describe how to obtain the required installation package and install the MongoDB client.
   -  During the installation, select a client version that matches the instance version based on the actual operating system.

Procedure
---------

#. Obtain the installation package.

   a. Access https://www.mongodb.com/try/download/community-edition/releases/archive.

   b. Select version **4.2.25**, platform **RedHat/CentOS 8.0 x64**, and package **tgz**, as shown in :ref:`MongoDB page <dds_faq_0018__fig646895910135>`.

      .. _dds_faq_0018__fig646895910135:

      .. figure:: /_static/images/en-us_image_0000002529818314.png
         :alt: **Figure 1** MongoDB page

         **Figure 1** MongoDB page

   c. Use either of the following methods to upload the installation package to the ECS:

      .. note::

         For details about how to log in to an ECS, see :ref:`How Can I Create and Log In to an ECS? <dds_faq_0034>`

      -  Click to download the binary installation package of version 4.2.25. The name of the installation package is **mongodb-linux-x86_64-rhel80-4.2.25.tgz**. Upload the installation package to the ECS.
      -  Obtain the download link, log in to the ECS, and run the **wget link** command.

         .. note::

            Replace *link* with the actual download link address.

#. Decompress the installation package on the ECS.

   **tar zxvf mongodb-**\ *linux-x86_64-rhel80-4.2.25*\ **.tgz**

   .. note::

      Replace the installation package name with the actual one.

#. Access the **bin** directory where the installation package is located.

   **cd mongodb-**\ *linux-x86_64-rhel80-4.2.25*\ **/bin**

   .. note::

      Replace the installation package name with the actual one.

   The common tools are as follows:

   -  MongoDB client mongo
   -  Data export tool mongoexport
   -  Data import tool mongoimport

#. Make the packages executable.

   -  Run the **chmod +x mongo** command to grant a client permission to connect to an instance.
   -  Run the **chmod +x mongoexport** command to grant a client permission to export data.
   -  Run the **chmod +x mongoimport** command to grant a client permission to import data.

#. Connect to an instance through the installed client.

   -  To connect to a cluster instance, see :ref:`Connecting to a Cluster Instance Over Private Networks <dds_02_0009>`.
   -  To connect to a replica set instance, see :ref:`Connecting to a Replica Set Instance Over Private Networks <dds_02_0055>`.
   -  To connect to a single node instance, see :ref:`Connecting to a Single-Node Instance Over Private Networks <dds_02_0074>`.
