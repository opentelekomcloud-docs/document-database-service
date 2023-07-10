:original_name: dds_02_0024.html

.. _dds_02_0024:

Setting a Security Group
========================

Scenarios
---------

This section guides you on how to add a security group rule to control access from and to DDS DB instances in a security group.

Precautions
-----------

The default security group rule allows all outgoing data packets. ECSs and DDS DB instances in the same security group can access each other. After a security group is created, you can create different rules for that security group, which allows you to control access to the DB instances that are in it.

To access a DB instance in a security group from a source outside of that group, you need to create an inbound rule.

For details about the constraints on using security groups, see "Security Group Overview" in the *Virtual Private Cloud User Guide*.

Procedure
---------

For details about setting a security group, see "Adding a Security Group Rule" in the *Virtual Private Cloud User Guide*.
