JTAG
####

To debug Baseband processors design 6-pin 1.6 mm pitch compression connector (compatible with `Molex 78864100`_) is used (J1).
It is located on the PCB bottom side (see :ref:`target-LimeSDR-Micro_mPCIe_v1.3_components_bot.png`) and is not populated by default. 

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
     - LA_TDO
     - N12
     - 1.8V
     - Test Data Output
   * - 2
     - LA_TDI
     - M10
     - 1.8V
     - Test Data Input
   * - 3
     - LA_TMS
     - M12
     - 1.8V
     - Test Mode Select
   * - 4
     - VCC1P8
     -
     -
     - Power (1.8V)
   * - 5
     - LA_TCK
     - N10
     - 1.8V
     - Test Clock
   * - 6
     - JTAG_RST
     - N8
     - 1.8V
     - Reset

.. _Molex 78864100: https://www.molex.com/en-us/products/part-detail/788641001