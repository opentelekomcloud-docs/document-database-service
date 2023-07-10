:original_name: dds_faq_0018.html

.. _dds_faq_0018:

How Can I Install a MongoDB Client?
===================================

MongoDB official website provides client installation packages for different OSs. Download the official binary installation package at https://www.mongodb.com/download-center#community.

The following uses Red Hat Linux 7 and MongoDB 3.4.0 as examples to describe how to obtain the required installation package and install the MongoDB client.

Procedure
---------

#. Obtain the installation package.

   a. Log in at https://www.mongodb.com/download-center/community.

   b. Choose **Server**, select **RHEL 7.0 Linux 64-bit x64** for **OS**, and click **All version binaries**. :ref:`Figure 1 <dds_faq_0018__fig129943125910>` shows an example.

      .. _dds_faq_0018__fig129943125910:

      .. figure:: /_static/images/en-us_image_0000001096453900.png
         :alt: **Figure 1** MongoDB official webpage

         **Figure 1** MongoDB official webpage

   c. Open the downloading page, click **linux/mongodb-linux-x86_64-rhel70-3.4.0.tgz** to download the binary installation package of MongoDB 3.4.0. :ref:`Figure 2 <dds_faq_0018__fig12339163313218>` shows an example.

      .. _dds_faq_0018__fig12339163313218:

      .. figure:: /_static/images/en-us_image_0000001142893909.png
         :alt: **Figure 2** Downloading page

         **Figure 2** Downloading page

#. Upload the installation package to the ECS. For details about how to log in to an ECS.

#. Decompress the installation package on the ECS.

   **tar zxvf mongodb-linux-x86_64-rhel70-3.4.0.tgz**

#. Obtain the client tool from the **bin** directory of the installation package.

   **cd mongodb-linux-x86_64-rhel70-3.4.0/bin**

   The common tools are as follows:

   -  MongoDB client mongo
   -  Data export tool mongoexport
   -  Data import tool mongoimport

#. Before using a client tool, assign the execute permission to it.

   -  Run the **chmod +x mongo** command to grant a client permission to connect to a DB instance.
   -  Run the **chmod +x mongoexport** command to grant a client permission to export data.
   -  Run the **chmod +x mongoimport** command to grant a client permission to import data.

#. Connect to a DB instance through the installed client.

   -  For details on how to connect to a cluster instance, see :ref:`Connecting to a Cluster Instance Over Private Networks <en-us_topic_0044018334>`.
   -  For details on how to connect to a replica set instance, see :ref:`Connecting to a Replica Set Instance Over Private Networks <en-us_topic_0105284966>`.
   -  For details on how to connect to a single node instance, see :ref:`Connecting to a Single Node Instance Over Private Networks <dds_02_0028>`.
