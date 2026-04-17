RF Network Control
##################

RF network contains matching networks, RF switches and MHF4 connectors 
(X1 - TX and X2, X4 - RX) as shown in Figure 6.

.. figure:: /images/LimeSDR-Micro_M.2_v1.1_diagrams_r0_RF.png
  :width: 600

  Figure 6. LimeSDR Micro M.2 2280 v1.1 RF diagram

LMS7002M RF transceiver TX and RX ports has dedicated matching network which determines the working frequency range. More detailed information on LMS7002M RF transceiver ports and matching network frequency ranges is listed in the Table 3.

.. list-table:: Table 3. LMS7002M RF transceiver ports and matching networks frequency ranges
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

Onboard RF network switches are controlled via 2.4V logic signals. 
This is achieved by resistor dividers connected between I2C GPIO expander (TX_SW, RX_SW2, RX_SW3) and switch 
control pin (TX_SW_DIV, RX_SW2_DIV, RX_S3_DIV).

Connectors X8 and J2 offers 3.3V logic control signals for external RF front end control.

RF network control signals are described in the Table 4.


.. table:: Table 4. RF network control signals
 
    +-----------------------------+-----------------------------+------------------+-----------------+--------------------------------------------------------+
    | **Component**               | **Schematic signal   name** | **I/O standard** | **Pin**         | **Description**                                        |
    +=============================+=============================+==================+=================+========================================================+
    | SKY13330-397LF(IC5)         | TX_SW/TX_SW_DIV             | 3.3V             | P15 (LA)        | 3.3V logic level   signal divided to 2.4V logic level. |
    +-----------------------------+-----------------------------+------------------+-----------------+--------------------------------------------------------+
    | SKY13414-485LF(IC3 and IC4) | RX_SW2/RX_SW2_DIV           | 3.3V             | GPB0 (expander) | 3.3V logic level   signal divided to 2.4V logic level. |
    |                             +-----------------------------+------------------+-----------------+--------------------------------------------------------+
    |                             | RX_SW3/RX_SW3_DIV           | 3.3V             | GPB2 (expander) | 3.3V logic level   signal divided to 2.4V logic level. |
    +-----------------------------+-----------------------------+------------------+-----------------+--------------------------------------------------------+
    | J2                          | LA_PA_EN                    | 3.3V             | P14 (LA)        | RF control signal output                               |
    +-----------------------------+-----------------------------+------------------+-----------------+--------------------------------------------------------+
    | X8                          | LA_TRX1                     | 3.3V             | P15 (LA)        | RF control signal output                               |
    |                             +-----------------------------+------------------+-----------------+                                                        |
    |                             | LA_PA_EN                    | 3.3V             | P14 (LA)        |                                                        |
    |                             +-----------------------------+------------------+-----------------+                                                        |
    |                             | EXP_GPA1                    | 3.3V             | GPA1 (expander) |                                                        |
    |                             +-----------------------------+------------------+-----------------+                                                        |
    |                             | EXP_GPA2                    | 3.3V             | GPA2 (expander) |                                                        |
    +-----------------------------+-----------------------------+------------------+-----------------+--------------------------------------------------------+
