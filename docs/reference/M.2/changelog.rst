Changelog
#########

The first production LimeSDR M.2 2280 was revision v1.0 and so this changelog starts with changes from that point.

v1.1
****
The major changes are:

* Changed GNSS power rail from VCC3P3_CLK to VCC3P3 to minimize GNSS module spurs in RF TX.
* Removed IC16 74LVC1G3157FZ4 analog mux for CLK_XO/XLK_IN clock mux.
* Replaced LMK00105 IC16 clock buffer with LMK00101. No external mux is required because LMK00101 has two inputs.
* Connected RF TX switch control directly to LA9310 BB chip (TRX0/GPIO_07) for better TX isolation in inactive time window
* LMS_TXEN connected to LA_CFG_TEST_PORT_DIS (LNA1_EN/GPIO_11) line via 1.8 -> 3.3V conversion
* Added secure key option (NF due to I2C address conflict with switching regulator)
* Added MHF4 connector for LA_PA_EN
* Connected MHF4 connector to EXT_PPS mux for EXT_PPS_IN/EXT_PPS_OUT selection.
* X3 (RX AUX) circuit removed
* Altium variant function enabled to more conveniently manage components assembly info, alternatives and to more easily generate manufacturing information such as BOM and PCB views.
* Added PROJECT_VERSION and SHEET_TOTAL parameters to project and schematic sheets

Board size and main components positions remained the same.

RF Control
==========

Connected RF TX switch control directly to LA9310 BB chip for better TX isolation in inactive time window.

Changed level converter LA_CFG_BOOT_SRC0 -> LA_TRX0 connections to LA_CFG_BOOT_SRC1 -> LA_TRX1 and connected LA_TRX1 TX switch control to instead TX_SW.

.. figure:: /images/LimeSDR-Micro_M.2_2280_v1.1_changes_txcontrol1.png
  :width: 300

.. figure:: /images/LimeSDR-Micro_M.2_2280_v1.1_changes_txcontrol2.png
  :width: 300

  Figure 1. TX control

Changed M.2 LA_CFG_BOOT_SRC0 net to LA_CFG_BOOT_SRC1 and M.2_TRX0 to M.2_TRX1

.. figure:: /images/LimeSDR-Micro_M.2_2280_v1.1_changes_trxcontrol1.png
  :width: 300

.. figure:: /images/LimeSDR-Micro_M.2_2280_v1.1_changes_trxcontrol2.png
  :width: 300

  Figure 2. M.2_TRX control

Added MHF4 connector for LA_PA_EN. Placed instead RX_AUX (X3) connector.

.. figure:: /images/LimeSDR-Micro_M.2_2280_v1.1_changes_paen.png
  :width: 300

  Figure 3. PA_EN connector

A_TRX1 and LA_PA_EN lines can operate from LA9310 timer independently. LA_TRX1 is dedicated for internal RF TX switch control and its polarity depends on selected active channel. LA_PA_EN is dedicated for external RFFE control and can always maintain same polarity.

LA_CFG_TEST_PORT_DIS line via 1.8 -> 3.3V conversion disconnected from LA_LNA1_EN and connected to LMS_TXEN.

.. figure:: /images/LimeSDR-Micro_M.2_2280_v1.1_changes_txencontrol1.png
  :width: 300

.. figure:: /images/LimeSDR-Micro_M.2_2280_v1.1_changes_txencontrol2.png
  :width: 300

  Figure 4. LMS_TXEN control


BB processor
============

Added testpoint for LA_CFG_BOOT_SRC0 to easier change boot mode to I2C EEPROM

Changed LA_CFG_PCIE_GEN configuration to 1: PCIe interface will allow negotiation to PCIe Gen3 (8 Gbit/s) frequencies

.. figure:: /images/LimeSDR-Micro_M.2_2280_v1.1_changes_LAconfig.png
  :width: 300

  Figure 5. BB processor configuration

Clock
=====

Removed IC16 74LVC1G3157FZ4 analog mux for CLK_XO/XLK_IN clock mux.

Replaced LMK00105 IC16 clock buffer with LMK00101. No external mux is required because LMK00101 has two inputs.

Renamed LMK_CLKOUT4 to LMK_CLKOUT7 respectively.

Connected MHF4 connector J3 directly to LMK_CLKOUT1.

Connected MHF4 connector J4 directly to LMK CLKin1.

Disabled M.2_CLK_IN clock in path by default (0R NF).

.. figure:: /images/LimeSDR-Micro_M.2_2280_v1.1_changes_lmk.png
  :width: 300

  Figure 6. LMK00101 clock buffer

Disconnected MHF4 connector J3 from EXT_PPS_IN.

Disconnected MHF4 connector J5 from EXT_PPS_OUT.

Connected MHF4 connector J5 to EXT_PPS mux for EXT_PPS_IN/EXT_PPS_OUT.

.. figure:: /images/LimeSDR-Micro_M.2_2280_v1.1_changes_pps.png
  :width: 300

  Figure 7. PPS circuit

Added ESD (NF) for ADF_REF_IN.

.. figure:: /images/LimeSDR-Micro_M.2_2280_v1.1_changes_adf.png
  :width: 300

  Figure 8. ADF_REG_IN ESD

Miscellaneous
=============

X3 (RX AUX) circuit removed.

.. figure:: /images/LimeSDR-Micro_M.2_2280_v1.1_changes_x3.png
  :width: 300

  Figure 9. RF connectors

Changed HW_VER from 0 to 1.

Renamed TX_SW to EXT_PPS_SEL and connected to EXT_PPS mux control.

Renamed A1 line to EXP_GPA1 and connected to FPC connector pin 6 instead LA_LNA1_EN.

.. figure:: /images/LimeSDR-Micro_M.2_2280_v1.1_changes_exp.png
  :width: 300

  Figure 10. I2C expander

Connected LA_I2C to FPC connector instead GND pins via 0R resistors.

Changed level converter LA_CFG_BOOT_SRC0 -> LA_TRX0 connections to LA_CFG_BOOT_SRC1 -> LA_TRX1 and connected LA_TRX1 TX switch control to instead TX_SW.

Renamed A1 line to EXP_GPA1 and connected to FPC connector pin 6 instead LA_LNA1_EN.

.. figure:: /images/LimeSDR-Micro_M.2_2280_v1.1_changes_rfctl.png
  :width: 300

  Figure 11. RFCTL GPIO connector

Changed GNSS power rail from VCC3P3_CLK to VCC3P3 to minimize GNSS module spurs in RF TX. ESD fitted.

.. figure:: /images/LimeSDR-Micro_M.2_2280_v1.1_changes_gnss.png
  :width: 300

  Figure 12. GNSS

Added secure key option (NF due to I2C address conflict with switching regulator).

.. figure:: /images/LimeSDR-Micro_M.2_2280_v1.1_changes_seckey.png
  :width: 300

  Figure 13. I2C secure key storage

Fitted ESDs (TXA, RXA, RXB, GNSS_ANT)

.. figure:: /images/LimeSDR-Micro_M.2_2280_v1.1_changes_esd1.png
  :width: 300

.. figure:: /images/LimeSDR-Micro_M.2_2280_v1.1_changes_esd2.png
  :width: 300

.. figure:: /images/LimeSDR-Micro_M.2_2280_v1.1_changes_esd3.png
  :width: 300

.. figure:: /images/LimeSDR-Micro_M.2_2280_v1.1_changes_esd4.png
  :width: 300

  Figure 14. I2C secure key storage


v1.0
****

Initial version.