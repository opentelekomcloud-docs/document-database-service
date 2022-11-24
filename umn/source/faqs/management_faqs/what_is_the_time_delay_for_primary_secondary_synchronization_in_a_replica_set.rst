:original_name: dds_faq_0006.html

.. _dds_faq_0006:

What Is the Time Delay for Primary/Secondary Synchronization in a Replica Set?
==============================================================================

The delay for primary/secondary synchronization cannot be calculated using a formula. The delay is affected by the following factors:

#. Network communication status
#. Transaction pressure on the primary node, that is, transactions per second (TPS) of the primary node
#. Transaction size executed by the primary node, that is, the duration of a transaction execution
#. Load of the secondary node

If the primary node bears heavy pressure within a period and executes a large number of transactions per second, the synchronization to the secondary node is delayed.

You can view **Delay Between Primary and Secondary Nodes** of the secondary node on the Cloud Eye console to know the synchronization delay.
