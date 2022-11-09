:original_name: dds_api_0010.html

.. _dds_api_0010:

Token Authentication
====================

Application Scenarios
---------------------

If you use a token for authentication, you must obtain the user's token and add **X-Auth-Token** to the request message header of the service API when making an API call.

This section describes how to make an API call for token authentication.

Invoking an API
---------------

#. .. _dds_api_0010__en-us_topic_0110967262_li14280177102918:

   Obtain the following information:

   a. To obtain the IAM endpoint and region name in the message body, see `Regions and Endpoints <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.
   b. To obtain the project ID, see :ref:`Obtaining a Project ID <dds_projectid>`.

#. .. _dds_api_0010__en-us_topic_0110967262_li109381224173013:

   Send a POST https://*IAM\_Endpoint*/v3/auth/tokens request to obtain the user token.

   .. table:: **Table 1** Header description

      +--------------+----------------------------------------------+-----------+------------------+
      | Name         | Description                                  | Mandatory | Example          |
      +==============+==============================================+===========+==================+
      | Content-Type | Specifies the MIME type of the request body. | Yes       | application/json |
      +--------------+----------------------------------------------+-----------+------------------+

   An example request message is as follows:

   .. code-block:: text

      {
          "auth": {
              "identity": {
                  "methods": [
                      "password"
                  ],
                  "password": {
                      "user": {
                          "name": "username",
                          "password": "password",
                          "domain": {
                              "name": "domainname"
                          }
                      }
                  }
              },
              "scope": {
                  "project": {
                     "id": "project_id"
                   }
              }
          }
      }

   In the preceding command, replace parameter in italic with the actual values. For details, see the "Obtaining a User Token" section in the *Identity and Access Management API Reference*.

   a. **IAM\_Endpoint**: Replace it with the IAM endpoint obtained in :ref:`1 <dds_api_0010__en-us_topic_0110967262_li14280177102918>`.
   b. **username** and **password**: Replace them respectively with the username and password of the IAM server.
   c. **project_id**: Replace it with the project ID obtained in :ref:`1 <dds_api_0010__en-us_topic_0110967262_li14280177102918>`.

   After the request is processed, the value of **X-Subject-Token** in the header is the token value.

   .. code-block::

      X-Subject-Token:MIIDkgYJKoZIhvcNAQcCoIIDgzCCA38CAQExDTALBglghkgBZQMEAgEwgXXXXX...

#. Run the following command to set the token as an environment variable for subsequent operations:

   **export Token=\ {**\ *X-Subject-Token*\ **}**

   **X-Subject-Token**: Replace it with the token obtained in :ref:`2 <dds_api_0010__en-us_topic_0110967262_li109381224173013>`. An example command is as follows:

   **export Token=MIIDkgYJKoZIhvcNAQcCoIIDgzCCA38CAQExDTALBglghkgBZQMEAgEwgXXXXX...**
