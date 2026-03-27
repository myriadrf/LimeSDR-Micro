JTAG
####

To debug Baseband processors design 10-pin 0.05" pitch JTAG connector is used (J1). 
It is located on the PCB top side (see :ref:`target-LimeSDR-Micro_M.2_2280_v1.0_components_top.png`) and is not populated by default. 
JTAG connector pins, schematic signal names and I/O standards are listed 
in Table 12. 

.. list-table:: Table 12. JTAG connector X9 pins
   :header-rows: 1
   :stub-columns: 1

   * - Connector pin
     - Schematic signal name
     - BB processor pin
     - I/O standard
     - Comment

   * - 1
     - VCC1P8
     - 
     - 1.8V
     - Power (1.8V)

   * - 2
     - TMS
     - M12
     - 1.8V
     - Test Mode Select

   * - 3
     - GND
     - 
     - 
     - Ground

   * - 4
     - TCK
     - N10
     - 1.8V
     - Test Clock

   * - 5
     - GND
     - 
     - 
     - Ground

   * - 6
     - TDO
     - N12
     - 1.8V
     - Test Data Output

   * - 7
     - NC
     - 
     - 
     - No Connection

   * - 8
     - TDI
     - M10
     - 1.8V
     - Test Data Input

   * - 9
     - GND
     - 
     - 
     - Ground

   * - 10
     - RST
     - N8
     - 1.8V
     - Reset