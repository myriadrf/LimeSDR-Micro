GPIO Connector
##############

Three base band processors RF control/GPIOs and one I2C GPIO expander pin are connected 
to 8 pin FPC connector (X8). Additionaly one pin is dedicated for power (3.3V) and every other pin 
is ground as shown in table 13.  


.. list-table:: Table 13. RFCTL/ GPIOs connector (X7) pins
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
     - TDD0_GPIO
     - M14
     - 3.3V
     - TXRX1/GPI_08
   * - 3
     - RF_I2C_SCL
     - P6
     - 3.3V
     - BB processor I2C clock
   * - 4
     - TDD1_GPIO
     - P14
     - 3.3V
     - PA_EN/GPIO12
   * - 5
     - RF_I2C_SDA
     - R6
     - 3.3V
     - BB processor I2C data
   * - 6
     - LNA2_EN
     - M15
     - 3.3V
     - LNA2_EN/GPIO_10
   * - 7
     - GND
     -
     - 3.3V
     - Ground
   * - 8
     - EXP_GPB7
     - GPIO EXP (GPB7)
     - 3.3V
     - I2C GPIO expander