Boot Source
#############

.. warning::

   This topic involves hardware modifications and can harm the device if performed incorrectly. Proceed with caution.

This guide describes how to select the boot source for the onboard `NXP LA9310`_ baseband processor. The LA9310 supports two boot sources:

- ROM. Default option for classic LA9310 use cases.
- I\ :sup:`2`\ C EEPROM. This option is better suited for general purpose SDR that can be plugged into any system.

.. warning::
  LimeSDR Micro boards in boot from ROM configuration may not be detected or experience boot issues on some systems.

Boot Source Selection
=====================

Boot source selection is controlled by the ``CFG_BOOT_SRC[1:0]`` POR configuration pins, which are multiplexed with ``TXRX[1:0]``. Their values are sampled when ``PORESET_B`` is deasserted, and are captured in ``DCFG.PORSR1[15:14]``.

.. list-table:: Table 1. LA9310 Boot Source Selection
   :header-rows: 1

   * - CFG_BOOT_SRC[1:0]
     - Boot source
   * - 00
     - Reserved
   * - 01
     - Reserved
   * - 10
     - I\ :sup:`2`\ C EEPROM
   * - 11
     - ROM

I\ :sup:`2`\ C EEPROM Boot
--------------------------

On selecting this mode, the BootROM reads the boot header and image from an EEPROM at I\ :sup:`2`\ C address ``0x50``. This selection requires a pull-down on ``TXRX[0]``.

ROM Boot
--------

On selecting this mode, the LA9310 initializes its PCIe interface and waits for the host to enumerate and configure it. The host then supplies the boot header and boot-loader data via host memory.

Default Boot Source
===================

The default boot source depends on the board's form factor and version. Default boot sources are as follows:

.. list-table:: Table 2. Default boot source by board version
   :name: default-boot-source-by-version
   :header-rows: 1

   * - Board version
     - Default boot source
   * - M.2 v1.2
     - I\ :sup:`2`\ C EEPROM
   * - M.2 v1.1
     - ROM
   * - M.2 v1.0
     - ROM
   * - mPCIe v1.3
     - ROM
   * - mPCIe v1.2
     - ROM
   * - mPCIe v1.1
     - ROM

Changing the Boot Source
========================

Changing the LA9310's boot source requires a hardware modification to the LimeSDR Micro board. The exact modification depends on which form factor and board version you have.

Identify your board's form factor, then follow the corresponding guide:

- :doc:`M.2/index`
- :doc:`mPCIe/index`

.. toctree::
   :maxdepth: 1
   :hidden:

   M.2/index
   mPCIe/index

.. _NXP LA9310: https://www.nxp.com/docs/en/reference-manual/LA9310RM.pdf
