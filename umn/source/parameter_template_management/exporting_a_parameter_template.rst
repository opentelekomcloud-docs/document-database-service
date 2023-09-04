:original_name: dds_03_0111.html

.. _dds_03_0111:

Exporting a Parameter Template
==============================

-  You can export a parameter template of a DB instance for future use. You can also apply the exported parameter template to other instances by referring to :ref:`Applying a Parameter Template <dds_03_0014>`.
-  You can export parameter template details (parameter names, values, and descriptions) of an instance to a CSV file for review and analysis.

Procedure
---------

#. Log in to the management console.
#. Click |image1| in the upper left corner and select a region and a project.
#. Click **Service List**. Under **Database**, click **Document Database Service** to go to the DDS console.
#. In the navigation pane on the left, choose **Instance Management**. On the displayed page, click the target instance. The **Basic Information** page is displayed.
#. In the navigation pane on the left, choose **Parameters**. On the **Parameters** tab, above the parameter list, click **Export**.

   -  Exporting to a custom template Export the parameter list of the instance to a parameter template for future use.

      In the displayed dialog box, configure required details and click **OK**.

      .. note::

         -  **New Parameter Template**: The template name can be 4 to 64 characters long and starts with a letter. It can contain only letters, digits, hyphens (-), underscores (_), and periods (.).
         -  **Description**: The template description consists of a maximum of 256 characters and cannot include line breaks or the following special characters: >!<"&'=

      After the parameter template is exported, a new template is generated in the list on the **Parameter Template Management** page.

   -  Exporting to a file: You can export the parameter template details (parameter names, values, and descriptions) of a DB instance to a CSV file for review and analysis.

      In the displayed dialog box, enter the file name and click **OK**.

      .. note::

         The file name must start with a letter and consist of 4 to 81 characters. It can contain only letters, digits, hyphens (-), and underscores (_).

.. |image1| image:: /_static/images/en-us_image_0000001268771757.png
