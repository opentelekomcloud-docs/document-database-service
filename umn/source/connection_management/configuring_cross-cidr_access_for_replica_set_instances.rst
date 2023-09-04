:original_name: dds_03_0100.html

.. _dds_03_0100:

Configuring Cross-CIDR Access for Replica Set Instances
=======================================================

If a client and a replica set instance are deployed in different CIDR blocks and the client is not in 192.168.0.0/16, 172.16.0.0/24, or 10.0.0.0/8, configure Cross-CIDR Access for the instance to communicate with the client.

Precautions
-----------

-  During the configuration of cross-CIDR access, services are running properly without interruption or intermittent disconnection.
-  If the client and replica set instance are in different VPCs and CIDR blocks, configure a VPC peering connection by referring to **VPC Peering Connection** in *Virtual Private Cloud User Guide*.

**Procedure**
-------------

#. :ref:`Log in to the DDS console. <dds_02_0043>`

#. On the **Instance Management** page, click the target replica set instance.

#. In the navigation pane on the left, choose **Connections**.

#. On the **Address** area, click **Enable** to the right of **Cross-CIDR Access** and specify the client CIDR block details.

   .. note::

      Up to 30 CIDR blocks can be configured, and each of them can overlap but they cannot be the same. That is, the source CIDR blocks can overlap but cannot be the same.

#. After cross-CIDR access is enabled, **Enabled** is displayed to the right of **Cross-CIDR Access**.

   If you need to change the client CIDR block, click **Change** to the right of **Cross-CIDR Access**.

   .. note::

      -  To ensure the ECS and the DB instance can communicate with each other, configure the connection by referring to section "VPC Peering Connection Overview" in the *Virtual Private Cloud User Guide*.
