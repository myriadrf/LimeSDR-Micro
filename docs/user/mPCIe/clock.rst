Reference Clock
###############

The LimeSDR Micro mPCIe clock system is based on a high stability 30.72 MHz VCTCXO (Voltage Controlled Temperature Compensated Crystal Oscillator) which can be tuned via an external 1PPS reference signal or GPSDO function.

The board provides reference clock and 1PPS input and output via mPCIe connector, as well as dedicated U.FL connectors for reference clock input (J4), output (J3) and 1PPS input/output (J5).

.. list-table:: Table 2. Clock Functions
   :header-rows: 1

   * - Function
     - Specification
     - Notes
   * - On-board Oscillator
     - 30.72 MHz VCTCXO
     - Rakon E6245LF, ±50 ppb stability
   * - External Clock Input
     - mPCIe pin 19 and U.FL (J4)
     - 10-52 MHz, 1.8V - 3.3V
   * - Clock Output
     - mPCIe pin 30 and U.FL (J3)
     - 3.3V CMOS
   * - 1PPS input (not populated)
     - mPCIe pin 3
     - 3.3V CMOS
   * - 1PPS output (not populated)
     - mPCIe pin 5
     - 3.3V CMOS
   * - 1PPS input(not populated)/output
     - U.FL (J5)
     - 3.3V CMOS

.. note::
   By default 1PPS input source is onboard GNSS receiver. To change 1PPS input source:
   
   For LimeSDR Micro mPCIe v1.3 remove R169 and populate R167 (mPCIe) or R172 (U.FL J5) with zero-ohm resistor.

   For LimeSDR Micro mPCIe v1.2 remove R170 and populate R168 (mPCIe) or R173 (U.FL J5) with zero-ohm resistor.

   For LimeSDR Micro mPCIe v1.1 remove R173 and populate R170 (mPCIe) or R177 (U.FL J5) with zero-ohm resistor.
    

.. warning::
   When using external clock references, ensure signal levels and frequencies match specifications. 
   
   Improper clock signals may cause unstable operation and potential damage to the device.

