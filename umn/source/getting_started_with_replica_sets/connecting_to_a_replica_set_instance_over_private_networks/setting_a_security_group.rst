:original_name: dds_02_0049.html

.. _dds_02_0049:

Setting a Security Group
========================

**Scenarios**
-------------

This section guides you on how to add a security group rule to control access from and to DDS DB instances associated with a security group. The following describes how to set security groups.

Precautions
-----------

The default security group rule allows all outgoing data packets. By default\ **,** ECSs and DDS DB instances in the same security group can access each other. After a security group is created, you can create different rules for that security group, which allows you to control access to the DB instances that are in it.

To access a DB instance in a security group from a source outside of that group, you need to create an inbound rule.

For details about the constraints on using security groups, see "Security Group Overview" in the *Virtual Private Cloud User Guide*.

Procedure
---------

For details about setting a security group, see "Adding a Security Group Rule" in the *Virtual Private Cloud User Guide*.
