:original_name: dds_03_change_security_group.html

.. _dds_03_change_security_group:

Changing a Security Group
=========================

**Scenarios**
-------------

This section guides you on how to change a security group for cluster, replica set, and single node instances. If any of the following operations is in progress, do not change the security group:

-  Adding nodes
-  Migrating data

Procedure
---------

#. :ref:`Log in to the DDS console. <dds_02_0043>`

#. On the **Instance Management** page, click the instance name. The **Basic Information** page is displayed.

#. In the **Network Information** area on the **Basic Information** page, click |image1| to select the security group to which the DB instance belongs.

   You can also choose **Connections** in the navigation pane on the left. On the **Private Connection** tab, in the **Security Group** area, click |image2| to select the security group to which the DB instance belongs.

   .. important::

      Ensure that the new security group does not affect the DB instance connection. Otherwise, the connection may be interrupted.

   -  To submit the change, click |image3|. This process takes about 1 to 3 minutes.
   -  To cancel the change, click |image4|.

#. View the modification result.

.. |image1| image:: /_static/images/en-us_image_0000001280327773.png
.. |image2| image:: /_static/images/en-us_image_0000001236447314.png
.. |image3| image:: /_static/images/en-us_image_0000001143053837.png
.. |image4| image:: /_static/images/en-us_image_0000001142773933.png
