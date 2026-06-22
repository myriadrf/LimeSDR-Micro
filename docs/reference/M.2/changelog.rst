Changelog
#########

The first production LimeSDR Micro M.2 2280 was revision v1.0 and so this changelog starts with changes from that point.

v1.2
****

LimeSDR-Micro M.2 2280 v1.2 board is designed using LimeSDR Micro M.2 2280 v1.1 project as base with the schematic and PCB Layout changes described in this document.

The major changes are:

* Added SMBUS interface for M.2 (disconnected by default).
* Moved M.2 pins that now are used for SMBUS to other M.2 pins.
* Added TH jumper (NF) for LA_CFG_BOOT_SRC0.
* Changed default BOOT_SRC to EEPROM.
* Connected LMS RBB to ADCIN (Ch 1, 2 I/Q).
* Connected LMS_TSTAO, LMS_TSTDO0, LMS_TSTDO1 via 0R NF to J2 (PA_EN) for test signals measurement as option.
* Changed LMS VDD_TBB (P4) power from VCC1P25_LMS to VCC1P4_LMS

M.2 Connector
=============

In earlier M.2 specification there was no SMBUS interface. In later SMBUS interface was added for Socket 3 PCIe (Key M) and Socket 2 (Key B-M):

* Pin 40 - GPIO_0 (I/O)/SMB_CLK (I/O) (0/1.8V*)
* Pin 42 - GPIO_1 (I/O)/SMB_DATA (I/O) (0/1.8V*)
* 44 GPIO_2 (I/O)/ALERT# (I) (0/1.8V*)

Following changes for M.2 pins were implemented. 

* Disconnected M.2_GPIO_1 from pin 42
* Connected M.2_GPIO_1 via 0R (as it was) to M.2 pin 58 (MFG_CLOCK).
* Renamed M.2_GPIO_1 to M.2_MFG.
* Disconnected M.2_TRX1 from pin 40
* Connected M.2_TRX1 via 0R (as it was) to M.2 pin 56 (MFG_DATA).
* Connected LA_I2C_SDA_LS via 0R NF to M.2 pin 42 (SMB_DATA).
* Connected LA_I2C_SCL_LS via 0R NF to M.2 pin 40 (SMB_CLK).
* M.2 pin 44 (SMBUS ALERT) that was connected to M.2_GPIO_2 net via 0R (R142) was changed to 0R NF.

.. figure:: /images/LimeSDR-Micro_M.2_2280_v1.2_changes_M.2.png

  Figure 1. M.2 Pins

.. figure:: /images/LimeSDR-Micro_M.2_2280_v1.2_changes_GPIOs.png

  Figure 2. GPIOs

BB processor boot configuration
===============================

After board firmware development and discussions decision was made that default boot mode must be EEPROM. In production for initial firmware programming and in case of firmware corruption simple method of changing boot to PCIe host memory was required. To temporarily change boot mode top PCIe 0.05” pitch header was added (not fitted).

Following changes for BB processor was implemented:

* Added TH jumper (NF) for LA_CFG_BOOT_SRC0, removed TP6.
* Changed default BOOT_SRC to EEPROM (R121 NF, R130 fit).
* TP6 (testpoint) for LA_CFG_BOOT_SRC0 line was removed.

.. figure:: /images/LimeSDR-Micro_M.2_2280_v1.2_changes_laconfig.png

  Figure 3. LA9310 configuration

RF transceiver (LMS) changes
============================

* Connected LA_PA_EN via 0R fit to J2 instead direct connection.
* Connected LMS_TSTAO, LMS_TSTDO0, LMS_TSTDO1 via 0R NF to J2 (PA_EN) for test signals measurement (PLL optimization etc.).

.. figure:: /images/LimeSDR-Micro_M.2_2280_v1.2_changes_J2.png

.. figure:: /images/LimeSDR-Micro_M.2_2280_v1.2_changes_LMS.png

  Figure 4. J2 connections

* Removed series 0R on RX BB path: C8, C12, C13, C17, C18, C22, C23, C27
* Removed series 0R on RX BB path: R28, R34, R37, R42, R44, R49, R51, R58

.. figure:: /images/LimeSDR-Micro_M.2_2280_v1.2_changes_RXBB.png

  Figure 5. LMS RX BB

Connected LMS RBB to ADCIN (Ch 1, 2 I/Q). This will help to utilize internal BB ADC for DC offset and RSSI calibration:

Y6 -> V4, AB2 -> U5, AB4 -> Y2, AA5 -> W3, AD2-> AA1, AC3 -> V6, AC5 -> AA3, AB6 ->Y4

.. figure:: /images/LimeSDR-Micro_M.2_2280_v1.2_changes_BBloopback.png

  Figure 6. LMS RX BB loopback

Miscellaneous
=============

Minor changes:

* Cosmetic changes (LA9310 boot notes etc.)
* Removed series 0R resistors on RX BB path.

Changed from HW_VER = 1 [0 1] to HW_VER = 2 [1 0]

.. figure:: /images/LimeSDR-Micro_M.2_2280_v1.2_changes_ioexp.png

.. figure:: /images/LimeSDR-Micro_M.2_2280_v1.2_changes_HW_VER.png

  Figure 7. HW_VER bits

PCB changes
===========

LimeSDR-Micro_M.2_2280 v1.2 is based on LimeSDR-Micro_M.2_2280 v1.1 layout. LimeSDR-Micro_M.2_2280 v1.2 complies with D3 height requirement (less or equal to 1.35 mm) from the bottom side. LimeSDR-Micro_M.2_2280 v1.2 doesn't comply with any allowed height requirement (1.5 mm maximum allowed) from the top side because of the height of VCTCXO, RF baluns and RF shield, which are up to 4.5mm.

.. figure:: /images/LimeSDR-Micro_M.2_2280_v1.2_3D_top.png

  Figure 8. LimeSDR-Micro M.2 2280 v1.2 3D view (top)

.. figure:: /images/LimeSDR-Micro_M.2_2280_v1.2_3D_bot.png

  Figure 9. LimeSDR-Micro M.2 2280 v1.2 3D view (bottom)

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