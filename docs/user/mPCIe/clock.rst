Reference Clock
###############

The LimeSDR Micro mPCIe clock system is based on a high stability 30.72 MHz VCTCXO (Voltage Controlled Temperature Compensated Crystal Oscillator) which can be tuned via an external 1PPS reference signal or GPSDO function.

The board provides reference clock and 1PPS inputs and outputs through the mPCIe connector and dedicated U.FL connectors. Select your board version below to see its clock and 1PPS connections.

.. tabs::

   .. tab:: v1.3

      .. list-table:: Table 3. LimeSDR Micro mPCIe v1.3 clock and 1PPS connections
         :header-rows: 1

         * - Function
           - Connection
           - Notes
         * - On-board oscillator
           - XO1
           - 30.72 MHz VCTCXO, Rakon E6245LF, ±50 ppb stability
         * - Clock input
           - U.FL (J4)
           - 10-52 MHz, 1.8V - 3.3V
         * - Clock input
           - mPCIe pin 19
           - Not connected by default (fit R151)
         * - Clock output
           - U.FL (J3)
           - 3.3V CMOS
         * - Clock output
           - mPCIe pin 30
           - 3.3V CMOS
         * - 1PPS input
           - U.FL (J5)
           - 3.3V CMOS, not connected by default (fit R172)
         * - 1PPS input
           - mPCIe pin 3
           - Not connected by default (fit R167)
         * - 1PPS output
           - U.FL (J5)
           - 3.3V CMOS
         * - 1PPS output
           - mPCIe pin 5
           - Not connected by default (fit R181)

      .. note::
         U.FL connector J5 is used for both 1PPS input and output. The direction is selected by an on-board analogue switch.

      .. note::
         By default 1PPS input source is onboard GNSS receiver. To change 1PPS input source, remove R169 and populate R167 (mPCIe) or R172 (U.FL J5) with zero-ohm resistor.

   .. tab:: v1.2

      .. list-table:: Table 3. LimeSDR Micro mPCIe v1.2 clock and 1PPS connections
         :header-rows: 1

         * - Function
           - Connection
           - Notes
         * - On-board oscillator
           - XO1
           - 30.72 MHz VCTCXO, Rakon E6245LF, ±50 ppb stability
         * - Clock input
           - U.FL (J2)
           - 10-52 MHz, 1.8V - 3.3V
         * - Clock input
           - mPCIe pin 19
           - 10-52 MHz, 1.8V - 3.3V
         * - Clock output
           - U.FL (J2)
           - 3.3V CMOS, optional (fit R156, remove R155)
         * - Clock output
           - mPCIe pin 30
           - 3.3V CMOS
         * - 1PPS input
           - U.FL (J3)
           - 3.3V CMOS, not connected by default (fit R173)
         * - 1PPS input
           - mPCIe pin 3
           - Not connected by default (fit R168)
         * - 1PPS output
           - U.FL (J5)
           - 3.3V CMOS
         * - 1PPS output
           - mPCIe pin 5
           - Not connected by default (fit R180)

      .. note::
         U.FL connector J2 and mPCIe pin 19 are connected together. Connect only one external clock source at a time.

      .. note::
         By default 1PPS input source is onboard GNSS receiver. To change 1PPS input source, remove R170 and populate R168 (mPCIe) or R173 (U.FL J3) with zero-ohm resistor.

   .. tab:: v1.1

      .. list-table:: Table 3. LimeSDR Micro mPCIe v1.1 clock and 1PPS connections
         :header-rows: 1

         * - Function
           - Connection
           - Notes
         * - On-board oscillator
           - XO1
           - 30.72 MHz VCTCXO, Rakon E6245LF, ±50 ppb stability
         * - Clock input
           - U.FL (J1)
           - 10-52 MHz, 1.8V - 3.3V
         * - Clock input
           - mPCIe pin 19
           - 10-52 MHz, 1.8V - 3.3V
         * - Clock output
           - U.FL (J1)
           - 3.3V CMOS, optional (fit R166, remove R163)
         * - Clock output
           - mPCIe pin 30
           - 3.3V CMOS
         * - 1PPS input
           - U.FL (J2)
           - 3.3V CMOS, not connected by default (fit R177)
         * - 1PPS input
           - mPCIe pin 3
           - Not connected by default (fit R170)
         * - 1PPS output
           - U.FL (J4)
           - 3.3V CMOS
         * - 1PPS output
           - mPCIe pin 5
           - Not connected by default (fit R184)

      .. note::
         U.FL connector J1 and mPCIe pin 19 are connected together. Connect only one external clock source at a time.

      .. note::
         By default 1PPS input source is onboard GNSS receiver. To change 1PPS input source, remove R173 and populate R170 (mPCIe) or R177 (U.FL J2) with zero-ohm resistor.


.. warning::
   When using external clock references, ensure signal levels and frequencies match specifications. 
   
   Improper clock signals may cause unstable operation and potential damage to the device.
