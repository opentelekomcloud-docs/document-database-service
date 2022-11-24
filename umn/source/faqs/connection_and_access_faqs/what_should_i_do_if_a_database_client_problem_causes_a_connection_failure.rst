:original_name: dds_faq_0014.html

.. _dds_faq_0014:

What Should I Do If a Database Client Problem Causes a Connection Failure?
==========================================================================

Identify a DDS DB instance connection failure caused by a client problem from the following aspects.

#. ECS Security Policy

   In Windows, check whether the DDS port is enabled in the Windows security policy.

   In Linux, run the **iptables** command to check whether the DDS port is enabled in firewall settings.

#. Application Configuration

   Check whether the IP address, port parameter, and Java database connectivity (JDBC) are configured correctly.

.. note::

   If the problem persists, contact post-sales technical support.
