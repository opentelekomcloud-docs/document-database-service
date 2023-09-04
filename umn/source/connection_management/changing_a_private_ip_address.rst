:original_name: dds_03_0070.html

.. _dds_03_0070:

Changing a Private IP Address
=============================

**Scenarios**
-------------

After a database is migrated from on-premises or other cloud platforms to DDS, the private IP address of the database may be changed. DDS allows you to change the private IP address, reducing migration costs.

Constraints
-----------

Changing the private IP address of a node will invalidate the previous private IP address. After the change, the new private IP address is bound to the EIP.

Procedure
---------

#. :ref:`Log in to the DDS console. <dds_02_0043>`

#. In the left navigation pane, choose **Instance Management**. In the DB instance list, click the target cluster instance to go to the **Basic Information** page.

   Alternatively, on the **Basic Information** page, in the navigation pane on the left, click **Connections**.

#. In the **Node Information** area, locate the target node and in the **Operation** column, click **Change Private IP Address**.

#. In the displayed dialog box, enter a private IP address that is not in use and click **OK**.

#. In the **Node Information** area, locate the target node and view the new private IP address.
