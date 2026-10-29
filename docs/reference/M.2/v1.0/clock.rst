Clock Distribution
##################

The LimeSDR Micro M.2 2280 v1.0 board clock distribution block diagram is shown in Figure 7.

.. figure:: /images/LimeSDR-Micro_M.2_v1.0_diagrams_r1_clock.png
  :width: 600

  Figure 7. LimeSDR Micro M.2 2280 v1.0 board clock distribution block diagram

The LimeSDR Micro M.2 2280 v1.0 board features an on-board 30.72 MHz VCTCXO as the reference clock for 
the LMS7002M RF transceiver.

Rakon E6245LF 30.72 MHz voltage controlled temperature compensated crystal oscillator (VCTCXO) 
is the clock source for the board. The VCTCXO frequency may be tuned using a 16-bit DAC (IC18). 
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

Analogue switch IC16 selects the clock source for clock buffer IC15: the on-board VCTCXO XO1 (CLK_XO) or an external clock (CLK_IN) 
from MHF4 connector J2 or the M.2 connector (X9). The buffered clock signal LMK_CLKOUT4 can be fed to other boards through 
the M.2 connector (X9), and LMK_CLKOUT1 through MHF4 connector J2 when R158 is fitted.

The board clock lines and related signals are listed in Table 13.

.. table:: Table 13. Main clock lines

    +----------------------+---------------------------+------------------+-----------------------------------------------------+
    | **Source**           | **Schematic signal name** | **I/O standard** | **Description**                                     |
    +======================+===========================+==================+=====================================================+
    | External (J2)        | CLK_IN                    | 3.3 V            | External reference clock input (MHF4)               |
    +----------------------+---------------------------+------------------+-----------------------------------------------------+
    | External (J4)        | ADF_REF_IN                | 3.3 V            | External phase detector input (MHF4)                |
    +----------------------+---------------------------+------------------+-----------------------------------------------------+
    | Clock buffer (IC15)  | LMK_CLKOUT1               | 3.3 V            | Reference clock output (J2, R158 not fitted)        |
    |                      +---------------------------+------------------+-----------------------------------------------------+
    |                      | LMK_CLKOUT4               | 1.8 V            | Reference clock output (M.2)                        |
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
    | External (X9)        +---------------------------+ 1.8 V (diff)     | PCIe (M.2) reference clock                          |
    |                      | PCIE_REF_CLK_N            |                  |                                                     |
    +----------------------+---------------------------+------------------+-----------------------------------------------------+
    | RF transceiver (IC1) | LMS_MCLK1                 | 3.3 V            | Reference clock connected to BB processor           |
    +----------------------+---------------------------+------------------+-----------------------------------------------------+
    | GNSS Receiver (IC11) | GNSS_1PPS                 | 3.3 V            | PPS output from GNSS receiver for BB processor      |
    +----------------------+---------------------------+------------------+-----------------------------------------------------+
    | External (J3)        | EXT_PPS_IN                | 3.3 V            | External PPS input (MHF4)                           |
    +----------------------+---------------------------+------------------+-----------------------------------------------------+
    | External (X9)        | M.2_PPS_IN                | 3.3 V            | External PPS input (M.2)                            |
    +----------------------+---------------------------+------------------+-----------------------------------------------------+
    | BB processor (IC6)   | M.2_PPS_OUT               | 3.3 V            | M.2 PPS output                                      |
    |                      +---------------------------+------------------+-----------------------------------------------------+
    |                      | EXT_PPS_OUT               | 3.3 V            | External PPS output (J5)                            |
    +----------------------+---------------------------+------------------+-----------------------------------------------------+

