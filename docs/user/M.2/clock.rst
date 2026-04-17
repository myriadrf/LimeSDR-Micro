Reference Clock
###############

The LimeSDR Micro M.2 clock system is based on a high stability 30.72 MHz VCTCXO (Voltage Controlled Temperature Compensated Crystal Oscillator) which can be tuned via an external 1PPS reference signal or GPSDO function.

The board provides reference clock and 1PPS input and output via M.2 connector, as well as dedicated MHF4 connectors for reference clock input (J4), output (J3) and 1PPS input/output (J5).

.. list-table:: Table 2. Clock Functions
   :header-rows: 1

   * - Function
     - Specification
     - Notes
   * - On-board Oscillator
     - 30.72 MHz VCTCXO
     - Rakon E6245LF, ±50 ppb stability
   * - External Clock Input
     - M.2 pin 28 and MHF4 (J4)
     - 10-52 MHz, 1.8V - 3.3V
   * - Clock Output
     - M.2 pin 24 and MHF4 (J3)
     - m.2 - 1.8V / MHF - 3.3V CMOS
   * - 1PPS input (not populated)
     - M.2 pin 46
     - 3.3V CMOS
   * - 1PPS output (not populated)
     - M.2 pin 48
     - 3.3V CMOS
   * - 1PPS input(not populated)/output
     - MHF4 (J5)
     - 3.3V CMOS

.. note::
   By default 1PPS input source is onboard GNSS receiver. To change 1PPS input source:

   For LimeSDR Micro M.2 v1.1 remove R176 and populate R173 (M.2) or R179 (MHF4 J5) with zero-ohm resistor.
   
   For LimeSDR Micro M.2 v1.0 remove R175 and populate R172 (M.2) or R178 (MHF4 J5) with zero-ohm resistor.

.. warning::
   When using external clock references, ensure signal levels and frequencies match specifications. 
   
   Improper clock signals may cause unstable operation and potential damage to the device.

