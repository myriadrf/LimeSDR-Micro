Clock Distribution
##################

The LimeSDR Micro mPCIe v1.3 board clock distribution block diagram is shown in Figure 7.

.. figure:: /images/LimeSDR-Micro_mPCIe_v1.3_diagrams_r0_clock.png
  :width: 600

  Figure 7. LimeSDR Micro mPCIe v1.3 board clock distribution block diagram

The LimeSDR Micro mPCIe v1.3 board features an on-board 30.72 MHz VCTCXO as the reference clock for 
the LMS7002M RF transceiver.

Rakon E6245LF 30.72 MHz voltage controlled temperature compensated crystal oscillator (VCTCXO) 
is the clock source for the board. The VCTCXO frequency may be tuned using a 16-bit DAC (IC19). 
Main VCTCXO parameters are listed in Table 12.

.. list-table:: Table 12. Rakon E6245LF VCTCXO main parameters
   :header-rows: 1

   * - Frequency parameter
     - Value
   * - Calibration (25 °C ± 1 °C)
     - ± 1 ppm max
   * - Stability (-40 to 85 °C)
     - ± 50 ppb max
   * - Long term stability (first year)
     - ± 2 ppm max, ± 1.5 ppm max
   * - Control voltage range
     - 0.5 V .. 2.5 V
   * - Frequency tuning
     - ± 5 ppm 
   * - Slope
     - +7.5 ppm/V

Clock buffer IC17 selects the clock source: the on-board VCTCXO XO1 (CLK_XO) or an external clock (CLK_IN) 
from U.FL connector J4, or from the mPCIe connector (X8) when R151 is fitted. The source is selected by I/O expander 
output EXT_CLK_CTRL. The buffered clock signals (LMK_CLKOUT1 and LMK_CLKOUT4) can also be fed to other boards 
through U.FL connector J3 and the mPCIe connector (X8). LMK_CLKOUT4 reaches the mPCIe connector through analogue 
switch IC18, controlled by I/O expander output SMB_CLK_CTRL.

The board clock lines and related signals are listed in Table 13.

.. table:: Table 13. Main clock lines

    +----------------------+---------------------------+------------------+-----------------------------------------------------+
    | **Source**           | **Schematic signal name** | **I/O standard** | **Description**                                     |
    +======================+===========================+==================+=====================================================+
    | External (J4)        | CLK_IN_EXT                | 3.3 V            | External reference clock input (U.FL)               |
    +----------------------+---------------------------+------------------+-----------------------------------------------------+
    | External (X8)        | PCIE_CLK_IN               | 3.3 V            | External reference clock input (mPCIe, R151 NF)     |
    +----------------------+---------------------------+------------------+-----------------------------------------------------+
    | External (J6)        | ADF_REF_IN                | 3.3 V            | External phase detector input (U.FL)                |
    +----------------------+---------------------------+------------------+-----------------------------------------------------+
    | Clock buffer (IC17)  | LMK_CLKOUT1               | 3.3 V            | Reference clock output (J3) (U.FL)                  |
    |                      +---------------------------+------------------+-----------------------------------------------------+
    |                      | LMK_CLKOUT4               | 3.3 V            | Reference clock output (mPCIe) via IC18             |
    |                      +---------------------------+------------------+-----------------------------------------------------+
    |                      | LMS_TxPLL_CLK             | 1.8 V            | Reference clock connected to LMS (TX)               |
    |                      +---------------------------+------------------+-----------------------------------------------------+
    |                      | LMS_RxPLL_CLK             | 1.8 V            | Reference clock connected to LMS (RX)               |
    |                      +---------------------------+------------------+-----------------------------------------------------+
    |                      | ADF_RF_IN                 | 3.3 V            | Reference clock connected to ADF (phase detector)   |
    +----------------------+---------------------------+------------------+-----------------------------------------------------+
    | VCTCXO (XO1)         | CLK_XO                    | 3.3 V            | On-board reference clock                            |
    +----------------------+---------------------------+------------------+-----------------------------------------------------+
    |                      | PCIE_REF_CLK_P            |                  |                                                     |
    | External (X8)        +---------------------------+ 1.8 V (diff)     | PCIe (mPCIe) reference clock                        |
    |                      | PCIE_REF_CLK_N            |                  |                                                     |
    +----------------------+---------------------------+------------------+-----------------------------------------------------+
    | RF transceiver (IC1) | LMS_MCLK1                 | 3.3 V            | Reference clock connected to BB processor           |
    +----------------------+---------------------------+------------------+-----------------------------------------------------+
    | GNSS Receiver (IC11) | GNSS_1PPS                 | 3.3 V            | PPS output from GNSS receiver for BB processor      |
    +----------------------+---------------------------+------------------+-----------------------------------------------------+
    | External (J5)        | EXT_PPS_IN                | 3.3 V            | External PPS input (U.FL, R172 NF)                  |
    +----------------------+---------------------------+------------------+-----------------------------------------------------+
    | External (X8)        | PCIE_PPS_IN               | 3.3 V            | External PPS input (mPCIe, R167 NF)                 |
    +----------------------+---------------------------+------------------+-----------------------------------------------------+
    | BB processor (IC6)   | PCIE_PPS_OUT              | 3.3 V            | PPS output (mPCIe, R181 NF)                         |
    |                      +---------------------------+------------------+-----------------------------------------------------+
    |                      | EXT_PPS_OUT               | 3.3 V            | External PPS output (J5)                            |
    +----------------------+---------------------------+------------------+-----------------------------------------------------+

.. note::
   U.FL connector J5 is shared between PPS input and output. Analogue switch IC20, controlled by I/O expander output EXT_PPS_SEL, 
   connects J5 to EXT_PPS_OUT (low) or EXT_PPS_IN (high). By default, the BB processor PPS input (LA_PPS_IN) is driven 
   by the GNSS receiver (GNSS_1PPS) through R169; the external and mPCIe PPS inputs require fitting R172 or R167.

