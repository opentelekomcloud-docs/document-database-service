:original_name: dds_03_0060.html

.. _dds_03_0060:

Creating a User and Granting Permissions
========================================

This section describes how to use IAM to implement fine-grained permissions control for your DDS resources. With IAM, you can:

-  Create IAM users for employees based on the organizational structure of your enterprise. Each IAM user has their own security credentials, providing access to DDS resources.
-  Grant only the permissions required for users to perform a task.
-  Entrust an account or cloud service to perform professional and efficient O&M on your DDS resources.

If your account does not need individual IAM users, then you may skip over this topic.

This section describes the procedure for granting permissions (see :ref:`Figure 1 <dds_03_0060__fig15125554595>`).

**Prerequisites**
-----------------

Learn about the permissions (see :ref:`Permissions Management <dds_01_0019>`) supported by DDS and choose policies or roles according to your requirements. For the system policies of other services, see Permissions Policies.

Process Flow
------------

.. _dds_03_0060__fig15125554595:

.. figure:: /_static/images/en-us_image_0000001490031014.png
   :alt: **Figure 1** Process for granting DDS permissions

   **Figure 1** Process for granting DDS permissions

#. .. _dds_03_0060__li124716231010:

   `Create a user group and assign permissions <https://docs.otc.t-systems.com/usermanual/iam/iam_01_0030.html>`__ to it.

   Create a user group on the IAM console, and assign the **DDS FullAccess** policy to the group.

   .. note::

      To use some interconnected services, you also need to configure permissions of such services.

      For example, when using DAS to connect to a DB instance, you need to configure the DDS FullAccess and DAS FullAccess permissions.

#. `Create an IAM user <https://docs.otc.t-systems.com/usermanual/iam/iam_01_0031.html>`__ and add it to a user group.

   Create a user on the IAM console and add the user to the group created in :ref:`1 <dds_03_0060__li124716231010>`.

#. `Log in <https://docs.otc.t-systems.com/usermanual/iam/iam_01_0032.html>`__ and verify permissions.

   Log in to the DDS console by using the newly created user, and verify that the user only has read permissions for DDS.

   Choose **Service List** > **Document Database Service** and click **Buy DB Instance**. If you can buy a DDS DB instance, the required permission policies have taken effect.
