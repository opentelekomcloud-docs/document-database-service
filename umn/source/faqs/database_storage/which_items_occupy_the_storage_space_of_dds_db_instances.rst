:original_name: dds_faq_0030.html

.. _dds_faq_0030:

Which Items Occupy the Storage Space of DDS DB Instances?
=========================================================

The following types of data will occupy the storage space:

-  User data except backups
-  Data required for ensuring DB instance proper running occupy, such as system database data, rollback logs, and indexes
-  Log output files that are generated by DDS ensure the stable operating of DDS DB instances. For example, Oplogs occupy 10% of storage space and cannot be resized.
