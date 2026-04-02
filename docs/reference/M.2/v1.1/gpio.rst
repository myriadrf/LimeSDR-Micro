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
     - LA_TRX1
     - M14
     - 3.3V
     - TXRX1/GPIO8

   * - 3
     - RF_I2C_SCL
     - P6
     - 3.3V
     - IIC1_SCL/GPIO_02

   * - 4
     - LA_PA_EN
     - P14
     - 3.3V
     - PA_EN/GPIO12

   * - 5
     - RF_I2C_SDA
     - R6
     - 3.3V
     - IIC1_SDA/GPIO_01

   * - 6
     - EXP_GPA1
     - GPIO EXP (GPA1)
     - 3.3V
     - I2C GPIO expander

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