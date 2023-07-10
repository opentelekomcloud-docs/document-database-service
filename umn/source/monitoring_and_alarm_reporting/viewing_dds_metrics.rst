:original_name: dds_03_0076.html

.. _dds_03_0076:

Viewing DDS Metrics
===================

Scenarios
---------

Cloud Eye monitors DDS instance metrics. You can obtain the monitoring metrics of DDS on the management console.

Monitored data requires a period of time for transmission and display.

**Prerequisites**
-----------------

-  Cloud Eye does not display the metrics of a deleted DB instance or node. You can view the monitoring information only after the instance is restarted or recovered.

-  The DDS instance metrics are displayed on the Cloud Eye page with 5-10 minutes delay.

Method 1
--------

#. :ref:`Log in to the DDS console. <dds_02_0043>`
#. On the **Instance Management** page, click the target DB instance.
#. In the navigation pane on the left, choose **Advanced O&M**.
#. On the **Real-Time Monitoring** tab, view metrics of DDS instances and/or instance specific nodes if there are any.
#. On the **Real-Time Monitoring** tab, you can select a duration to view the monitoring data.

   -  You can view the monitoring data of the last 1 hour, 3 hours, and 12 hours.
   -  After the automatic refresh function is enabled, monitoring data is automatically refreshed at an interval of 60s.
   -  For more metric information, click :ref:`View details <dds_03_0076__section1657925514410>` to switch to the Cloud Eye console.

.. _dds_03_0076__section1657925514410:

Method 2
--------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select a region and a project.

#. Under **Management & Deployment**, click **Cloud Eye**.

#. In the navigation pane on the left, choose **Cloud Service Monitoring** > **Document Database Service**.

#. On the displayed page, locate the target instance and click **View Metric** in the **Operation** column.

#. In the DDS monitoring area, you can select a duration to view the monitoring data.

   You can view the monitoring data of DDS in the recent 1 hour, 3 hours, or 12 hours. To view the monitoring curve of a longer time range, click |image2| to enlarge the graph.

.. |image1| image:: /_static/images/en-us_image_0000001280455205.png
.. |image2| image:: /_static/images/en-us_image_0000001236135268.png
