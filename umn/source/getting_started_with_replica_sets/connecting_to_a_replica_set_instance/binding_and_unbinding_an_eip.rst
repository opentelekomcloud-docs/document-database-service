:original_name: dds_02_0015.html

.. _dds_02_0015:

Binding and Unbinding an EIP
============================

.. _dds_02_0015__section055104935914:

**Scenarios**
-------------

You can access DDS through a private IP address or an EIP. The application scenario of the connection address is as follows:

-  Use a private IP address when:

   DDS provides a private IP address by default.

   Your applications are deployed on an ECS in a region where your replica set instance is located.

-  Use an EIP when:

   -  Your applications are deployed on an ECS in a region separated from the region where your replica set instance is located.
   -  Your applications are deployed on another cloud platform.

Precautions
-----------

-  Before accessing a database, you need to apply for an EIP on the VPC console. Then, add an inbound rule to allow the IP addresses or IP address ranges of ECSs. For details, see section :ref:`Setting a Security Group <dds_02_0013>`.
-  In the replica set instance, only primary and secondary nodes can be bound to an EIP. To change the EIP that has been bound to a node, you need to unbind it from the node first.

.. _dds_02_0015__section0350133891310:

Binding an EIP
--------------

#. On the **Instance Management** page, click the target replica set instance.

#. In the navigation pane on the left, choose **Connections**.

#. In the **Basic Information** area, locate the target node and click **Bind EIP** in the **Operation** column.

#. In the displayed dialog box, all EIPs in the unbound status are listed. Select the required EIP and click **OK**. If no available EIPs are displayed, click **View EIP** and create an EIP on the VPC console.

#. In the **EIP** column, check that the EIP is successfully bound.

   To unbind an EIP from the DB instance, see :ref:`Unbinding an EIP <dds_02_0015__section142610351410>`.

.. _dds_02_0015__section142610351410:

Unbinding an EIP
----------------

#. On the **Instance Management** page, click the replica set instance that has been bound with an EIP.

#. In the navigation pane on the left, choose **Connections**.

#. In the **Basic Information** area, locate the target node and click **Unbind EIP** in the **Operation** column.

#. In the displayed dialog box, click **OK** to unbind the EIP.

   To bind an EIP to the DB instance again, see :ref:`Binding an EIP <dds_02_0015__section0350133891310>`.
