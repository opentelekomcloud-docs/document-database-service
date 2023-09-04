:original_name: dds_faq_0025.html

.. _dds_faq_0025:

How Do I Back Up DDS Databases to an ECS?
=========================================

You can store DDS backup data on the ECS using mongoexport. However, you are advised not to store database backups on ECSs. To ensure high data reliability and service assurance, you can use the DDS backup function to store backups to a professional storage object, such as OBS.
