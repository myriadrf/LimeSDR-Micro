Mini PCIe (mPCIe) edge connector
################################

Communication between the device and the host system is established through the mPCIe edge connector.

Connector pinout and signals according to the specification is given in Table 14.

.. list-table:: Table 14. Mini PCIe x1 edge connector pinout 
   :header-rows: 1
   :stub-columns: 1
   
   * - Pin
     - Mini PCIe x1 Specification
     - LimeSDR XTRX Schematic Signal Name
     - Description
   * - 1
     - Wake#
     - NC
     - Not connected
   * - 2
     - 3.3 Vaux
     - VCC3P3_MPCIE
     - Main power input 3.3V (VCC3P3_MPCIE)
   * - 3
     - COEX1
     - PCIE_PPS_IN
     - External 1PPS input
   * - 4
     - GND
     - GND
     - Ground
   * - 5
     - COEX2
     - PCIE_PPS_OUT
     - GPS 1PPS output
   * - 6
     - GND
     - NC
     - Not connected
   * - 7
     - CLKREQ#
     - CLK_REQUEST#
     - PCIe clock request tied to GND through resistor (330 Ohm)
   * - 8
     - UIM PWR
     - NC
     - Not connected
   * - 9
     - GND
     - GND
     - Ground
   * - 10
     - UIM_DATA
     - NC
     - Not connected
   * - 11
     - REFCLK-
     - PCIE_REF_CLK_N
     - PCI Express reference clock differential pair (negative)
   * - 12
     - UIM_CLK
     - NC
     - Not connected
   * - 13
     - REFCLK+
     - PCIE_REF_CLK_P
     - PCI Express reference clock differential pair (positive)
   * - 14
     - UIM_RESET
     - NC
     - Not connected
   * - 15
     - GND
     - GND
     - Ground
   * - 16
     - UIM_VPP
     - NC
     - Not connected
   * - 17
     - Reserved
     - TDD0_GPIO
     - TDD TX enable output or BB processor GPIO7
   * - 18
     - GND
     - GND
     - Ground
   * - 19
     - Reserved
     - PCIE_CLK_IN
     - External clock input (3.3 V)
   * - 20
     - W_DISABLE#
     - TDD1_GPIO
     - TDD TX enable output or BB processor GPIO12
   * - 21
     - GND
     - GND
     - Ground
   * - 22
     - PERST#
     - PCIE_PERST#
     - PCI Express interface reset
   * - 23
     - PERn0
     - PCIE_PER0_N
     - PCI Express output differential pair (negative)
   * - 24
     - 3.3Vaux
     - NC
     - Not connected
   * - 25
     - PERp0
     - PCIE_PER0_P
     - PCI Express output differential pair (positive)
   * - 26
     - GND
     - GND
     - Ground
   * - 27
     - GND
     - GND
     - Ground
   * - 28
     - 1.5Volt
     - NC
     - Not connected
   * - 29
     - GND
     - GND
     - Ground
   * - 30
     - SMB CLK
     - PCIE_CLK_OUT
     - Clock output (CLK_OUT)
   * - 31
     - PETn0
     - PCIE_PET0_N
     - PCI Express input differential pair (negative)
   * - 32
     - SMB Data
     - LA_I2C_SDA
     - No connection
   * - 33
     - PETp0
     - PCIE_PET0_P
     - PCI Express input differential pair (positive)
   * - 34
     - GND
     - GND
     - Ground
   * - 35
     - GND
     - GND
     - Ground
   * - 36
     - USB_D-
     - NC
     - Not connected
   * - 37
     - GND
     - GND
     - Jumper to GND (connected by default)
   * - 38
     - USB_D+
     - USB_D_P
     - USB 2.0 differential pair (positive)
   * - 39
     - 3.3Vaux
     - PCIE_TX1_N
     - Not connected
   * - 40
     - GND
     - GND
     - Ground
   * - 41
     - 3.3Vaux
     - PCIE_TX1_P
     - Not connected
   * - 42
     - LED_WWAN#
     - LED_WWAN#
     - WWAN LED output (active low)
   * - 43
     - GND
     - GND
     - Jumper to GND (connected by default)
   * - 44
     - LED_WLAN#
     - LED_WLAN#
     - WLAN LED output (active low)
   * - 45
     - Reserved
     - LNA1_EN
     - BB processor LNA1_EN / GPIO11 (output)
   * - 46
     - LED_WPAN#
     - LED_WPAN#
     - WPAN LED output (active low)
   * - 47
     - Reserved
     - PCIE_RX1_N
     - Not connected
   * - 48
     - 1.5Volt
     - NC
     - Not connected
   * - 49
     - Reserved
     - PCIE_RX1_P
     - Not connected
   * - 50
     - GND
     - GND
     - Ground
   * - 51
     - Reserved
     - PCIE_W_DISABLE2#
     - BB processor ASLEEP / GPIO19 (input)
   * - 52
     - 3.3Vaux
     - VCC3P3_MPCIE
     - Main power input 3.3V (VCC3P3_MPCIE)