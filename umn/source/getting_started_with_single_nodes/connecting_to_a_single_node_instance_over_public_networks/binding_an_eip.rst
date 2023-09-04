:original_name: dds_02_0026.html

.. _dds_02_0026:

Binding an EIP
==============

Scenarios
---------

After you create a DB instance, you can bind it to an EIP to allow external access. If later you want to prohibit external access, you can also unbind the EIP from the DB instance.

Precautions
-----------

-  Before accessing a database, you need to apply for an EIP on the VPC console. Then, add an inbound rule to allow the IP addresses or IP address ranges of ECSs. For details, see section :ref:`Setting a Security Group <dds_02_0080>`.
-  To change the EIP that has been bound to a node, you need to unbind it from the node first.

.. _dds_02_0026__section3199593620428:


Binding an EIP
--------------

#. On the **Instance Management** page, click the target single node instance.

#. In the navigation pane on the left, choose **Connections**.

#. In the **Basic Information** area, locate the target node and click **Bind EIP** in the **Operation** column.

   Or in the **Node Information** area on the **Basic Information** page, locate the target node and choose **More** > **Bind EIP** in the **Operation** column.

#. In the displayed dialog box, all available unbound EIPs are listed. Select the required EIP and click **OK**. If no available EIPs are displayed, click **View EIP** and create an EIP on the VPC console.

#. Locate the target node, in the **EIP** column, view the EIP that is successfully bound.

   To unbind an EIP from the DB instance, see :ref:`Unbinding an EIP <dds_02_0026__section35191234134216>`.

.. _dds_02_0026__section35191234134216:

Unbinding an EIP
----------------

#. On the **Instance Management** page, click the target single node instance.

#. In the navigation pane on the left, choose **Connections**.

#. In the **Basic Information** area, locate the target node and click **Unbind EIP** in the **Operation** column.

   Or in the **Node Information** area on the **Basic Information** page, locate the target node and choose **More** > **Bind EIP** in the **Operation** column.

#. In the displayed dialog box, click **Yes**.

   To bind an EIP to the DB instance again, see :ref:`Binding an EIP <dds_02_0026__section3199593620428>`.
