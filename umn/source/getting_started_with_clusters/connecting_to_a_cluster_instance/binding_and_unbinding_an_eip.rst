:original_name: dds_02_0006.html

.. _dds_02_0006:

Binding and Unbinding an EIP
============================

.. _dds_02_0006__section055104935914:

**Scenarios**
-------------

You can access DDS through a private IP address or an EIP. The application scenario of the connection address is as follows:

-  Use a private IP address when:

   DDS provides a private IP address by default.

   Your applications are deployed on an ECS in a region where your cluster instance is located.

-  Use an EIP when:

   -  Your applications are deployed on an ECS in a region separated from the region where your cluster instance is located.
   -  Your applications are deployed on another cloud platform.

Precautions
-----------

-  Before accessing a database, you need to apply for an EIP on the VPC console. Then, add an inbound rule to allow the IP addresses or IP address ranges of ECSs. For details, see section :ref:`Setting a Security Group <dds_02_0005>`.
-  In the cluster instance, only mongos can be bound to an EIP. To change the EIP that has been bound to a node, you need to unbind it from the node first.

.. _dds_02_0006__section0463161611514:

Binding an EIP
--------------

#. On the **Instance Management** page, click the target cluster instance.

#. In the navigation pane on the left, choose **Connections**.

#. In the **Basic Information** area, locate the target mongos node and click **Bind EIP** in the **Operation** column.

#. In the displayed dialog box, all EIPs in the unbound status are listed. Select the required EIP and click **OK**. If no available EIPs are displayed, click **View EIP** and create an EIP on the VPC console.

#. In the **EIP** column on the **mongos** tab, view the EIP that is successfully bound.

   To unbind an EIP from the DB instance, see :ref:`Unbinding an EIP <dds_02_0006__section1139494151519>`.

.. _dds_02_0006__section1139494151519:

Unbinding an EIP
----------------

#. On the **Instance Management** page, click the target cluster instance.

#. In the navigation pane on the left, choose **Connections**.

#. In the **Basic Information** area, locate the target mongos node and click **Unbind EIP** in the **Operation** column.

#. In the displayed dialog box, click **OK** to unbind the EIP.

   To bind an EIP to the DB instance again, see :ref:`Binding an EIP <dds_02_0006__section0463161611514>`.
