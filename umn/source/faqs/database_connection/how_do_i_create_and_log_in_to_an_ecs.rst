:original_name: dds_faq_0034.html

.. _dds_faq_0034:

How Do I Create and Log In to an ECS?
=====================================

For details on how to create and log in to an ECS, see "Creating and Logging In to a Windows ECS" or "Creating and Logging In to a Linux ECS" in the *Elastic Cloud Server User Guide*.

-  The ECS to be created must be in the same VPC with the DDS DB instance to which it connects.
-  When you create an ECS, select an OS, such as Red Hat 6.6, and bind an EIP to it.
-  Configure the security group to enable the ECS to access the DB instance through the private IP address, that is, the node address in the **Private IP Address** column on the **Basic Information** page.
