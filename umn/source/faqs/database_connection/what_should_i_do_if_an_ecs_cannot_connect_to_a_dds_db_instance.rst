:original_name: dds_faq_0013.html

.. _dds_faq_0013:

What Should I Do If an ECS Cannot Connect to a DDS DB Instance?
===============================================================

Perform the following steps to identify the problem:

.. _dds_faq_0013__section10677164802818:

Replica Set Instance
--------------------

#. Check whether the ECS and replica set instance are in the same VPC.

   -  If yes, go to :ref:`3 <dds_faq_0013__li78427303150>`.
   -  If no, configure the VPC peering connection. For details, see "VPC Peering Connection" in *Virtual Private Cloud User Guide*. Then, go to :ref:`2 <dds_faq_0013__li484115308155>`.

#. .. _dds_faq_0013__li484115308155:

   Check whether the client and replica set instance are deployed in different CIDR blocks and whether the CIDR block of the client is not 192.168.0.0/16, 172.16.0.0/24, or 10.0.0.0/8.

   -  If yes, go to :ref:`Configuring Cross-CIDR Access for Replica Set Instances <dds_03_0100>` and then go to :ref:`3 <dds_faq_0013__li78427303150>`.
   -  If no, go to :ref:`3 <dds_faq_0013__li78427303150>`.

#. .. _dds_faq_0013__li78427303150:

   Check whether a security group has been associated with the ECS.

   -  If yes, check whether the security group rules are suitable. For details, see :ref:`Setting a Security Group <dds_02_0049>`. Then, go to :ref:`4 <dds_faq_0013__li984263071514>`.
   -  If no, go to the VPC console from the ECS details page and click **Security Groups** to add a security group.

#. .. _dds_faq_0013__li984263071514:

   On the ECS, check whether the DDS instance address port can be connected.

   .. code-block::

      telnet <DB instance address> {8635}

   -  If yes, the network is normal. Check the database username and password. For details, see :ref:`Connecting to a Replica Set Instance Over Private Networks <en-us_topic_0105284966>`.
   -  If the ECS still cannot connect to the instance port, contact technical support.

Cluster and Single Node Instances
---------------------------------

#. Check whether the ECS and DDS instance are located in the same VPC.

   -  If yes, go to :ref:`2 <dds_faq_0013__li10923237103639>`.
   -  If no, create an ECS in the VPC where the DDS instance is located.

#. .. _dds_faq_0013__li10923237103639:

   Check whether a security group has been associated with the ECS.

   -  If yes, check whether the security group rules are suitable. For details, see :ref:`Setting a Security Group <dds_02_0022>`. Then, go to :ref:`3 <dds_faq_0013__li2748172710406>`.
   -  If no, go to the VPC console from the ECS details page and click **Security Groups** to add a security group.

#. .. _dds_faq_0013__li2748172710406:

   On the ECS, check whether the DDS instance address port can be connected.

   .. code-block::

      telnet <DB instance address> {8635}

   -  If yes, the network is normal. Check the database username and password. For details, see :ref:`Connecting to a Cluster Instance Over Private Networks <en-us_topic_0044018334>`.
   -  If the ECS still cannot connect to the instance port, contact technical support.
