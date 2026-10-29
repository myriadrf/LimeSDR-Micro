Clock Distribution
##################

The LimeSDR Micro mPCIe v1.2 board clock distribution block diagram is shown in Figure 7.

.. figure:: /images/LimeSDR-Micro_v1.2_diagrams_r0_clock.png
  :width: 600

  Figure 7. LimeSDR Micro mPCIe v1.2 board clock distribution block diagram

The LimeSDR Micro mPCIe v1.2 board features an on-board 30.72 MHz VCTCXO as the reference clock for 
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

Analogue switch IC17 selects the clock source for clock buffer IC16: the on-board VCTCXO XO1 (CLK_XO) or an external 
clock (CLK_IN). The source is selected by I/O expander output EXT_CLK_CTRL. By default, CLK_IN is connected to both 
U.FL connector J2 (through R155) and the mPCIe connector (X9, through R154), so only one external clock source should 
be connected at a time. The buffered clock signal LMK_CLKOUT4 can be fed to other boards through the mPCIe connector (X9), 
via analogue switch IC18 controlled by I/O expander output SMB_CLK_CTRL. J2 can be used as a clock output (LMK_CLKOUT3) 
by fitting R156 and removing R155.

The board clock lines and related signals are listed in Table 13.

.. table:: Table 13. Main clock lines

    +----------------------+---------------------------+------------------+-----------------------------------------------------+
    | **Source**           | **Schematic signal name** | **I/O standard** | **Description**                                     |
    +======================+===========================+==================+=====================================================+
    | External (J2)        | CLK_EXT                   | 3.3 V            | External reference clock input (U.FL)               |
    +----------------------+---------------------------+------------------+-----------------------------------------------------+
    | External (X9)        | PCIE_CLK_IN               | 3.3 V            | External reference clock input (mPCIe)              |
    +----------------------+---------------------------+------------------+-----------------------------------------------------+
    | External (J4)        | ADF_REF_IN                | 3.3 V            | External phase detector input (U.FL)                |
    +----------------------+---------------------------+------------------+-----------------------------------------------------+
    | Clock buffer (IC16)  | LMK_CLKOUT3               | 3.3 V            | Reference clock output (J2, R156 NF)                |
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
    | External (X9)        +---------------------------+ 1.8 V (diff)     | PCIe (mPCIe) reference clock                        |
    |                      | PCIE_REF_CLK_N            |                  |                                                     |
    +----------------------+---------------------------+------------------+-----------------------------------------------------+
    | RF transceiver (IC1) | LMS_MCLK1                 | 3.3 V            | Reference clock connected to BB processor           |
    +----------------------+---------------------------+------------------+-----------------------------------------------------+
    | GNSS Receiver (IC11) | GNSS_1PPS                 | 3.3 V            | PPS output from GNSS receiver for BB processor      |
    +----------------------+---------------------------+------------------+-----------------------------------------------------+
    | External (J3)        | EXT_PPS_IN                | 3.3 V            | External PPS input (U.FL, R173 NF)                  |
    +----------------------+---------------------------+------------------+-----------------------------------------------------+
    | External (X9)        | PCIE_PPS_IN               | 3.3 V            | External PPS input (mPCIe, R168 NF)                 |
    +----------------------+---------------------------+------------------+-----------------------------------------------------+
    | BB processor (IC6)   | PCIE_PPS_OUT              | 3.3 V            | PPS output (mPCIe, R180 NF)                         |
    |                      +---------------------------+------------------+-----------------------------------------------------+
    |                      | EXT_PPS_OUT               | 3.3 V            | External PPS output (J5)                            |
    +----------------------+---------------------------+------------------+-----------------------------------------------------+

.. note::
   By default, the BB processor PPS input (LA_PPS_IN) is driven by the GNSS receiver (GNSS_1PPS) through R170. 
   The external (J3) and mPCIe PPS inputs require fitting R173 or R168. The BB processor PPS output (LA_PPS_OUT) 
   is connected to J5 through R183; the mPCIe PPS output requires fitting R180.

