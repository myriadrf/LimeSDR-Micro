Mini PCIe (mPCIe) edge connector
################################

Communication between the device and the host system is established through the mPCIe edge connector.

The connector pinout and signals, compared with the Mini PCIe specification, are given in Table 15.

.. list-table:: Table 15. Mini PCIe x1 edge connector (X10) pinout
   :header-rows: 1
   :stub-columns: 1
   
   * - Pin
     - Specification
     - Schematic signal name
     - Description
   * - 1
     - Wake#
     - NC
     - Not connected
   * - 2
     - 3.3Vaux
     - VCC3P3_MPCIE
     - Main power input 3.3 V
   * - 3
     - COEX1
     - PCIE_PPS_IN
     - External 1PPS input (R170 NF)
   * - 4
     - GND
     - GND
     - Ground
   * - 5
     - COEX2
     - PCIE_PPS_OUT
     - 1PPS output (R184 NF)
   * - 6
     - 1.5Volt
     - NC
     - Not connected
   * - 7
     - CLKREQ#
     - CLK_REQUEST#
     - Tied to GND via R132 (330 |Omega|)
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
     - PCIe reference clock (negative)
   * - 12
     - UIM_CLK
     - NC
     - Not connected
   * - 13
     - REFCLK+
     - PCIE_REF_CLK_P
     - PCIe reference clock (positive)
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
     - TDD control output (P14)
   * - 18
     - GND
     - GND
     - Ground
   * - 19
     - Reserved
     - PCIE_CLK_IN
     - Reference clock input
   * - 20
     - W_DISABLE#
     - TDD1_GPIO
     - TDD control output (K15)
   * - 21
     - GND
     - GND
     - Ground
   * - 22
     - PERST#
     - PCIE_PERST#
     - PCIe reset (R89 NF)
   * - 23
     - PERn0
     - PCIE_PER0_N
     - PCIe data lane (negative)
   * - 24
     - 3.3Vaux
     - NC
     - Not connected
   * - 25
     - PERp0
     - PCIE_PER0_P
     - PCIe data lane (positive)
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
     - SMB_CLK
     - PCIE_CLK_OUT
     - Reference clock output
   * - 31
     - PETn0
     - PCIE_PET0_N
     - PCIe data lane (negative)
   * - 32
     - SMB_DATA
     - LA_I2C_SDA
     - I\ :sup:`2`\ C data (R139 NF)
   * - 33
     - PETp0
     - PCIE_PET0_P
     - PCIe data lane (positive)
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
     - GND via R143
   * - 38
     - USB_D+
     - NC
     - Not connected
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
     - WWAN LED (active low)
   * - 43
     - GND
     - GND
     - GND via R146
   * - 44
     - LED_WLAN#
     - LED_WLAN#
     - WLAN LED (active low)
   * - 45
     - Reserved
     - PCIE_RESERVED
     - I/O expander GPB7
   * - 46
     - LED_WPAN#
     - LED_WPAN#
     - WPAN LED (active low)
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
     - GPIO input (R12)
   * - 52
     - 3.3Vaux
     - VCC3P3_MPCIE
     - Main power input 3.3 V

.. note::

   - Pins in brackets in the Description column are LA9310 (IC6) pins. NF marks resistors that are not populated by default.
   - Pin 19 is connected to the clock input (CLK_IN) through R133, together with U.FL connector J1 (through R163). Connect only one external clock source at a time.
   - Pin 22 (``PCIE_PERST#``) does not reset the LA9310 by default. Fit R89 to connect it to the LA9310 reset circuit (see :doc:`bbprocessor`).
   - Pin 30 carries ``CLK_OUT`` through analogue switch IC22 and R136. Pins 30 and 32 can instead carry the LA9310 I\ :sup:`2`\ C bus by fitting R142 and R139 (and removing R136).
   - Pin 45 is connected to I/O expander IC15 output GPB7 through R147.
   - Pin 51 is connected to LA9310 ``GPIO_19`` through level converter IC8 and is pulled up to 3.3 V by R150.
   - The LED pins (42, 44, 46) are driven by I/O expander IC15 outputs GPA3, GPA2 and GPA1.
