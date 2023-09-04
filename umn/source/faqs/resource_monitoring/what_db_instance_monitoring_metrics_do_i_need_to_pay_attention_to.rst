:original_name: dds_faq_0019.html

.. _dds_faq_0019:

What DB Instance Monitoring Metrics Do I Need to Pay Attention To?
==================================================================

You need to focus on the CPU, memory, and storage space usage.

You can configure DDS to report alarms as needed. If an alarm is reported, you can take proper measures to clear it.

**Configuration examples:**

-  Configure DDS to report alarms to Cloud Eye if CPU utilization reaching or exceeding a certain value (90% for example) for multiple times (3 for example) within a period of time (5 minutes for example).
-  Configure DDS to report alarms to Cloud Eye if its memory utilization reaches or exceeds a specific value (for example, 90%) multiple times (for example, 4 times) within a set period (for example, 5 minutes).
-  Configure DDS to report alarms to Cloud Eye if its storage utilization reaches or exceeds a specific value (for example, 85%) multiple times (for example, 5 times) within a set period (for example, 5 minutes).

.. note::

   For details on Cloud Eye alarm configuration, see "Alarm Rule Management" in *Cloud Eye Service User Guide*.

**Measures:**

If a storage usage alarm is reported, perform either of the following operations:

-  Check the storage space consumption and see whether any space can be freed up by deleting data from DB instances or dumping the data to another system.
-  Scale up the storage space. For details, see section :ref:`Scaling Up Storage Space <en-us_topic_increase_storage>`.
