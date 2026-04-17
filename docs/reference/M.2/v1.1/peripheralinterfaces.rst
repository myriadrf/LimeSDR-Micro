Peripheral Interfaces
#####################

Baseband processors SPI (LA_SPI) pins, schematic signal names and I/O standards/levels are shown in Table 10.

.. list-table:: Table 10. LA_SPI interface pins
   :header-rows: 1

   * - Schematic signal name
     - BB processor pin
     - I/O standard
     - Comment

   * - LA_SPI_SCLK
     - P8
     - 3.3V
     - Serial Clock (LA output)

   * - LA_SPI_MOSI
     - R9
     - 3.3V
     - Data (LA output)

   * - LA_SPI_MISO
     - R8
     - 3.3V
     - Data (LA input)

   * - LA_SPI_LMS_SS
     - P7
     - 3.3V
     - IC1 (LMS7002) SPI slave select (LA output)

   * - LA_SPI_ADF_SS_LS
     - P11
     - 3.3V
     - IC20 (ADF4002) SPI slave select (LA output)

Baseband processors I2C (LA_I2C)  
interface slave devices and related information are given in Table 11.

.. list-table:: Table 11. LA_I2C interfaces pins
   :header-rows: 1
  
   * - I2C slave device
     - Slave device
     - I2C address

   * - IC10
     - Temperature sensor
     - 1 0 0 1 0 1 1 RW

   * - IC13
     - EEPROM
     - 1 0 1 0 0 0 0 RW

   * - IC14
     - I/O expander
     - 0 1 0 0 0 0 0 RW

   * - IC18
     - XO DAC
     - 1 0 0 1 1 0 0 RW

   * - IC25
     - Switching regulator
     - 1 1 0 0 0 0 0 RW (I2C_SDA_SEL = 0)

   * - IC29
     - Switching regulator
     - 1 1 0 0 0 0 0 RW (I2C_SDA_SEL = 1)

   * - IC15 (not populated)
     - I2C secure key storage
     - 1 1 0 0 0 0 0 RW  

Switching regulators (IC25 and IC29) share identical I2C address, switching between them 
is done by I2C_SDA_SEL signal connected to I2C I/O expanders GPB3.

Before populating I2C secure key storage (IC15) make sure to avoid identical address conflicts with switching regulators. 