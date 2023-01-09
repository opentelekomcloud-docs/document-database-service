:original_name: dds_api_0010.html

.. _dds_api_0010:

Authentication
==============

DDS supports token authentication.

Token Authentication
--------------------

.. note::

   The validity period of a token is 24 hours. If a token needs to be used, the system caches the token to avoid frequent calling.

A token specifies temporary permissions in a computer system. During API authentication using a token, the token is added to requests to get permissions for calling the API.

If you use a token for authentication, you must obtain the user's token and add **X-Auth-Token** to the request message header of the service API when making an API call.

When `calling an API to obtain a user token <https://docs.otc.t-systems.com/en-us/api/iam/en-us_topic_0057845583.html>`__, you must set **auth.scope** in the request body to **project**.

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
                  "name": "xxxxxxxx"
                }
           }
       }
   }

After a token is obtained, add the **X-Auth-Token** header field must be added to requests to specify the token when calling other APIs. For example, if the token is **ABCDEFJ....**, add **X-Auth-Token: ABCDEFJ....** in a request as follows:

.. code-block:: text

   POST https://dds.eu-de.otc.t-systems.com/v3/auth/projects
   Content-Type: application/json
   X-Auth-Token: ABCDEFJ....
