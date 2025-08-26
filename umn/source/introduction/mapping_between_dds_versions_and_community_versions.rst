:original_name: dds_01_0060.html

.. _dds_01_0060:

Mapping Between DDS Versions and Community Versions
===================================================

Document Database Service (DDS) is a cloud database service compatible with MongoDB. DDS major versions select community versions that have not reached EOL and have new major functions as candidate versions for compatibility. The DDS version does not correspond to the community version. To help you understand the mapping between DDS versions and community versions, DDS uses compatible community versions. For details, see :ref:`Figure 1 <dds_01_0060__fig12011574199>`.

.. _dds_01_0060__fig12011574199:

.. figure:: /_static/images/en-us_image_0000002378611730.png
   :alt: **Figure 1** Mapping between DDS versions and community versions

   **Figure 1** Mapping between DDS versions and community versions

-  DDS 4.0 are developed based on the corresponding community versions. The implementation of the same interface is consistent with that in the community. Compared with a community version, DDS has higher security and more O&M functions. DDS can better meet commercial application requirements.
-  After October 16, 2018, DDS 4.0 uses the community version 4.0.3 as the baseline version. New features are independently developed and evolved.
-  DDS 4.2 and later versions use the community version 4.0.3 as the baseline version. New features are independently developed and evolved. The storage engine is switched to RocksDB to provide better user experience.
-  DDS source code has been opened in the GitHub community. For details, see https://github.com/hwCloudDBSDDS/dds.
