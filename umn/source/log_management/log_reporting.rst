:original_name: en-us_topic_0000002142634625.html

.. _en-us_topic_0000002142634625:

Log Reporting
=============

Prerequisites
-------------

You have created a log group and a log stream on the Log Tank Service (LTS) console.

Scenarios
---------

If you enable log reporting to LTS, new audit logs generated for DDS DB instances will be uploaded to LTS for management. You can view details about audit logs of DDS DB instances, including searching for logs, visualizing logs, downloading logs, and viewing real-time logs.

-  Enable log reporting to LTS for a single DB instance by referring to :ref:`Enabling Log Reporting to LTS for a Single DB Instance <en-us_topic_0000002142634625__section1383195911614>`.
-  Edit log reporting to LTS for a single DB instance by referring to :ref:`Editing Log Reporting to LTS for a Single DB Instance <en-us_topic_0000002142634625__section1284145910614>`.
-  Disable log reporting to LTS for a single DB instance by referring to :ref:`Disabling Log Reporting to LTS for a Single DB Instance <en-us_topic_0000002142634625__section1486559069>`.
-  Enable log reporting to LTS in batches by referring to :ref:`Enabling Log Reporting to LTS in Batches <en-us_topic_0000002142634625__section198713591065>`.
-  Disable log reporting to LTS in batches by referring to :ref:`Disabling Log Reporting to LTS in Batches <en-us_topic_0000002142634625__section1087859766>`.

Precautions
-----------

-  Logs record all requests sent to your DB instance and are stored in LTS.
-  This request does not take effect immediately. There is a delay of about 10 minutes.
-  After this function is enabled, all audit policies are reported by default.
-  If **Audit Policy** is enabled, LTS reuses the audit policy set for your DB instance and you will also be billed for reporting audit logs to LTS. (Only after you disable **Audit Policy**, the fee will be terminated.)
-  If you enable audit log reporting to LTS for an instance with the **Audit Policy** toggle switch turned on, you can turn off this switch only when the instance status becomes available.

.. _en-us_topic_0000002142634625__section1383195911614:

Enabling Log Reporting to LTS for a Single DB Instance
------------------------------------------------------

#. Log in to the console.
#. Click |image1| in the upper left corner and select a region and a project.
#. Click |image2| in the upper left corner of the page and choose **Databases** > **Document Database Service**.
#. On the **Instances** page, locate a target DB instance and click its name.
#. In the navigation pane on the left, choose **Audit Logs**.
#. On the **Audit Logs** page, click |image3| next to **Report Logs to LTS**.
#. In the displayed dialog box, specify **Log Group** and **Log Stream**.
#. Click **OK**.

.. _en-us_topic_0000002142634625__section1284145910614:

Editing Log Reporting to LTS for a Single DB Instance
-----------------------------------------------------

#. Log in to the console.
#. Click |image4| in the upper left corner and select a region and a project.
#. Click |image5| in the upper left corner of the page and choose **Databases** > **Document Database Service**.
#. On the **Instances** page, locate a target DB instance and click its name.
#. In the navigation pane on the left, choose **Audit Logs**.
#. On the **Audit Logs** page, click **Edit** next to the **Report Logs to LTS** toggle switch.

   .. note::

      The editing function is available only when the **Report Logs to LTS** toggle switch is turned on.

#. In the displayed dialog box, specify **Log Group** and **Log Stream**.

   .. note::

      Select the target log group and log stream.

#. Click **OK**.

.. _en-us_topic_0000002142634625__section1486559069:

Disabling Log Reporting to LTS for a Single DB Instance
-------------------------------------------------------

#. Log in to the console.
#. Click |image6| in the upper left corner and select a region and a project.
#. Click |image7| in the upper left corner of the page and choose **Databases** > **Document Database Service**.
#. On the **Instances** page, locate a target DB instance and click its name.
#. In the navigation pane on the left, choose **Audit Logs**.
#. On the **Audit Logs** page, click |image8| next to **Report Logs to LTS**.
#. In the displayed dialog box, click **Yes**.

.. _en-us_topic_0000002142634625__section198713591065:

Enabling Log Reporting to LTS in Batches
----------------------------------------

#. Log in to the console.
#. Click |image9| in the upper left corner and select a region and a project.
#. Click |image10| in the upper left corner of the page and choose **Databases** > **Document Database Service**.
#. In the navigation pane on the left, choose **Log Reporting**.
#. Select target DB instances and click **Enable Log Reporting**.
#. In the displayed dialog box, specify **Log Group** and **Log Stream**.

   .. note::

      -  Select the target log group and log stream.

#. Click **OK**.

.. _en-us_topic_0000002142634625__section1087859766:

Disabling Log Reporting to LTS in Batches
-----------------------------------------

#. Log in to the console.
#. Click |image11| in the upper left corner and select a region and a project.
#. Click |image12| in the upper left corner of the page and choose **Databases** > **Document Database Service**.
#. In the navigation pane on the left, choose **Log Reporting**.
#. Select target DB instances and click **Disable Log Reporting**.
#. In the displayed dialog box, click **OK**.

.. |image1| image:: /_static/images/en-us_image_0000002142796009.png
.. |image2| image:: /_static/images/en-us_image_0000002107237174.png
.. |image3| image:: /_static/images/en-us_image_0000002142716389.png
.. |image4| image:: /_static/images/en-us_image_0000002107237190.png
.. |image5| image:: /_static/images/en-us_image_0000002142716401.png
.. |image6| image:: /_static/images/en-us_image_0000002107077414.png
.. |image7| image:: /_static/images/en-us_image_0000002142796029.png
.. |image8| image:: /_static/images/en-us_image_0000002107237198.png
.. |image9| image:: /_static/images/en-us_image_0000002142796045.png
.. |image10| image:: /_static/images/en-us_image_0000002107237210.png
.. |image11| image:: /_static/images/en-us_image_0000002107077430.png
.. |image12| image:: /_static/images/en-us_image_0000002142796049.png
