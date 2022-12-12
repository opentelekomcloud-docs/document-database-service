:original_name: en-us_topic_parameter_group.html

.. _en-us_topic_parameter_group:

Creating a Parameter Group
==========================

**Scenarios**
-------------

DB parameter groups act as a container for engine configuration values that are applied to one or more DB instances. This section guides you on how to create a parameter group to manage your DB instance configurations.

.. note::

   -  DDS does not share parameter group quotas with RDS.
   -  Each account can create up to 100 DDS parameter groups for the cluster and replica set instances to share.

Cluster
-------

#. :ref:`Log in to the DDS console. <dds_02_0043>`
#. In the navigation pane on the left, click **Parameter Group Management**.
#. On the **Parameter Group Management** page, click **Create Parameter Group**.
#. Select a DB engine version from the **DB Engine Version** drop-down list, **Cluster** for **DB Instance Type**, specify **Node Type**, **Parameter Group Name**, and **Description**, and then click **OK**.

   -  **Node Type**: specifies the node type that this parameter group will apply to. For example, to create a parameter group applying to config, select **config**.
   -  **Parameter Group Name**: specifies the parameter group name, which is a string of 1 to 64 characters composed of only letters (case-sensitive), digits, hyphens (-), underscores (_), and periods (.).
   -  **Description**: contains a maximum of 256 characters and cannot contain the carriage return character and the following special characters: >!<"&'=

#. On the **Parameter Group Management** page, view and manage parameter groups on the **Clusters** tab.

Replica Set
-----------

#. :ref:`Log in to the DDS console. <dds_02_0043>`
#. In the navigation pane on the left, click **Parameter Group Management**.
#. On the **Parameter Group Management** page, click **Create Parameter Group**.
#. Select a DB engine version from the **DB Engine Version** drop-down list, **Replica set** for **DB Instance Type**, specify **Parameter Group Name** and **Description**, and then click **OK**.

   -  **Parameter Group Name**: specifies the parameter group name, which is a string of 1 to 64 characters composed of only letters (case-sensitive), digits, hyphens (-), underscores (_), and periods (.).
   -  **Description**: contains a maximum of 256 characters and cannot contain the carriage return character and the following special characters: >!<"&'=

#. On the **Parameter Group Management** page, view and manage parameter groups on the **Replica Sets** tab.
