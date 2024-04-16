:original_name: dds_02_0046.html

.. _dds_02_0046:

Binding an EIP
==============

**Scenarios**
-------------

After you create a DB instance, you can bind it to an EIP to allow external access. If you want to prohibit external access later, you can also unbind the EIP from the DB instance.

Precautions
-----------

-  Before accessing a database, you need to apply for an EIP on the VPC console. Then, add an inbound rule to allow the IP addresses or IP address ranges of ECSs. For details, see section :ref:`Setting a Security Group <dds_02_0019>`.
-  In the cluster instance, only dds mongos can be bound to an EIP. To change the EIP that has been bound to a node, you need to unbind it from the node first.

.. _dds_02_0046__section3199593620428:


Binding an EIP
--------------

#. On the **Instance Management** page, click the target cluster instance.

#. In the navigation pane on the left, choose **Connections**. In the **Basic Information** area, locate the target dds mongos node and click **Bind EIP** in the **Operation** column.

   Or in the **Node Information** area on the **Basic Information** page, locate the target dds mongos node and choose **More** > **Bind EIP** in the **Operation** column.

#. In the displayed dialog box, all available unbound EIPs are listed. Select the required EIP and click **OK**. If no available EIPs are displayed, click **View EIP** and create an EIP on the VPC console.

#. In the **EIP** column on the dds mongos tab, view the EIP that is successfully bound.

   To unbind an EIP from the DB instance, see :ref:`Unbinding an EIP <dds_02_0046__section186511510267>`.

.. _dds_02_0046__section186511510267:

Unbinding an EIP
----------------

#. On the **Instance Management** page, click the target cluster instance.

#. In the navigation pane on the left, choose **Connections**. In the **Basic Information** area, locate the target dds mongos node and click **Unbind EIP** in the **Operation** column.

   Or in the **Node Information** area on the **Basic Information** page, locate the target dds mongos node and choose **More** > **Unbind EIP** in the **Operation** column.

#. In the displayed dialog box, click **Yes**.

   To bind an EIP to the DB instance again, see :ref:`Binding an EIP <dds_02_0046__section3199593620428>`.
