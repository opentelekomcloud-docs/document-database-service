:original_name: dds_03_0082.html

.. _dds_03_0082:

SQL Execution Control
=====================

Scenarios
---------

-  All requests whose execution duration exceeds *n* seconds need to be killed.
-  Requests from an IP address for a specific client need to be killed.
-  All requests for full table scan need to be killed.

Precautions
-----------

-  The instance node must have 4 or more vCPUs.
-  This function is available for replica set instances and cluster instances of version 3.4 or later.
-  A maximum of 10 rules can be created for a DB instance.
-  For an ultra-large cluster with more than 32 shards, creating and enabling rules whose **Node Type** is **shard** or **dds mongos_shard** will fail. You are advised to create rules whose **Node Type** is **dds mongos**.
-  For a cluster with more than 10 shards, you are advised to select one rule at a time when enabling or disabling rules.

Creating a Rule
---------------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select a region and a project.

#. Click **Service List**. Under **Database**, click **Document Database Service** to go to the DDS console.

#. On the **Instances** page, locate the target DB instance and click its name.

#. In the navigation tree on the left, click **SQL Execution Control**.

#. Click **Create Rule**.

#. On the **Create Rule** page, set parameters as required. For details, see :ref:`Table 1 <dds_03_0082__en-us_topic_0000001617195976_table1793543515589>`.


   .. figure:: /_static/images/en-us_image_0000002469992721.png
      :alt: **Figure 1** Parameters for creating a rule

      **Figure 1** Parameters for creating a rule

   .. _dds_03_0082__en-us_topic_0000001617195976_table1793543515589:

   .. table:: **Table 1** Parameter description

      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                 |
      +===================================+=============================================================================================================================================================================================+
      | SQL Type                          | You can specify one or more SQL statement types.                                                                                                                                            |
      |                                   |                                                                                                                                                                                             |
      |                                   | The value can be:                                                                                                                                                                           |
      |                                   |                                                                                                                                                                                             |
      |                                   | -  **query**: operation for querying data.                                                                                                                                                  |
      |                                   | -  **update**: operation for updating data.                                                                                                                                                 |
      |                                   | -  **insert**: operation for inserting data.                                                                                                                                                |
      |                                   | -  **remove**: operation for deleting data.                                                                                                                                                 |
      |                                   | -  **command**: command operation.                                                                                                                                                          |
      |                                   | -  **getmore**: operation for obtaining more data.                                                                                                                                          |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Table Namespace                   | -  If this parameter is left blank, this rule applies to operations on all databases and tables in the DB instance.                                                                         |
      |                                   | -  If this parameter is set to a database name, this rule applies to operations on all collections in the database. For example, the value can be **db1**.                                  |
      |                                   | -  If this parameter is set to a value in the format of database_name.collection_name, this rule only applies to operations on the collection. For example, the value can be **db1.coll1**. |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Client IP Address                 | If an ECS is used, the value is the private IP address of the ECS.                                                                                                                          |
      |                                   |                                                                                                                                                                                             |
      |                                   | .. note::                                                                                                                                                                                   |
      |                                   |                                                                                                                                                                                             |
      |                                   |    -  This parameter does not take effect for cluster DB instances of version 3.4.                                                                                                          |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Execution Plan                    | -  By default, this parameter is left blank, indicating that this rule applies to all execution plans.                                                                                      |
      |                                   | -  The value **COLLSCAN** indicates that the operation for full table scan will be killed.                                                                                                  |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Maximum Concurrency               | -  The value **0** indicates that this parameter does not take effect.                                                                                                                      |
      |                                   | -  For example, if this parameter is set to **100**, a maximum of 100 operations that meet the conditions can be performed.                                                                 |
      |                                   |                                                                                                                                                                                             |
      |                                   |    .. note::                                                                                                                                                                                |
      |                                   |                                                                                                                                                                                             |
      |                                   |       If there are 110 **currentOp** operations that meet the conditions, 10 operations will be randomly killed.                                                                            |
      |                                   |                                                                                                                                                                                             |
      |                                   | -  Either this parameter or **Maximum Execution Duration** must be greater than **0**.                                                                                                      |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Maximum Execution Duration        | -  The value **0** indicates that this parameter does not take effect.                                                                                                                      |
      |                                   | -  For example, if this parameter is set to **5**, **currentOp** operations executed for more than 5s will be killed. The value must be no less than **2**.                                 |
      |                                   | -  Either this parameter or **Maximum Concurrency** must be greater than **0**.                                                                                                             |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Node Type                         | -  **dds mongos** indicates that this rule only applies to mongos nodes in a DDS instance.                                                                                                  |
      |                                   | -  **shard** indicates that this rule only applies to shard nodes.                                                                                                                          |
      |                                   | -  **dds mongos_shard** indicates that this rule applies to both mongos and shard nodes in a DDS instance.                                                                                  |
      |                                   | -  **replica** indicates that this rule applies to replica sets.                                                                                                                            |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **OK**.

Enabling a Rule
---------------

#. Log in to the management console.
#. Click |image2| in the upper left corner and select a region and a project.
#. Click **Service List**. Under **Database**, click **Document Database Service** to go to the DDS console.
#. On the **Instances** page, locate the target DB instance and click its name.
#. In the navigation tree on the left, click **SQL Execution Control**.
#. Locate the target rule and click **Enable** in the **Operation** column.
#. Click **Yes**.
#. View the rule status on the **SQL Execution Control** page.

.. _dds_03_0082__section1422153763219:

Disabling a Rule
----------------

#. Log in to the management console.
#. Click |image3| in the upper left corner and select a region and a project.
#. Click **Service List**. Under **Database**, click **Document Database Service** to go to the DDS console.
#. On the **Instances** page, locate the target DB instance and click its name.
#. In the navigation tree on the left, click **SQL Execution Control**.
#. Locate the target rule and click **Disable** in the **Operation** column.
#. Click **Yes**.
#. View the rule status on the **SQL Execution Control** page.

Deleting a Rule
---------------

.. caution::

   An enabled rule cannot be deleted. To delete a rule, you must disable the rule by referring to :ref:`Disabling a Rule <dds_03_0082__section1422153763219>`.

#. Log in to the management console.
#. Click |image4| in the upper left corner and select a region and a project.
#. Click **Service List**. Under **Database**, click **Document Database Service** to go to the DDS console.
#. On the **Instances** page, locate the target DB instance and click its name.
#. In the navigation tree on the left, click **SQL Execution Control**.
#. Locate the target rule and click **Delete** in the **Operation** column.
#. Click **Yes**.

.. |image1| image:: /_static/images/en-us_image_0000002436514314.png
.. |image2| image:: /_static/images/en-us_image_0000002436514314.png
.. |image3| image:: /_static/images/en-us_image_0000002436514314.png
.. |image4| image:: /_static/images/en-us_image_0000002436514314.png
