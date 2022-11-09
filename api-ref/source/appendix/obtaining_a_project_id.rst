:original_name: dds_projectid.html

.. _dds_projectid:

Obtaining a Project ID
======================

Scenarios
---------

A project ID is required for some URLs when an API is called. Therefore, you need to obtain a project ID in advance. Two methods are available:

-  :ref:`Obtaining the Project ID by Calling an API <dds_projectid__section18520151052413>`
-  :ref:`Obtain a Project ID from the Console <dds_projectid__section127010198244>`

.. _dds_projectid__section18520151052413:

Obtaining the Project ID by Calling an API
------------------------------------------

The API used to obtain a project ID is **GET https://{Endpoint}/v3/projects**. **{Endpoint}** is the IAM endpoint and can be obtained from `Regions and Endpoints <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__ For details about API authentication, see :ref:`Token Authentication <dds_api_0010>`.

The following is an example response. The value of **id** is the project ID.

.. code-block::

   {
       "projects": [
           {
               "domain_id": "65382450e8f64ac0870cd180d14e684b",
               "is_domain": false,
               "parent_id": "65382450e8f64ac0870cd180d14e684b",
               "name": "project_name",
               "description": "",
               "links": {
                   "next": null,
                   "previous": null,
                   "self": "https://www.example.com/v3/projects/a4a5d4098fb4474fa22cd05f897d6b99"
               },
               "id": "a4a5d4098fb4474fa22cd05f897d6b99",
               "enabled": true
           }
       ],
       "links": {
           "next": null,
           "previous": null,
           "self": "https://www.example.com/v3/projects"
       }
   }

.. _dds_projectid__section127010198244:

Obtain a Project ID from the Console
------------------------------------

#. Register yourself on the management console and log in to it.

#. Move your pointer over the username and select **My Credential** in the displayed drop-down list.

   On the **My Credential** page, view the project ID in the project list.


   .. figure:: /_static/images/en-us_image_0208249570.jpg
      :alt: **Figure 1** Viewing project IDs

      **Figure 1** Viewing project IDs
