Reference Clock
###############

The LimeSDR Micro M.2 2280 clock system is based on a high stability 30.72 MHz VCTCXO (Voltage Controlled Temperature Compensated Crystal Oscillator) which can be tuned via an external 1PPS reference signal or GPSDO function.

The board provides reference clock and 1PPS inputs and outputs through the M.2 connector and dedicated MHF4 connectors. Select your board version below to see its clock and 1PPS connections.

.. tabs::

   .. tab:: v1.2

      .. list-table:: Table 3. LimeSDR Micro M.2 v1.2 clock and 1PPS connections
         :header-rows: 1

         * - Function
           - Connection
           - Notes
         * - On-board oscillator
           - XO1
           - 30.72 MHz VCTCXO, Rakon E6245LF, ±50 ppb stability
         * - Clock input
           - MHF4 (J4)
           - 10-52 MHz, 1.8V - 3.3V
         * - Clock input
           - M.2 pin 28
           - Not connected by default (fit R155)
         * - Clock output
           - MHF4 (J3)
           - 3.3V CMOS
         * - Clock output
           - M.2 pin 24
           - 1.8V CMOS
         * - 1PPS input
           - MHF4 (J5)
           - 3.3V CMOS, not connected by default (fit R179)
         * - 1PPS input
           - M.2 pin 46
           - Not connected by default (fit R173)
         * - 1PPS output
           - MHF4 (J5)
           - 3.3V CMOS
         * - 1PPS output
           - M.2 pin 48
           - Not connected by default (fit R189)

      .. note::
         MHF4 connector J5 is used for both 1PPS input and output. The direction is selected by an on-board analogue switch.

      .. note::
         By default 1PPS input source is onboard GNSS receiver. To change 1PPS input source, remove R176 and populate R173 (M.2) or R179 (MHF4 J5) with zero-ohm resistor.

      .. note::
         The 1PPS level converters are set to 3.3 V by default. To use the M.2 1PPS pins, set them to 1.8 V by removing R174 and R187 and populating R171 and R183 with zero-ohm resistors. This also sets MHF4 connector J5 to 1.8 V.

   .. tab:: v1.1

      .. list-table:: Table 3. LimeSDR Micro M.2 v1.1 clock and 1PPS connections
         :header-rows: 1

         * - Function
           - Connection
           - Notes
         * - On-board oscillator
           - XO1
           - 30.72 MHz VCTCXO, Rakon E6245LF, ±50 ppb stability
         * - Clock input
           - MHF4 (J4)
           - 10-52 MHz, 1.8V - 3.3V
         * - Clock input
           - M.2 pin 28
           - Not connected by default (fit R155)
         * - Clock output
           - MHF4 (J3)
           - 3.3V CMOS
         * - Clock output
           - M.2 pin 24
           - 1.8V CMOS
         * - 1PPS input
           - MHF4 (J5)
           - 3.3V CMOS, not connected by default (fit R179)
         * - 1PPS input
           - M.2 pin 46
           - Not connected by default (fit R173)
         * - 1PPS output
           - MHF4 (J5)
           - 3.3V CMOS
         * - 1PPS output
           - M.2 pin 48
           - Not connected by default (fit R189)

      .. note::
         MHF4 connector J5 is used for both 1PPS input and output. The direction is selected by an on-board analogue switch.

      .. note::
         By default 1PPS input source is onboard GNSS receiver. To change 1PPS input source, remove R176 and populate R173 (M.2) or R179 (MHF4 J5) with zero-ohm resistor.

      .. note::
         The 1PPS level converters are set to 3.3 V by default. To use the M.2 1PPS pins, set them to 1.8 V by removing R174 and R187 and populating R171 and R183 with zero-ohm resistors. This also sets MHF4 connector J5 to 1.8 V.

   .. tab:: v1.0

      .. list-table:: Table 3. LimeSDR Micro M.2 v1.0 clock and 1PPS connections
         :header-rows: 1

         * - Function
           - Connection
           - Notes
         * - On-board oscillator
           - XO1
           - 30.72 MHz VCTCXO, Rakon E6245LF, ±50 ppb stability
         * - Clock input
           - MHF4 (J2)
           - 10-52 MHz, 1.8V - 3.3V
         * - Clock input
           - M.2 pin 28
           - 10-52 MHz, 1.8V - 3.3V
         * - Clock output
           - MHF4 (J2)
           - 3.3V CMOS, optional (fit R158, remove R157)
         * - Clock output
           - M.2 pin 24
           - 1.8V CMOS
         * - 1PPS input
           - MHF4 (J3)
           - 3.3V CMOS, not connected by default (fit R178)
         * - 1PPS input
           - M.2 pin 46
           - Not connected by default (fit R172)
         * - 1PPS output
           - MHF4 (J5)
           - 3.3V CMOS
         * - 1PPS output
           - M.2 pin 48
           - Not connected by default (fit R188)

      .. note::
         MHF4 connector J2 and M.2 pin 28 are connected together. Connect only one external clock source at a time.

      .. note::
         By default 1PPS input source is onboard GNSS receiver. To change 1PPS input source, remove R175 and populate R172 (M.2) or R178 (MHF4 J3) with zero-ohm resistor.

      .. note::
         The 1PPS level converters are set to 3.3 V by default. To use the M.2 1PPS pins, set them to 1.8 V by removing R173 and R186 and populating R170 and R182 with zero-ohm resistors. This also sets MHF4 connectors J3 and J5 to 1.8 V.


.. warning::
   When using external clock references, ensure signal levels and frequencies match specifications. 
   
   Improper clock signals may cause unstable operation and potential damage to the device.
