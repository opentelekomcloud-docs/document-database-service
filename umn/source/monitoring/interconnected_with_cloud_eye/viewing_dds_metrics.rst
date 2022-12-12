:original_name: dds_03_0078.html

.. _dds_03_0078:

Viewing DDS Metrics
===================

Scenarios
---------

Cloud Eye monitors DDS running statuses. You can obtain the monitoring metrics of DDS on the management console.

Monitored data requires a period of time for transmission and display. The status of DDS displayed on the Cloud Eye page is the status obtained 5 to 10 minutes before. You can view the monitored data of a newly created DB instance 5 to 10 minutes later.

**Prerequisites**
-----------------

-  The DDS DB instance is running properly.

   Cloud Eye does not display the metrics of a faulty or deleted DB instance or node. You can view the monitoring information only after the instance is restarted or recovered.

.. note::

   Cloud Eye will delete a DDS DB instance or node that becomes faulty for 24 hours from the monitoring list and will not monitor it any more. However, you need to manually clear its alarm rules.

-  The DB instance has been properly running for at least 10 minutes.

   For a newly created DB instance, you need to wait for a while before viewing the monitoring metrics.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select a region and a project.

#. Under **Management & Deployment**, click **Cloud Eye**.

#. In the navigation pane on the left, choose **Cloud Service Monitoring** > **Document Database Service**.

#. On the displayed page, locate the target instance and click **View Metric** in the **Operation** column.

#. In the DDS monitoring area, you can select a duration to view the monitoring data.

   You can view the monitoring data of DDS in the recent 1 hour, 3 hours, or 12 hours. To view the monitoring curve of a longer time range, click |image2| to enlarge the graph.

.. |image1| image:: /_static/images/en-us_image_0284275156.png
.. |image2| image:: /_static/images/en-us_image_0284275295.png
