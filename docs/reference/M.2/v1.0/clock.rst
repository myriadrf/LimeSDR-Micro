Clock Distribution
##################

LimeSDR Micro M.2 2280 v1.0 board clock distribution block diagram is as shown in Figure 7.

.. figure:: /images/LimeSDR-Micro_M.2_v1.0_diagrams_r1_clock.png
  :width: 600

  Figure 7. LimeSDR Micro M.2 2280 v1.0 board clock distribution block diagram

LimeSDR Micro M.2 2280 v1.0 board features an on board 30.72 MHz VCTCXO as the reference clock for 
LMS7002M RF transceiver.

Rakon E6245LF 30.72 MHz voltage controlled temperature compensated crystal oscillator (VCTCXO) 
is the clock source for the board. VCTCXO frequency may be tuned by using 16 bit DAC (IC18). 
Main VCTCXO parameters are listed in Table 7.

.. list-table:: Table 7. Rakon E7355LF VCTCXO main parameters
   :header-rows: 1

   * - Frequency parameter
     - Value
   * - Calibration (25°C ± 1°C)
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

Analogue switch (IC16) gives option to select clock source for clock buffered from 
onboard VCTCXO clock XO1 (CLK_XO) and external MHF4 (J2)/M.2 (X9) sources (CLK_IN). Buffered clock signal 
(LMK_CLKOUT1 and LMK_CLKOUT4) can also be fed to other board using MHF4 (XJ2)/M.2 (X9) connectors.

The board clock lines and other related signals/information are listed in Table 8.

.. table:: Table 8. LimeSDR Micro M.2 2280 main clock lines

    +----------------------+---------------------------+------------------+-----------------------------------------------------+
    | **Source**           | **Schematic signal name** | **I/O standard** | **Description**                                     |
    +======================+===========================+==================+=====================================================+
    | External (J2)        | CLK_IN                    | 3.3V             | External reference clock input (MHF4)               |
    +----------------------+---------------------------+------------------+-----------------------------------------------------+
    | Clock buffer (IC15)  | LMK_CLKOUT1               | 3.3V             | Reference clock output (MHF4)                       |
    |                      +---------------------------+------------------+-----------------------------------------------------+
    |                      | LMK_CLKOUT4               | 1.8V             | Reference clock output (M.2)                        |
    |                      +---------------------------+------------------+-----------------------------------------------------+
    |                      | LMS_TxPLL_CLK             | 1.8V             | Reference clock connected to LMS (TX)               |
    |                      +---------------------------+------------------+-----------------------------------------------------+
    |                      | LMS_RxPLL_CLK             | 1.8V             | Reference clock connected to LMS (RX)               |
    |                      +---------------------------+------------------+-----------------------------------------------------+
    |                      | ADF_RF_IN                 | 3.3V             | Reference clock connected to ADF (phase   detector) |
    +----------------------+---------------------------+------------------+-----------------------------------------------------+
    | VCTCXO (XO1)         | CLK_XO                    | 3.3V             | Onboard reference clock                             |
    +----------------------+---------------------------+------------------+-----------------------------------------------------+
    |                      | PCIE_REF_CLK_P            |                  |                                                     |
    | External (M.2)       +---------------------------+ 1.8V (diff)      | PCIe reference clock                                |
    |                      | PCIE_REF_CLK_N            |                  |                                                     |
    +----------------------+---------------------------+------------------+-----------------------------------------------------+
    | RF tranceiver (IC1)  | LMS_MCLK1                 | 3.3V             | Reference clock connected to BB processor           |
    +----------------------+---------------------------+------------------+-----------------------------------------------------+
    | GNSS Receiver (IC11) | GNSS_1PPS                 | 3.3V             | PPS output from GNSS receiver for BB   processor    |
    +----------------------+---------------------------+------------------+-----------------------------------------------------+
    | External  (J3)       | EXT_PPS_IN                | 3.3V             | External PPS input (MHF4)                           |
    +----------------------+---------------------------+------------------+-----------------------------------------------------+
    | External   (M.2)     | M.2_PPS_IN                | 3.3V             | External PPS input (M.2)                            |
    +----------------------+---------------------------+------------------+-----------------------------------------------------+
    | BB processor   (IC6) | M.2_PPS_OUT               | 3.3V             | M.2 PPS output                                      |
    |                      +---------------------------+------------------+-----------------------------------------------------+
    |                      | EXT_PPS_OUT               | 3.3V             | External PPS output (J5)                            |
    +----------------------+---------------------------+------------------+-----------------------------------------------------+
