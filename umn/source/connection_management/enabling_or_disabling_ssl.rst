:original_name: dds_03_0074.html

.. _dds_03_0074:

Enabling or Disabling SSL
=========================

**Scenarios**
-------------

DDS allows you to use SSL to encrypt connections to a DB instance to protect your data.

-  If SSL is enabled, you can connect to a DB instance using SSL. For details, see sections about connecting to a DB instance using SSL over public or private networks in this document.
-  If SSL is disabled, you can connect to the DB instance using an unencrypted connection. For details, see sections about connecting to a DB instance using an unencrypted connection over public or private networks in this document.

.. important::

   -  For security purposes, disabling SSL is not advised.
   -  Enabling or disabling SSL will cause DB instance restart. Exercise caution when you perform this operation.

.. _dds_03_0074__en-us_topic_0049044698_section45421719172826:

Enabling SSL
------------

#. On the **Instance Management** page, click the target DB instance.

#. In the **DB Information** area on the **Basic Information** page, click |image1| next to the **SSL** field.

   Alternatively, in the navigation pane on the left, choose **Connections**. In the **Basic Information** area, click |image2| next to the **SSL** field.

#. In the displayed dialog box, click **Yes**.

#. In the **Basic Information** area, view the modification result.

.. _dds_03_0074__section4225593518277:

Disabling SSL
-------------

#. On the **Instance Management** page, click the target DB instance.

#. In the **DB Information** area on the **Basic Information** page, click |image3| next to the **SSL** field.

   Alternatively, in the navigation pane on the left, choose **Connections**. In the **Basic Information** area, click |image4| next to the **SSL** field.

#. In the displayed dialog box, click **Yes**.

#. In the **Basic Information** area, view the modification result.

.. |image1| image:: /_static/images/en-us_image_0000001142893907.png
.. |image2| image:: /_static/images/en-us_image_0000001143133859.png
.. |image3| image:: /_static/images/en-us_image_0000001142773959.png
.. |image4| image:: /_static/images/en-us_image_0000001143053861.png
