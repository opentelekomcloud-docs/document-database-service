:original_name: dds_faq_0012.html

.. _dds_faq_0012:

What Is the Number of DDS Database Connections?
===============================================

The number of connections indicates the number of applications that can be simultaneously connected to the database. The number of connections is irrelevant to the maximum number of users allowed by your applications or websites.

-  For a cluster instance, the number of connections indicates the number of connections between the client and the dds mongos.
-  For a replica set instance, the number of connections indicates the number of connections between the client and the primary and secondary nodes.
-  For a single-node instance, the number of connections indicates the number of connections between the client and the node.
