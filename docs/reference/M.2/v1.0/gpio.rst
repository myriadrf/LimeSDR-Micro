GPIO Connector
##############

Three base band processors RF control/GPIOs and one I2C GPIO expander pin are connected 
to 8 pin FPC connector (X8). Additionaly one pin is dedicated for power (3.3V) and every other pin 
is ground as shown in table 13.  


.. list-table:: Table 13. RFCTL/ GPIOs connector (X8) pins
   :header-rows: 1
   :stub-columns: 1

   * - Connector pin
     - Schematic signal name
     - BB processor pin
     - I/O standard
     - Comment

   * - 1
     - VCC3P3
     - 
     - 3.3V
     - Power (3.3V)

   * - 2
     - LA_TRX0
     - M14
     - 3.3V
     - TXRX0/GPIO7

   * - 3
     - GND
     - 
     - 3.3V
     - Ground

   * - 4
     - LA_PA_EN
     - P14
     - 3.3V
     - PA_EN/GPIO12

   * - 5
     - GND
     - 
     - 3.3V
     - Ground

   * - 6
     - LA_LNA1_EN
     - M15
     - 3.3V
     - LNA1_EN/GPIO11

   * - 7
     - GND
     - 
     - 3.3V
     - Ground

   * - 8
     - EXP_GPA2
     - GPIO EXP (GPA2)
     - 3.3V
     - I2C GPIO expander