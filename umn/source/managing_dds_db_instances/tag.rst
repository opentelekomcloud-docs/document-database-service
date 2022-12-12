:original_name: dds_03_0023.html

.. _dds_03_0023:

Tag
===

**Scenarios**
-------------

Tag Management Service (TMS) enables you to use tags on the management console to manage resources. TMS works with other cloud services to manage tags. TMS manages tags globally and other cloud services manage their own tags.

Adding tags to DDS DB instances helps you better identify and manage them. A DB instance can be tagged during or after it is created.

-  You are advised to set predefined tags on the TMS console.
-  A tag consists of a key and value. You can add only one value for each key. For details about the naming rules of tag keys and tag values, see :ref:`Table 1 <dds_03_0023__table197401426182516>`.
-  Each DB instance can have up to 20 tags.

.. _dds_03_0023__table197401426182516:

.. table:: **Table 1** Naming rules

   +-----------------------+--------------------------------------------------------------------------------------------------+-----------------------+
   | Parameter             | Requirement                                                                                      | Example               |
   +=======================+==================================================================================================+=======================+
   | Tag key               | -  Cannot be left blank.                                                                         | Organization          |
   |                       | -  For each DB instance, each tag key is unique.                                                 |                       |
   |                       | -  Consists of a maximum of 36 characters.                                                       |                       |
   |                       | -  The key can only consist of digits, letters, underscores (_), hyphens (-), and at sign (@).   |                       |
   +-----------------------+--------------------------------------------------------------------------------------------------+-----------------------+
   | Tag value             | -  Can be empty.                                                                                 | dds_01                |
   |                       | -  Consists of a maximum of 43 characters.                                                       |                       |
   |                       | -  The value can only consist of digits, letters, underscores (_), hyphens (-), and at sign (@). |                       |
   +-----------------------+--------------------------------------------------------------------------------------------------+-----------------------+

Adding a Tag
------------

#. :ref:`Log in to the DDS console. <dds_02_0043>`
#. On the **Instance Management** page, click the target DB instance.
#. In the navigation pane on the left, click **Tags**.
#. On the **Tags** page, click **Add Tag**. In the displayed dialog box, enter a tag key and value, and click **OK**.
#. View and manage tags on the **Tags** page.

Editing a Tag
-------------

#. :ref:`Log in to the DDS console. <dds_02_0043>`

#. On the **Instance Management** page, click the target DB instance.

#. In the navigation pane on the left, click **Tags**.

#. On the **Tags** page, locate the tag to be edited and click **Edit** in the **Operation** column. In the displayed dialog box, change the tag value and click **OK**.

   Only the tag value can be edited when editing a tag.

#. View and manage tags on the **Tags** page.

Deleting a Tag
--------------

#. :ref:`Log in to the DDS console. <dds_02_0043>`
#. On the **Instance Management** page, click the target DB instance.
#. In the navigation pane on the left, click **Tags**.
#. On the **Tags** page, locate the tag to be deleted and click **Delete** in the **Operation** column. In the displayed dialog box, click **Yes**.
#. After a tag has been deleted, it will not be displayed on the **Tags** page.
