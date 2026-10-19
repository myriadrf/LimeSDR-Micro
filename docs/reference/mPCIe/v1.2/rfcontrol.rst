RF Network Control
##################

The RF network contains matching networks, RF switches and U.FL connectors 
(X1 - TX and X2, X4 - RX), as shown in Figure 6. U.FL connector X3 (RX_AUX) is a placeholder for future use and is not connected.

.. figure:: /images/LimeSDR-Micro_v1.2_diagrams_r0_RFFE.png
  :width: 600

  Figure 6. LimeSDR Micro mPCIe v1.2 RF diagram

Each LMS7002M RF transceiver TX and RX port has a dedicated matching network that determines its operating frequency range. The LMS7002M RF transceiver ports and matching network frequency ranges are listed in Table 10.

.. list-table:: Table 10. LMS7002M RF transceiver ports and matching networks frequency ranges
   :header-rows: 1

   * - RF transceiver port
     - Frequency range
   * - TX1_1
     - 3.3 GHz - 3.8 GHz
   * - TX1_2
     - 0.03 GHz - 1.9 GHz
   * - RX1_H, RX2_H
     - 3.3 GHz - 3.8 GHz 
   * - RX1_W, RX2_W
     - 0.7 GHz - 2.6 GHz
   * - RX1_L, RX2_L
     - 0.3 GHz - 2.2 GHz

The on-board RF switches are controlled by 2.4 V logic signals, derived from 3.3 V I/O expander outputs 
(TX_SW, RX_SW2, RX_SW3) by resistor dividers (TX_SW_DIV, RX_SW2_DIV, RX_SW3_DIV).

Connector X8 provides 3.3 V logic control signals for an external RF front end.

RF network control signals are described in Table 11.


.. table:: Table 11. RF network control signals
 
    +-----------------------------+-----------------------------+------------------+-----------------+--------------------------------------------------------+
    | **Component**               | **Schematic signal name**   | **I/O standard** | **Pin**         | **Description**                                        |
    +=============================+=============================+==================+=================+========================================================+
    | SKY13330-397LF (IC5)        | TX_SW/TX_SW_DIV             | 3.3 V            | GPB1 (expander) | 3.3 V logic level signal divided to 2.4 V logic level. |
    +-----------------------------+-----------------------------+------------------+-----------------+--------------------------------------------------------+
    | SKY13414-485LF (IC3, IC4)   | RX_SW2/RX_SW2_DIV           | 3.3 V            | GPB0 (expander) | 3.3 V logic level signal divided to 2.4 V logic level. |
    |                             +-----------------------------+------------------+-----------------+--------------------------------------------------------+
    |                             | RX_SW3/RX_SW3_DIV           | 3.3 V            | GPB2 (expander) | 3.3 V logic level signal divided to 2.4 V logic level. |
    +-----------------------------+-----------------------------+------------------+-----------------+--------------------------------------------------------+
    | X8                          | TDD0_GPIO                   | 3.3 V            | M14 (LA)        | RF control signal output                               |
    |                             +-----------------------------+------------------+-----------------+                                                        |
    |                             | TDD1_GPIO                   | 3.3 V            | P14 (LA)        |                                                        |
    |                             +-----------------------------+------------------+-----------------+                                                        |
    |                             | LNA1_EN                     | 3.3 V            | M15 (LA)        |                                                        |
    |                             +-----------------------------+------------------+-----------------+                                                        |
    |                             | EXP_GPB7                    | 3.3 V            | GPB7 (expander) |                                                        |
    +-----------------------------+-----------------------------+------------------+-----------------+--------------------------------------------------------+

.. note::
   TDD0_GPIO, TDD1_GPIO and LNA1_EN are also available on the mPCIe edge connector (pins 17, 20 and 45, respectively). See :doc:`mpcie`.

