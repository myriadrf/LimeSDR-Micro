Board Versions
##############

There are currently three versions of the LimeSDR Micro M.2 board: v1.0, v1.1 and v1.2.

v1.0, v1.1 and v1.2 boards are supported by the same software. The main features added in each new board version are listed in Table 1. For a full list of changes, see the :doc:`/reference/M.2/changelog`.

.. list-table:: Table 1. Features added in each board version
   :header-rows: 1
   :stub-columns: 1

   * - Version
     - New features
   * - v1.2
     - * Boots from I\ :sup:`2`\ C EEPROM by default
       * Boot source selection header (JP1, not populated)
       * SMBus interface on the M.2 connector (not connected by default)
   * - v1.1
     - * PCIe Gen 3 support
       * TDD control signal output on MHF4 connector (J2)
       * 1PPS input or output on MHF4 connector (J5)
       * ESD protection on RF and GNSS antenna connectors
   * - v1.0
     - Initial version

.. figure:: /images/LimeSDR-Micro_M.2_2280_v1.2_3D_top.png
  :width: 600

  Figure 1. LimeSDR Micro M.2 v1.2 board top view

.. figure:: /images/LimeSDR-Micro_M.2_2280_v1.1_3D_top.png
  :width: 600

  Figure 2. LimeSDR Micro M.2 v1.1 board top view

.. figure:: /images/LimeSDR-Micro_M.2_2280_v1.0_3D_top.png
  :width: 600

  Figure 3. LimeSDR Micro M.2 v1.0 board top view