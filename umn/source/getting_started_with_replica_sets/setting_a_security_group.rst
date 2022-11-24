:original_name: dds_02_0013.html

.. _dds_02_0013:

Setting a Security Group
========================

**Scenarios**
-------------

This section guides you on how to add a security group rule to control access from and to DDS DB instances in a security group. This document describes how to set security groups.

Background Information
----------------------

You can access a DDS DB instance in either of the following ways:

-  Public network
-  Internal network

Precautions
-----------

The default security group rule allows all outgoing data packets. ECSs and DDS DB instances can access each other in the same security group. After a security group is created, you can add security group rules to control the access from and to the DDS DB instances in the security group.

By default, a tenant can create a maximum of 500 security group rules. An excessive number of security group rules increases the network latency of the first packet. It is recommended that you add a maximum of 50 rules for each security group.

To access the DDS DB instances in a security group from external resources, create an inbound rule for the security group.

**Procedure**
-------------

#. Log in to the management console.
#. Click |image1| in the upper left corner and select a region and project.
#. Click **Service List**. Under **Network**, click **Virtual Private Cloud**.
#. In the navigation pane on the left, choose **Access Control** > **Security Groups**.
#. On the **Security Group** page, click the security group name.
#. On the **Inbound Rules** tab, click **Add Rule**. In the displayed **Add Inbound Rule** dialog box, set required parameters to add inbound rules. On the **Outbound Rules** tab, click **Add Rule**. In the displayed **Add Outbound Rule** dialog box, set required parameters to add outbound rules.
#. Add a security group rule as prompted.

   .. table:: **Table 1** Parameter description

      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Parameter             | Description                                                                                                                                      | Value Example         |
      +=======================+==================================================================================================================================================+=======================+
      | Protocol              | Specifies the network protocol. Allows all traffic or supports user-defined protocols, TCP, UDP, ICMP, and SSH.                                  | TCP                   |
      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Port                  | Specifies the port allowing the access to ECSs or external devices.                                                                              | 8635                  |
      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Source/Destination    | Specifies the supported IP address and security group.                                                                                           | -  192.168.10.0/24    |
      |                       |                                                                                                                                                  | -  default            |
      |                       | -  **IP address**: indicates that the security group rule takes effect in a specified IP address range.                                          |                       |
      |                       |                                                                                                                                                  |                       |
      |                       |    -  xxx.xxx.xxx.xxx/32 (IPv4)                                                                                                                  |                       |
      |                       |    -  xxx.xxx.xxx.0/24 (subnet)                                                                                                                  |                       |
      |                       |    -  0.0.0.0/0 (any IP address)                                                                                                                 |                       |
      |                       |                                                                                                                                                  |                       |
      |                       | -  **Security group**: indicates that this rule allows all IP addresses of ECSs to access DDS DB instances in the same specified security group. |                       |
      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+

#. Click **OK**.

.. |image1| image:: /_static/images/en-us_image_0284275018.png
