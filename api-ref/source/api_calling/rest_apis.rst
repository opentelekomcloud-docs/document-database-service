:original_name: dds_api_0016.html

.. _dds_api_0016:

REST APIs
=========

API requests sent by third-party applications to public cloud services must be authenticated using signatures.

Public cloud APIs follow RESTful API design rules.

In REST, specific information or data on a network is represented by resources. REST allows users to access service resources by creating, querying, updating, and deleting resources.

A REST API request and response are divided into the following parts:

-  Request URI
-  Request header
-  Request body
-  Response header
-  Response body

Request URI
-----------

A request URI consists of the following:

**{URI-scheme}://{Endpoint}/{resource-path}?{query-string}**

Although a request URI is included in a request header, most programming languages or frameworks require the request URI to be separately transmitted, rather than being conveyed in a request message.

.. table:: **Table 1** URI parameter description

   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                         | Description                                                                                                                                     |
   +===================================+=================================================================================================================================================+
   | URI-scheme                        | Specifies the protocol used for transmitting requests.                                                                                          |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+
   | Endpoint                          | Specifies the domain name or IP address of the server bearing the REST service endpoint.                                                        |
   |                                   |                                                                                                                                                 |
   |                                   | To obtain the parameter value, see `Regions and Endpoints <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.                        |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+
   | resource-path                     | Specifies the API access path for performing a specified operation. Obtain this value from the URI of the API, for example, **v3/auth/tokens**. |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+
   | query-string                      | This parameter is optional. For example, you can set it to API version or resource selection criteria.                                          |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+

Request Methods
---------------

HTTP methods, which are also called operations or actions, specify the type of operations that you are requesting.

.. table:: **Table 2** HTTP methods

   +--------+--------------------------------------------------------------------------+
   | Method | Description                                                              |
   +========+==========================================================================+
   | GET    | Requests a server to return the specified resources.                     |
   +--------+--------------------------------------------------------------------------+
   | POST   | Requests a server to add resources or perform special operations.        |
   +--------+--------------------------------------------------------------------------+
   | DELETE | Requests a server to delete specified resources, for example, an object. |
   +--------+--------------------------------------------------------------------------+

Request Header
--------------

You can also add additional fields to the request header, for example, the fields required by a specified URI and an HTTP method. :ref:`Table 3 <dds_api_0016__table18389930>` lists common request header fields.

.. _dds_api_0016__table18389930:

.. table:: **Table 3** Common request headers

   +----------------+------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------+----------------------------------+
   | Name           | Description                                                                                                                  | Mandatory                                                                              | Example                          |
   +================+==============================================================================================================================+========================================================================================+==================================+
   | Content-Type   | Specifies the MIME type of the request body.                                                                                 | Yes                                                                                    | application/json                 |
   +----------------+------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------+----------------------------------+
   | Content-Length | Specifies the length of the request body. The unit is byte.                                                                  | This parameter is optional for POST requests, but must be left blank for GET requests. | 3495                             |
   +----------------+------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------+----------------------------------+
   | X-Project-Id   | Specifies the project ID. For details about how to obtain the project ID, see :ref:`Obtaining a Project ID <dds_projectid>`. | No                                                                                     | e9993fc787d94b6c886cbaa340f9c0f4 |
   +----------------+------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------+----------------------------------+
   | X-Auth-Token   | Specifies the user token.                                                                                                    | Yes                                                                                    | ``-``                            |
   +----------------+------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------+----------------------------------+

(Optional) Request Body
-----------------------

A request body is generally sent in a structured format (for example, JSON or XML), corresponding to **Content-Type** in the request header, and is used to transfer content other than the request header.

If the request body contains Chinese characters, convert the Chinese characters into the UTF-8 encoding format.

Response Headers
----------------

A response header consists of the following two parts:

-  An HTTP status code, which is a service-defined status code indicating a success or an error

-  Additional fields, for example **Content-Type**

   :ref:`Table 4 <dds_api_0016__en-us_topic_0113746487_en-us_topic_0020536997_table3877208613139>` lists common response header fields.

   .. _dds_api_0016__en-us_topic_0113746487_en-us_topic_0020536997_table3877208613139:

   .. table:: **Table 4** Common response headers

      +----------------+---------------------------------------------------------------------------------------------------------------------------------------+-------------------------------+
      | Name           | Description                                                                                                                           | Example                       |
      +================+=======================================================================================================================================+===============================+
      | Date           | Standard HTTP header field, which represents the date and time at which the message was originated. The format is defined by RFC 822. | Wed, 27 Dec 2018 06:49:46 GMT |
      +----------------+---------------------------------------------------------------------------------------------------------------------------------------+-------------------------------+
      | Content-Length | Standard HTTP header field, which specifies the size of the entity body, in decimal number of bytes, sent to the recipient.           | ``-``                         |
      +----------------+---------------------------------------------------------------------------------------------------------------------------------------+-------------------------------+
      | Content-Type   | Standard HTTP header field, which specifies the media type of the entity body sent to the recipient.                                  | application/json              |
      +----------------+---------------------------------------------------------------------------------------------------------------------------------------+-------------------------------+

(Optional) Response Body
------------------------

A response body is generally returned in a structured format (for example, JSON or XML), corresponding to **Content-Type** in the response header, and is used to transfer content other than the response header.
