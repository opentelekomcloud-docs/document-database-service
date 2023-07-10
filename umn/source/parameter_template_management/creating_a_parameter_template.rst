:original_name: en-us_topic_parameter_group.html

.. _en-us_topic_parameter_group:

Creating a Parameter Template
=============================

DB parameter templates act as a container for engine configuration values that are applied to one or more DB instances.

Precautions
-----------

-  DDS does not share parameter template quotas with RDS.
-  Each account can create up to 100 DDS parameter templates for the cluster, replica set, and single node instances.

Cluster
-------

#. Log in to the management console.
#. Click |image1| in the upper left corner and select a region and a project.
#. Click **Service List**. Under **Database**, click **Document Database Service** to go to the DDS console.
#. In the navigation pane on the left, choose **Parameter Template Management**.
#. On the **Parameter Template Management** page, click **Create Parameter Template**.
#. Select **Cluster** for **DB Instance Type**, specify **DB Engine Version**, **Node Type**, **New Parameter Template**, and **Description** (optional), and then click **OK**.

   -  **Node Type**: specifies the node type that this parameter template will apply to. For example, to create a parameter template applying to config, select **config**.
   -  **New Parameter Template**: The template name can be 4 to 64 characters long and starts with a letter. It can contain only letters, digits, hyphens (-), underscores (_), and periods (.).
   -  **Description**: contains a maximum of 256 characters and cannot contain the carriage return character and the following special characters: >!<"&'=

#. On the **Parameter Template Management** page, view and manage parameter templates on the **Clusters** tab.

Replica Set
-----------

#. Log in to the management console.
#. Click |image2| in the upper left corner and select a region and a project.
#. Click **Service List**. Under **Database**, click **Document Database Service** to go to the DDS console.
#. In the navigation pane on the left, choose **Parameter Template Management**.
#. On the **Parameter Template Management** page, click **Create Parameter Template**.
#. Select **Replica set** for **DB Instance Type**, specify **DB Engine Version**, **New Parameter Template**, and **Description** (optional), and then click **OK**.

   -  **New Parameter Template**: The template name can be 4 to 64 characters long and starts with a letter. It can contain only letters, digits, hyphens (-), underscores (_), and periods (.).
   -  **Description**: contains a maximum of 256 characters and cannot contain the carriage return character and the following special characters: >!<"&'=

#. On the **Parameter Template Management** page, view and manage parameter templates on the **Replica Sets** tab.

Single Node
-----------

#. Log in to the management console.
#. Click |image3| in the upper left corner and select a region and a project.
#. Click **Service List**. Under **Database**, click **Document Database Service** to go to the DDS console.
#. In the navigation pane on the left, choose **Parameter Template Management**.
#. On the **Parameter Template Management** page, click **Create Parameter Template** .
#. Select **Single node** for **DB Instance Type**, specify **DB Engine Version**, **New Parameter Template**, and **Description** (optional), and then click **OK**.

   -  **New Parameter Template**: The template name can be 4 to 64 characters long and starts with a letter. It can contain only letters, digits, hyphens (-), underscores (_), and periods (.).
   -  **Description**: contains a maximum of 256 characters and cannot contain the carriage return character and the following special characters: >!<"&'=

#. On the **Parameter Template Management** page, view and manage parameter templates on the **Single Nodes** tab.

.. |image1| image:: /_static/images/en-us_image_0000001268771757.png
.. |image2| image:: /_static/images/en-us_image_0000001268771757.png
.. |image3| image:: /_static/images/en-us_image_0000001268771757.png
