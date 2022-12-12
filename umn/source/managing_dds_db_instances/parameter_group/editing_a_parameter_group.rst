:original_name: en-us_topic_configuration.html

.. _en-us_topic_configuration:

Editing a Parameter Group
=========================

**Scenarios**
-------------

This section guides you on how to edit parameters in the parameter groups that you have created to meet your service requirements and achieve optimal performance.

.. note::

   Default parameter groups are unchangeable. You can only view them by clicking their names. If inappropriate settings of user-created parameter groups lead to a database reboot failure, you can refer to the settings of the default parameter groups to reset them.

Procedure
---------

#. :ref:`Log in to the DDS console. <dds_02_0043>`

#. In the navigation pane on the left, click **Parameter Group Management**.

#. On the **Parameter Group Management** page, select the **Clusters** or **Replica Sets** tab and click the parameter group you created.

#. Modify the required parameters.

   Related parameters are described as follows:

   -  For details on parameter descriptions, visit `MongoDB official website <https://docs.mongodb.com/v3.2/reference/parameters/>`__.
   -  The default value of the **net.maxIncomingConnections** parameter varies according to DB instance specifications. Therefore, this parameter is set to **default** before being specified.

   Possible operations are as follows:

   -  If you want to save the modifications, click **Save**.
   -  If you want to cancel the modifications, click **Cancel**.
   -  If you want to preview the modifications, click **Preview**.

   .. note::

      For details on the description of parameter group status, see section :ref:`Database Status <dds_01_0026>`.

      After modifying a parameter, you need to view the associated instance status in the instance list. If **Pending restart** is displayed, you need to restart the instance for the modification to take effect.
