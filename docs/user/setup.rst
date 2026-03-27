Hardware Setup
##############

Host Interface
**************

LimeSDR Micro should be plugged into a M.2 slot with B, M or B+M key on the host device. 

The host must provide a PCIe Gen3 x1 interface, and supply power via the M.2 connector.

Cooling
*******

Depending on the application, host system and ambient temperature, additional cooling may be required to ensure reliable operation of the LimeSDR Micro board. This may be in the form of airflow through the host system, or a dedicated heatsink fitted to the board.



When designing a cooling solution for a LimeSDR Mico–based system, power dissipation should be evaluated based on the specific user configuration and use case. In general, the LimeSDR XTRX cooling solution should be designed to dissipate at least 8 W of power, providing sufficient thermal margin to ensure safe and reliable operation during peak loads.

.. note::
   In the event of errors, instability or reduced performance, check the board temperature to ensure that it is within the specified operating range.

RF Connections
**************

.. figure:: /images/LimeSDR-Micro_M.2_2280_v1.1_components_RFCON.png
  :width: 600
  
  Figure 8: LimeSDR Mini v2.x board top with RF connector positions

.. table:: Table 1. RF Connectors

  +--------------+----------------+---------+--------------------+-----------------------------------------+
  | Connector ID | Connector type | RF band |   Frequency range  |                   Note                  |
  +==============+================+=========+====================+=========================================+
  | X1           | MHF4           | TX low  | 0.03 GHz - 1.9 GHz | Channel A transmit low frequency range  |
  |              |                +---------+--------------------+-----------------------------------------+
  |              |                | TX high | 3.3 GHz - 3.8 GHz  | Channel A transmit high frequency range |
  +--------------+----------------+---------+--------------------+-----------------------------------------+
  | X2           | MHF4           | RX low  | 0.3 GHz - 2.2 GHz  | Channel A receive low frequency range   |
  |              |                +---------+--------------------+-----------------------------------------+
  |              |                | RX wide | 0.7 GHz - 2.6 GHz  | Channel A receive wide frequency range  |
  |              |                +---------+--------------------+-----------------------------------------+
  |              |                | RX high | 3.3 GHz - 3.8 GHz  | Channel A receive high frequency range  |
  +--------------+----------------+---------+--------------------+-----------------------------------------+
  | X3           | MHF4           | RX low  | 0.3 GHz - 2.2 GHz  | Channel B receive low frequency range   |
  |              |                +---------+--------------------+-----------------------------------------+
  |              |                | RX wide | 0.7 GHz - 2.6 GHz  | Channel B receive wide frequency range  |
  |              |                +---------+--------------------+-----------------------------------------+
  |              |                | RX high | 3.3 GHz - 3.8 GHz  | Channel B receive high frequency range  |
  +--------------+----------------+---------+--------------------+-----------------------------------------+

.. warning::
   Care should be taken when connecting external RF signals to the RX inputs, to ensure that the maximum safe input power of +10 dBm is not exceeded, as this may cause permanent damage to the device.

