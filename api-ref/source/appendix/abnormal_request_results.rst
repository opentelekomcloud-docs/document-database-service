:original_name: dds_api_0060.html

.. _dds_api_0060:

Abnormal Request Results
========================

-  Abnormal responses

   .. table:: **Table 1** Parameter description

      +------------+--------+------------------------------------------------------------------------------------------+
      | Name       | Type   | Description                                                                              |
      +============+========+==========================================================================================+
      | error_code | String | Specifies the error returned when a task submission exception occurs.                    |
      +------------+--------+------------------------------------------------------------------------------------------+
      | error_msg  | String | Specifies the description of the error returned when a task submission exception occurs. |
      +------------+--------+------------------------------------------------------------------------------------------+

-  Example abnormal response

   .. code-block:: text

      {
          "error_code": "DBS.200001",
          "error_msg": "Parameter error"
      }
