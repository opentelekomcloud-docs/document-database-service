:original_name: dds_02_0100.html

.. _dds_02_0100:

Enabling IP Addresses of shard and config Nodes
===============================================

Scenarios
---------

A cluster instance of Community Edition consists of mongos, shard, and config nodes. When your services need to read and write data from and into databases, connect to the mongos node. In certain scenarios, you need to read data from the shard or config node. Therefore, obtaining the IP address of the corresponding node is necessary.

This section describes how to obtain the IP addresses of the shard and config nodes.

Before You Start
----------------

-  DDS supports cluster instances of Community Edition 3.2, 3.4, 4.0, and 4.2.
-  DDS creates two connection addresses for the primary node and secondary node in a shard respectively.
-  Once the connection addresses are assigned to your nodes, they cannot be modified or deleted.
-  The connection address is accessible from private networks only.

Enabling shard IP Address
-------------------------

#. :ref:`Log in to the DDS console. <dds_02_0043>`

#. In the left navigation pane, choose **Instance Management**. In the DB instance list, click the target cluster instance to go to the **Basic Information** page.

   Alternatively, on the **Basic Information** page, in the navigation pane on the left, click **Connections**.

#. In the **Node Information** area, click the **shard** tab.

#. Click **Show shard IP Address**. In the displayed dialog box, enter and confirm the password for connecting to the node.

   .. note::

      -  After the shard IP address is enabled, you need to restart the corresponding shard nodes for the configuration to take effect.
      -  The shard IP address cannot be modified or disabled after being enabled, and the password cannot be modified.
      -  After the shard IP address is enabled and new shard nodes are added, you need to manually locate the newly added shard node and choose **More** > **Show shard IP Address** in the **Operation** column to show the shard IP address.
      -  After the shard IP address is enabled, all shard nodes in the current instance apply for connection addresses.

#. .. _dds_02_0100__li79582518253:

   Obtain the private IP address of the shard node.

   After the shard IP address is enabled, you can click **Connections** in the navigation pane on the left or on the current page to expand the node drop-down list and obtain the private IP address.

#. Obtain the connection address of a shard node.

   Example:

   Based on the private IP address obtained in :ref:`5 <dds_02_0100__li79582518253>`, the connection address of the current shard node is as follows:

   mongodb://**sharduser:<password>@192.168.237.15:8637,192.168.255.217:8637**/test?authSource=admin&replicaSet=shard_?

   .. note::

      -  **sharduser** is the default user when setting up "show shard IP address" function.
      -  **<password>**\ indicates the password of the sharduser.
      -  **192.168.237.15** and **192.168.255.217** are the private IP addresses of the shard's primary and secondary nodes.
      -  **8637** is the port of the shard node and cannot be changed.
      -  **shard_?** indicates the name of the shard node to be connected, for example, shard_1.

Enabling config IP Address
--------------------------

#. :ref:`Log in to the DDS console. <dds_02_0043>`

#. In the left navigation pane, choose **Instance Management**. In the DB instance list, click the target cluster instance to go to the **Basic Information** page.

   Alternatively, on the **Basic Information** page, in the navigation pane on the left, click **Connections**.

#. In the **Node Information** area, click the **config** tab.

#. Click **Show config IP Address**. In the displayed dialog box, enter and confirm the password for connecting to the node.

   .. note::

      -  After the config IP address is enabled, you need to restart the corresponding config node for the configuration to take effect.
      -  The config IP address cannot be modified or disabled after being enabled, and the password cannot be modified.

#. .. _dds_02_0100__li1225175894219:

   Obtain the private IP address of the config node.

   After the config IP address is enabled, you can click **Connections** in the navigation pane on the left or on the current page to expand the node drop-down list and obtain the private IP address.

#. Obtain the connection address of a config node.

   Example:

   Based on the private IP address obtained in :ref:`5 <dds_02_0100__li1225175894219>`, the connection address of the current config node is as follows:

   mongodb://**csuser:<password>@192.168.154.71:8636,192.168.143.227:8636**/test?authSource=admin&replicaSet=config

   .. note::

      -  **csuser** indicates the username of the current config node.
      -  **<password>**\ indicates the password of the csuser.
      -  **192.168.154.71** and **192.168.143.227** are the private IP addresses of the current node.
      -  **8636** is the port of the config node and cannot be changed.
