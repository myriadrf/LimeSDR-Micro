Hardware Setup
##############

Host Interface
==============

LimeSDR Micro mPCIe should be plugged into a Mini PCIe slot on the host device. 

The host must provide a PCIe x1 interface (Gen 3 recommended) and supply power (3.3 V) via the Mini PCIe connector.

.. note::
   LimeSDR Micro mPCIe v1.2 and older boards are configured for PCIe Gen2 (5 GT/s) by default.

Cooling
=======

Depending on the application, host system and ambient temperature, additional cooling may be required to ensure reliable operation of the LimeSDR Micro board. This may be in the form of airflow through the host system, or a dedicated heatsink fitted to the board.

When designing a cooling solution for a LimeSDR Micro mPCIe–based system, power dissipation should be evaluated based on the specific user configuration and use case. In general, the LimeSDR Micro mPCIe cooling solution should be designed to dissipate at least 4 W of power, providing sufficient thermal margin to ensure safe and reliable operation during peak loads.

.. note::
   In the event of errors, instability or reduced performance, check the board temperature to ensure that it is within the specified operating range.

RF Connections
==============

.. figure:: /images/LimeSDR-Micro_mPCIe_v1.3_components_RFCON.png
  :width: 600
  
  Figure 4. LimeSDR Micro mPCIe v1.x board top with RF connector positions

Figure 4 shows the LimeSDR Micro mPCIe v1.3 board. On LimeSDR Micro mPCIe v1.1 and v1.2, the J2 position is occupied by connector X3 (RX AUX), which is not connected.

.. table:: Table 2. RF Connectors

  +--------------+----------------+---------+--------------------+-----------------------------------------+
  | Connector ID | Connector type | RF band | Recommended range  |                   Note                  |
  +==============+================+=========+====================+=========================================+
  | X1           | U.FL           | TX low  | Below 2.6 GHz      | Channel A transmit low frequency range  |
  |              |                +---------+--------------------+-----------------------------------------+
  |              |                | TX high | 2.6 GHz and above  | Channel A transmit high frequency range |
  +--------------+----------------+---------+--------------------+-----------------------------------------+
  | X2           | U.FL           | RX low  | Below 1.5 GHz      | Channel A receive low frequency range   |
  |              |                +---------+--------------------+-----------------------------------------+
  |              |                | RX wide | 1.5 GHz to 2.2 GHz | Channel A receive wide frequency range  |
  |              |                +---------+--------------------+-----------------------------------------+
  |              |                | RX high | 2.2 GHz and above  | Channel A receive high frequency range  |
  +--------------+----------------+---------+--------------------+-----------------------------------------+
  | X4           | U.FL           | RX low  | Below 1.5 GHz      | Channel B receive low frequency range   |
  |              |                +---------+--------------------+-----------------------------------------+
  |              |                | RX wide | 1.5 GHz to 2.2 GHz | Channel B receive wide frequency range  |
  |              |                +---------+--------------------+-----------------------------------------+
  |              |                | RX high | 2.2 GHz and above  | Channel B receive high frequency range  |
  +--------------+----------------+---------+--------------------+-----------------------------------------+

.. note::
  The recommended frequency ranges are approximate values that cover most use cases, not hard limits of the RF paths. The optimum path may vary depending on other factors, such as the antenna and RF front-end parameters.

.. note::
  TDD control signal (PA_EN) output (J2) is only available in LimeSDR Micro mPCIe v1.3.

.. warning::
   Care should be taken when connecting external RF signals to the RX inputs, to ensure that the maximum safe input power of +10 dBm is not exceeded, as this may cause permanent damage to the device.

