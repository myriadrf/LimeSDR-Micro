Changelog
#########

The first production LimeSDR mPCIe was revision v1.1 and so this changelog starts with changes from that point.

v1.3
****

LimeSDR-Micro mPCIe v1.3 board is designed using LimeSDR-Micro mPCIe v1.2 project as base with the schematic and PCB Layout changes described in this document.
The major changes are:

* Changed GNSS power rail from VCC3P3_CLK to VCC3P3 to minimize GNSS module spurs in RF TX.
* Removed 74LVC1G3157FZ4 analog mux for CLK_XO/XLK_IN clock mux.
* Replaced LMK00105 clock buffer with LMK00101. No external mux is required because LMK00101 has two inputs.
* Connected RF TX switch control directly to LA9310 BB chip (TRX0/GPIO_07) for better TX isolation in inactive time window.
* LMS_TXEN connected to LA_CFG_TEST_PORT_DIS (LNA1_EN/GPIO_11) line via 1.8 -> 3.3V conversion.
* Added secure key option (NF due to I2C address conflict with switching regulator).
* Added U.FL connector for LA_PA_EN
* Connected U.FL connector to EXT_PPS mux for EXT_PPS_IN/EXT_PPS_OUT selection.
* X3 (RX AUX) circuit removed.
* Altium variant function enabled to more conveniently manage components assembly info, alternatives and to more easily generate manufacturing information such as BOM and PCB views.
* Added PROJECT_VERSION and SHEET_TOTAL parameters to project and schematic sheets.
  
Board size and main components positions remained the same.

.. figure:: /images/LimeSDR-Micro_mPCIe_v1.3_diagrams_r0_BD.png
   :width: 600
  
   Figure 1: Block diagram

Minor Changes
=============

* Updated diagrams
* Cosmetic changes (notes etc.)
* Fitted ESDs (TXA, RXA, RXB, GNSS_ANT)
* Changed HW_VER from 0 to 1

Transmit Control
================

Connected RF TX switch control directly to LA9310 BB chip for better TX isolation in inactive time window.

LA_CFG_TEST_PORT_DIS line via 1.8 -> 3.3V conversion disconnected from LA_LNA1_EN and connected to LMS_TXEN.



.. figure:: /images/LimeSDR-Micro_mPCIe_v1.3_changes_TXCTL1.png
  :width: 600

.. figure:: /images/LimeSDR-Micro_mPCIe_v1.3_changes_TXCTL2.png
  :width: 600

  Figure 1: Transmit control

Changed mPCIe LA_CFG_BOOT_SRC0 net to LA_CFG_BOOT_SRC1 (TRX1/GPIO_08) (level converter TDD0_GPIO_LS->TDD0_GPIO).

.. figure:: /images/LimeSDR-Micro_mPCIe_v1.3_changes_TDD0.png
  :width: 600

  Figure 2: TDD0_GPIO

Added U.FL connector for TDD1_GPIO (LA_PA_EN). Placed instead RX_AUX (X3) connector.

.. figure:: /images/LimeSDR-Micro_mPCIe_v1.3_changes_PAEN.png
  :width: 600

  Figure 3: TDD1_GPIO (LA_PA_EN) connector

TDD0_GPIO (LA_TRX1) and TDD1_GPIO (LA_PA_EN) lines can operate from LA9310 timer independently. LA_TRX1 is dedicated for internal RF TX switch control and its polarity depends on selected active channel. LA_PA_EN is dedicated for external RFFE control and can always maintain same polarity.

LA_CFG_TEST_PORT_DIS line via 1.8 -> 3.3V conversion disconnected from LA_LNA1_EN and connected to LMS_TXEN.

.. figure:: /images/LimeSDR-Micro_mPCIe_v1.3_changes_TXEN1.png
  :width: 600

.. figure:: /images/LimeSDR-Micro_mPCIe_v1.3_changes_TXEN2.png
  :width: 600

  Figure 4: LMS_TXEN control

Baseband Processor
==================

Added testpoint for LA_CFG_BOOT_SRC0 to easier change boot mode to I2C EEPROM.

Changed LA_CFG_PCIE_GEN configuration to 1: PCIe interface will allow negotiation to PCIe Gen3 (8 Gbit/s) frequencies.

.. figure:: /images/LimeSDR-Micro_mPCIe_v1.3_changes_LA.png
  :width: 600

  Figure 5: LA configuration

Clock
=====

.. figure:: /images/LimeSDR-Micro_mPCIe_v1.3_diagrams_r1_clock.png
  :width: 600

  Figure 6: Clock diagram

Removed 74LVC1G3157FZ4 analog mux for CLK_XO/XLK_IN clock mux.

Replaced LMK00105 clock buffer with LMK00101. No external mux is required because LMK00101 has two inputs.

Connected U.FL connector J3 directly to LMK_CLKOUT1.

Connected U.FL connector J4 directly to LMK CLKin1.

Disabled PCIE_CLK_IN clock in path by default (0R NF).

.. figure:: /images/LimeSDR-Micro_mPCIe_v1.3_changes_LMK.png
  :width: 600

  Figure 7: LMK00101 clock buffer

Disconnected U.FL connector J3 from EXT_PPS_IN.

Disconnected U.FL connector J5 from EXT_PPS_OUT.

Connected U.FL connector J5 to EXT_PPS mux for EXT_PPS_IN/EXT_PPS_OUT.

.. figure:: /images/LimeSDR-Micro_mPCIe_v1.3_changes_PPS.png
  :width: 600

  Figure 8: PPS circuit

Added ESD (NF) for ADF_REF_IN.

.. figure:: /images/LimeSDR-Micro_mPCIe_v1.3_changes_ADF.png

  Figure 9: PPS circuit

Miscellaneous
=============

X3 (RX AUX) circuit removed.

.. figure:: /images/LimeSDR-Micro_mPCIe_v1.3_changes_AUX.png
  :width: 600

  Figure 10: RF connectors

Changed HW_VER from 0 to 1.

Renamed TX_SW to EXT_PPS_SEL and connected to EXT_PPS mux control.

.. figure:: /images/LimeSDR-Micro_mPCIe_v1.3_changes_IO.png
  :width: 600

  Figure 11: I2C expander

Connected LA_I2C to FPC connector instead GND pins via 0R resistors.

Changed LA_CFG_BOOT_SRC0 net to LA_CFG_BOOT_SRC1 (level converter TDD0_GPIO_LS->TDD0_GPIO).

LA_CFG_PCIE_GEN line connected via 0R (LNA2_EN_LS) and via 1.8 -> 3.3V conversion (LA_LNA2_EN) replaced LA_LNA1_EN line RFCTL FPC connector and mPCIe pin 45.

.. figure:: /images/LimeSDR-Micro_mPCIe_v1.3_changes_FPC1.png
  :width: 600

.. figure:: /images/LimeSDR-Micro_mPCIe_v1.3_changes_FPC2.png
  :width: 600

  Figure 12: FPC connector and mPCIe

Changed GNSS power rail from VCC3P3_CLK to VCC3P3 to minimize GNSS module spurs in RF TX. ESD fitted.

.. figure:: /images/LimeSDR-Micro_mPCIe_v1.3_changes_GNSS.png
  :width: 600

  Figure 13: GNSS receiver

Added secure key option (NF due to I2C address conflict with switching regulator).

.. figure:: /images/LimeSDR-Micro_mPCIe_v1.3_changes_SECKEY.png

  Figure 14: 2C secure key storage

Fitted ESDs (TXA, RXA, RXB, GNSS_ANT).

.. figure:: /images/LimeSDR-Micro_mPCIe_v1.3_changes_ESD1.png

.. figure:: /images/LimeSDR-Micro_mPCIe_v1.3_changes_ESD2.png

.. figure:: /images/LimeSDR-Micro_mPCIe_v1.3_changes_ESD3.png

.. figure:: /images/LimeSDR-Micro_mPCIe_v1.3_changes_ESD4.png

  Figure 15: FPC connector and mPCIe

PCB Changes
===========

LimeSDR-Micro v1.3 is based on LimeSDR-Micro v1.2 layout.

PCB updated with schematic changes.

.. figure:: /images/LimeSDR-Micro_mPCIe_v1.3_3D_top.png
  :width: 600

  Figure 16: LimeSDR-Micro mPCIe v1.3 3D view (top)

.. figure:: /images/LimeSDR-Micro_mPCIe_v1.3_3D_bot.png
  :width: 600

  Figure 17: LimeSDR-Micro mPCIe v1.3 3D view (bottom)

v1.2
****

LimeSDR Micro v1.2 board is designed using LimeSDR Micro v1.1 (mPCIe) project as base. 
The reference clock structure has been changed, replacing the separate general-purpose buffers with one dedicated clock buffer. 
This should improve clock parameters such as phase jitter. A JST connector for RFCTL signals has also been added. 
Added the ability to supply an external 3.3V voltage to the lines of that voltage, bypassing the switching regulators and thus avoiding the voltage drop.

Board size and main components positions remained the same.

RF Transceiver
==============

Replaced single LMS_CLK by two separate LMS_TxPLL_CLK and LMS_RxPLL_CLK clocks as shown in Figure 1. 

.. figure:: /images/LimeSDR-Micro_v1.2_changes_RF.png
  :width: 600
  
  Figure 18: LMS7002M clock changes

Baseband Processor
==================

Changed reset circuit as shown in Figure 2.

.. figure:: /images/LimeSDR-Micro_v1.2_changes_BB_reset.png
  :width: 600
  
  Figure 19: Baseband processor reset circuit changes

Disconnected LA_GPIO_05, LA_GPIO_06 and LA_CFG_BOOT_SRC1 from TDD control signals and connected to testpoints as shown in Figure 3.

.. figure:: /images/LimeSDR-Micro_v1.2_changes_BB_signal.png
  :width: 600
  
  Figure 20: Baseband processor signal changes

Clock
=====

Clock buffers were changed to single LMK00105 resulting in new clock diagram given in Figure 4.

.. figure:: /images/LimeSDR-Micro_v1.2_diagrams_r0_clock.png
  :width: 600
  
  Figure 21: LimeSDR Micro v1.2 board clock distribution block diagram

Added LMK buffer with 1.8V and 3.3V outputs as shown in Figure 4.

.. figure:: /images/LimeSDR-Micro_v1.2_changes_LMK.png
  :width: 600
  
  Figure 22: New clock buffer LMK00105

Changed XO DAC from AD5693RACPZ-1RL7 (A grade, INL +-8LSB, internal reference, VLOGIC) to AD5693BCPZ-RL7 (B grade, INL +-3LSB, no internal reference, LDAC).

Changed R162 to NF, R161 to fit to tie LDAC pin low and DAC updates when new data is written to the input register.

Connected XO DAC VREF directly to external 2.5V reference source (R164 changed to 0R, R166 to NF).

all XO DAC changes are shown in figure 5.

.. figure:: /images/LimeSDR-Micro_v1.2_changes_XODAC.png
  :width: 600
  
  Figure 23: XO DAC changes 

Power
=====

Renamed switching regulators outputs nets VCC3P3 and VCC_CLK to VCC3P3_SW and VCC_CLK_SW accordingly as shown in Figure 6.

.. figure:: /images/LimeSDR-Micro_v1.2_changes_SWREG.png
  :width: 600
  
  Figure 24: Switching regulator changes 

Removed VCC1P8_CLK and VCCIO_CLK power nets and LC filters.

Added power rails selection for VCC3P3 and VCC_CLK (directly connection option to VCC_EXT) as shown in Figure 7.

.. figure:: /images/LimeSDR-Micro_v1.2_changes_VSEL.png
  :width: 600
  
  Figure 25: voltage selection changes

Changed Voltage reference from LM4040C30FTADICT-ND (3.0V) to AS431ANTR-G1DICT-ND (2.5V). Also changed resistors accordingly as shown in Figure 8.

.. figure:: /images/LimeSDR-Micro_v1.2_changes_VREF.png
  :width: 600
  
  Figure 26: voltage reference changes

Miscellaneous
=============

Renamed I2C expanders (IC15) GPB7 pin PCIE_RESERVED to EXP_GPB7 as shown in Figure 9 and connected it to RFCLT/GPIO connector (X8) pin 8.

.. figure:: /images/LimeSDR-Micro_v1.2_changes_I2Cexp.png
  :width: 600
  
  Figure 27: I2C expander changes

Removed I2C connector (X6) and added RFCTL/GPIO 8-pin FPC connector (X8) in its place with signals listed below:

* TDD0_GPIO_LS connected to LA_CFG_BOOT_SRC0 (TXRX0).
* TDD1_GPIO_LS connected to LA_CFG_RST_HNDSHK (PA_EN).
* LNA1_EN_LS connected to LA_CFG_TEST_PORT_DIS (LNA1_EN).
* EXP_GPB7 connected to I2C expander.

New RFCTL/GPIO connector is shown in Figure 10.

.. figure:: /images/LimeSDR-Micro_v1.2_changes_RFCTL.png
  :width: 600
  
  Figure 28: New FRCTL/GPIO connector

Connected LNA1_EN_LS to level converter (1.8V to 3.3V) as shown in Figure 11.

.. figure:: /images/LimeSDR-Micro_v1.2_changes_LNA1_EN_LS.png
  :width: 600
  
  Figure 29: LNA1_EN_LS signal changes

Changed mPCIe pin 45 PCIE_RESERVED to LNA1_EN as shown in Figure 12.

.. figure:: /images/LimeSDR-Micro_v1.2_changes_mPCIe.png
  :width: 600
  
  Figure 30: mPCIe connector changes

PCB
===

LimeSDR-Micro v1.2 is based on LimeSDR-Micro v1.1 layout.

New resulting PCB top side is shown in Figure 14 and bottom side is shown in Figure 15.

.. figure:: /images/LimeSDR-Micro_v1.2_3D_top.png
      :width: 600

      Figure 31: LimeSDR Micro mPCIe v1.2 top

.. figure:: /images/LimeSDR-Micro_v1.2_3D_bot.png
      :width: 600

      Figure 32: LimeSDR Micro mPCIe v1.2 bottom

v1.1
****

Initial version.