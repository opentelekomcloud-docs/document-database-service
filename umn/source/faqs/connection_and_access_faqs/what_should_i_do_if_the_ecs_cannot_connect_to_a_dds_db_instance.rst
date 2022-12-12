:original_name: dds_faq_0013.html

.. _dds_faq_0013:

What Should I Do If the ECS Cannot Connect to a DDS DB Instance?
================================================================

Perform the following steps to identify the problem: The following uses the cluster instance as an example.

#. Check whether the ECS and DDS DB instance are located in the same VPC.

   -  If they are in the same VPC, go to :ref:`2 <dds_faq_0013__li10923237103639>`.
   -  If they are in different VPCs, create an ECS in the VPC where the DDS DB instance is located.

#. .. _dds_faq_0013__li10923237103639:

   Check whether a security group has been added to the ECS.

   -  If yes, check whether its configuration rules are suitable. For details, see the security group description in section :ref:`Setting a Security Group <dds_02_0005>`. Then, go to :ref:`3 <dds_faq_0013__li2748172710406>`.
   -  If no security group has been added, go to the VPC console from the ECS details page and click **Security Groups** to add a security group.

#. .. _dds_faq_0013__li2748172710406:

   On the ECS, check whether the DDS DB instance address port can be connected.

   .. code-block::

      telnet <DB instance address> {8635}

   -  If the port can be connected, the network is normal. Check the database account and password. For details, see section :ref:`Connecting to a DB Instance Through a Client <en-us_topic_0044018334>`.
   -  If the port cannot be connected, contact post-sales technical support for troubleshooting.
