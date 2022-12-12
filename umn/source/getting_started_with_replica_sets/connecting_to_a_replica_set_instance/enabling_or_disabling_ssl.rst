:original_name: dds_02_0016.html

.. _dds_02_0016:

Enabling or Disabling SSL
=========================

Scenarios
---------

DDS allows you to use SSL to encrypt connections to a DB instance to protect your data.

-  If SSL is enabled, you can connect to a database using SSL. For details, see :ref:`SSL Connection <en-us_topic_0105284966__section3730754113815>`.
-  If SSL is disabled, you can connect to the database using a common connection. For details, see :ref:`Common Connection <en-us_topic_0105284966__en-us_topic_0085335422_sfc3bfb212a8440799f49320d91fc096c>`.

.. important::

   Enabling or disabling SSL will cause DB instance restart. Exercise caution when you perform this operation.

Enabling SSL
------------

#. On the **Instance Management** page, click the target replica set instance.
#. In the navigation pane on the left, choose **Connections**.
#. In the **Basic Information** area, click |image1| next to the **SSL** field.
#. In the displayed dialog box, click **Yes**.
#. In the **Basic Information** area, view the modification result.

.. _dds_02_0016__section584914451250:

Disabling SSL
-------------

#. On the **Instance Management** page, click the target replica set instance.
#. In the navigation pane on the left, choose **Connections**.
#. In the **Basic Information** area, click |image2| next to the **SSL** field.
#. In the displayed dialog box, click **Yes**.
#. In the **Basic Information** area, view the modification result.

.. |image1| image:: /_static/images/en-us_image_0284275089.png
.. |image2| image:: /_static/images/en-us_image_0284275146.png
