RF Network
##########

The RF network contains matching networks, RF switches and MHF4 connectors 
(X1 - TX and X2, X4 - RX), as shown in Figure 6.

.. figure:: /images/LimeSDR-Micro_M.2_v1.1_diagrams_r0_RF.png
  :width: 600

  Figure 6. LimeSDR Micro M.2 2280 v1.2 RF diagram

Frequency Range
===============

Each LMS7002M RF transceiver TX and RX port is connected to a dedicated RF path, and the appropriate path should be selected according to the operating frequency. On the receive side, the low-band path (RX_L) is recommended for frequencies below 1.5 GHz, the high-band path (RX_H) for frequencies of 2.2 GHz and above, and the wideband path (RX_W) for frequencies in between. On the transmit side, the TX1_2 path is recommended for frequencies below 2.6 GHz and the TX1_1 path for frequencies of 2.6 GHz and above. The recommended frequency ranges for all ports are summarised in Table 10.

.. note::
   The recommended frequency ranges are approximate values that cover most use cases, not hard limits of the RF paths. The optimum path may vary depending on other factors, such as the antenna and RF front-end parameters.

.. list-table:: Table 10. LMS7002M RF transceiver ports and recommended frequency ranges
   :header-rows: 1

   * - RF transceiver port
     - Recommended frequency range
   * - TX1_1
     - 2.6 GHz and above
   * - TX1_2
     - Below 2.6 GHz
   * - RX1_H, RX2_H
     - 2.2 GHz and above
   * - RX1_W, RX2_W
     - 1.5 GHz to 2.2 GHz
   * - RX1_L, RX2_L
     - Below 1.5 GHz

.. note::
   For applications requiring reception at frequencies of 30 MHz and below, the `LimeFEA HF Micro`_ companion board is recommended.

Control
=======

The on-board RF switches are controlled by 2.4 V logic signals, derived from 3.3 V control signals by resistor dividers. 
The TX switch control (TX_SW_DIV) is derived from LA_TRX1 (LA9310 pin P15), and the RX switch controls 
(RX_SW2_DIV, RX_SW3_DIV) are derived from I/O expander outputs RX_SW2 and RX_SW3.

Connectors X8 and J2 provide 3.3 V logic control signals for an external RF front end.

RF network control signals are described in Table 11.


.. table:: Table 11. RF network control signals
 
    +-----------------------------+-----------------------------+------------------+-----------------+--------------------------------------------------------+
    | **Component**               | **Schematic signal name**   | **I/O standard** | **Pin**         | **Description**                                        |
    +=============================+=============================+==================+=================+========================================================+
    | SKY13330-397LF (IC5)        | LA_TRX1/TX_SW_DIV           | 3.3 V            | P15 (LA)        | 3.3 V logic level signal divided to 2.4 V logic level. |
    +-----------------------------+-----------------------------+------------------+-----------------+--------------------------------------------------------+
    | SKY13414-485LF (IC3, IC4)   | RX_SW2/RX_SW2_DIV           | 3.3 V            | GPB0 (expander) | 3.3 V logic level signal divided to 2.4 V logic level. |
    |                             +-----------------------------+------------------+-----------------+--------------------------------------------------------+
    |                             | RX_SW3/RX_SW3_DIV           | 3.3 V            | GPB2 (expander) | 3.3 V logic level signal divided to 2.4 V logic level. |
    +-----------------------------+-----------------------------+------------------+-----------------+--------------------------------------------------------+
    | J2                          | LA_PA_EN                    | 3.3 V            | P14 (LA)        | RF control signal output                               |
    +-----------------------------+-----------------------------+------------------+-----------------+--------------------------------------------------------+
    | X8                          | LA_TRX1                     | 3.3 V            | P15 (LA)        | RF control signal output                               |
    |                             +-----------------------------+------------------+-----------------+                                                        |
    |                             | LA_PA_EN                    | 3.3 V            | P14 (LA)        |                                                        |
    |                             +-----------------------------+------------------+-----------------+                                                        |
    |                             | EXP_GPA1                    | 3.3 V            | GPA1 (expander) |                                                        |
    |                             +-----------------------------+------------------+-----------------+                                                        |
    |                             | EXP_GPA2                    | 3.3 V            | GPA2 (expander) |                                                        |
    +-----------------------------+-----------------------------+------------------+-----------------+--------------------------------------------------------+

.. _LimeFEA HF Micro: https://www.crowdsupply.com/lime-micro/limesdr-micro

