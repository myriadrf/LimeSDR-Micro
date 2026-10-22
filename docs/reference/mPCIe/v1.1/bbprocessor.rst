Baseband Processor
##################

The LimeSDR Micro mPCIe v1.1 board is built around the `NXP LA9310`_ baseband processor (IC6). The LA9310 contains an Arm Cortex-M4 core and a VSPA (Vector Signal Processing Accelerator) DSP. It connects the LMS7002M RF transceiver to the host over PCIe and controls the other devices on the board.

This section describes the LA9310 boot configuration, its baseband RF channels, and the digital interfaces used on the board.

Configuration
=============

The LA9310 reads its boot configuration from several multi-function pins when it comes out of power-on reset. After reset these pins work as GPIOs or in their other functions. On the board, each configuration pin is set by a 10 k\ |Omega| pull-up to 1.8 V or a 3.3 k\ |Omega| pull-down to ground.

The default configuration is:

- ``CFG_BOOT_SRC[1:0]`` (pins P15 and M14): ``11``, ROM boot. ``CFG_BOOT_SRC1`` is pulled up by R111 and ``CFG_BOOT_SRC0`` is pulled up by R110. To boot from the I\ :sup:`2`\ C EEPROM (``10``), remove R110 and fit R120. See :doc:`/advanced/boot_source/index`.
- ``CFG_BOOT_HO`` (pin R14): ``1``, the M4 core starts booting as soon as the reset state machine reaches SYSREADY. Pulled up by R112.
- ``CFG_RST_HNDSHK`` (pin P14): ``1``, the reset state machine pauses so that software can perform the necessary configuration. Pulled up by R113.
- ``CFG_TEST_PORT_DIS`` (pin M15): ``1``, the test port is disabled. Pulled up by R114.
- ``CFG_WRM_RSTB`` (pin M8): ``0``, warm reset; memory initialization steps may be skipped. Pulled down by R125.
- ``CFG_SYSRDY_EVT`` (pin R9): ``0``, the boot sequence determines the SYSREADY state through an event that wakes the M4 core from WFE. Pulled down by R126.
- ``CFG_PCIE_GEN`` (pin P13): ``0``, the PCIe interface can negotiate up to Gen2 (5 GT/s). Pulled down by R127.

.. note::

   Pin P14 also drives ``TDD0_GPIO`` (R129, IC13) on mPCIe pin 17. While the LA9310 is in reset, this signal follows the configuration pin level. See `GPIOs`_.

RF
==

The NXP LA9310 provides two main baseband receive channels (RX0 and RX1) that accept differential I/Q baseband signals for digital processing, and one transmit channel (TX) that outputs differential I/Q baseband signals for conversion to RF by external radio circuitry. Additionally, two receive observation channels (RO0 and RO1) allow sampling of external I/Q baseband signals for monitoring, feedback, and signal analysis.

Main
----

The LA9310's main I/Q channels interface with the LMS7002M RF transceiver, which provides RF upconversion and downconversion between the I/Q baseband signals and the RF domain.

For more information about the LMS7002M, see :doc:`rftransceiver`. The RF front end is described in :doc:`rfcontrol`.

Observation
-----------

The NXP LA9310 provides two additional I/Q baseband input channels (RO0 and RO1) for signal observation purposes. These channels have their own ADCs and are independent of the main receive channels (RX0 and RX1).

The baseband observation channels are accessible through the 15-pin, 0.3 mm-pitch FPC connector (X13). The connector pinout and corresponding signal descriptions are provided in Table 2.

.. list-table:: Table 2. LA9310 RX observation 15-pin FPC connector (X13)
   :header-rows: 1
   :stub-columns: 1

   * - Pin
     - Schematic signal name
     - Description

   * - 1
     - GND
     - Ground

   * - 2
     - LA_RO0_EXT_I_P
     - Observation channel 0 in-phase signal differential positive

   * - 3
     - LA_RO0_EXT_I_N
     - Observation channel 0 in-phase signal differential negative

   * - 4
     - GND
     - Ground

   * - 5
     - LA_RO0_EXT_Q_P
     - Observation channel 0 quadrature signal differential positive

   * - 6
     - LA_RO0_EXT_Q_N
     - Observation channel 0 quadrature signal differential negative

   * - 7
     - GND
     - Ground

   * - 8
     - VCC3P3
     - Power (3.3 V)

   * - 9
     - GND
     - Ground

   * - 10
     - LA_RO1_EXT_I_P
     - Observation channel 1 in-phase signal differential positive

   * - 11
     - LA_RO1_EXT_I_N
     - Observation channel 1 in-phase signal differential negative

   * - 12
     - GND
     - Ground

   * - 13
     - LA_RO1_EXT_Q_P
     - Observation channel 1 quadrature signal differential positive

   * - 14
     - LA_RO1_EXT_Q_N
     - Observation channel 1 quadrature signal differential negative

   * - 15
     - GND
     - Ground

.. note::

   Each observation input is connected to the LA9310 through a 47 |Omega| series resistor (R90–R97). By default, all observation inputs are tied to ground through 0 |Omega| resistors R99–R106. Remove R99–R106 before connecting an external signal source to X13. There are no AC coupling capacitors or bias components on the board, so the external signal source must provide a suitable common-mode voltage, or the LA9310 observation ADCs must be configured to match the input.


Interfaces
==========

The LA9310 digital interfaces used on the board are described below: the SPI, UART and I\ :sup:`2`\ C peripheral buses, the PCIe host connection, the JTAG debug connector and the TDD control GPIOs.

SPI
---

The LA9310 SPI interface is used to configure the LMS7002M RF transceiver (IC1) and the ADF4002 phase detector (IC23). The LA9310 SPI pins operate at 1.8 V and are translated to 3.3 V by level converters IC8 and IC12. SPI signals, LA9310 pins and I/O standards are listed in Table 3.

.. list-table:: Table 3. LA_SPI interface pins
   :header-rows: 1

   * - Schematic signal name
     - BB processor pin
     - I/O standard
     - Comment

   * - LA_SPI_SCLK
     - P8
     - 3.3 V
     - Serial Clock (LA output)

   * - LA_SPI_MOSI
     - R9
     - 3.3 V
     - Data (LA output)

   * - LA_SPI_MISO
     - R8
     - 3.3 V
     - Data (LA input)

   * - LA_SPI_LMS_SS
     - P7
     - 3.3 V
     - IC1 (LMS7002M) SPI slave select (LA output)

   * - LA_SPI_ADF_SS
     - P11
     - 3.3 V
     - IC23 (ADF4002) SPI slave select (LA output)

UART
----

The LA9310 UART provides communication with the GNSS receiver module (IC11). The signals are translated between 1.8 V and 3.3 V by level converter IC12. UART signals, LA9310 pins and I/O standards are listed in Table 4.

.. list-table:: Table 4. LA9310 UART interface pins
   :header-rows: 1

   * - Schematic signal name
     - BB processor pin
     - I/O standard
     - Comment

   * - GNSS_TXD
     - P10
     - 3.3 V
     - UART1_SOUT, to GNSS receiver UART RX (LA output)

   * - GNSS_RXD
     - P9
     - 3.3 V
     - UART1_SIN, from GNSS receiver UART TX (LA input)

I\ :sup:`2`\ C
--------------

The LA9310 I\ :sup:`2`\ C interface (``IIC1``) is used to manage the on-board peripheral devices. The ``IIC1_SCL`` (pin P6) and ``IIC1_SDA`` (pin R6) pins operate at 1.8 V and are connected to the 3.3 V ``LA_I2C`` bus through MOSFET level shifters VT1 and VT2. The devices on the bus and their addresses are listed in Table 5.

.. list-table:: Table 5. LA_I2C bus devices
   :header-rows: 1

   * - Board reference
     - Device
     - I2C address

   * - IC9
     - Temperature sensor
     - 1 0 0 1 0 1 1 RW

   * - IC14
     - EEPROM
     - 1 0 1 0 0 0 0 RW

   * - IC15
     - I/O expander
     - 0 1 0 0 0 0 0 RW

   * - IC21
     - XO DAC
     - 1 0 0 1 1 0 0 RW

   * - IC26
     - Switching regulator
     - 1 1 0 0 0 0 0 RW (I2C_SDA_SEL = 0)

   * - IC30
     - Switching regulator
     - 1 1 0 0 0 0 0 RW (I2C_SDA_SEL = 1)

Switching regulators IC26 and IC30 share the same I\ :sup:`2`\ C address. Analog switch IC32 routes ``LA_I2C_SDA`` to one regulator at a time, as selected by the ``I2C_SDA_SEL`` signal from I/O expander IC15 (pin GPB3).

The ``LA_I2C`` bus, the regulator enable signal ``EN_REG`` and ``CFG_BOOT_SRC0`` are also available on the 6-pin header footprint X6 (not populated).

PCIe
----

The LA9310 connects to the host over a single PCIe lane through the :doc:`mpcie` (X10). By default, the link can negotiate up to PCIe Gen2 (5 GT/s), as set by ``CFG_PCIE_GEN`` (see `Configuration`_).

The LA9310 hard reset input ``HRESET_B`` (pin K13, net ``LA_HRESET``) is pulled up to 1.8 V by R87. It is pulled low through diode D1 while the JTAG reset ``LA_TRST`` is low. ``LA_TRST`` is pulled up by R86, and C138 holds it low for a short time at power-up, so both resets are released after power-up. The host ``PCIE_PERST#`` signal is not connected by default; it can be connected to ``LA_TRST`` by fitting R89.

``GPIO_19/ASLEEP`` (pin R12) receives the mPCIe ``PCIE_W_DISABLE2#`` signal (pin 51) through level converter IC8 and R73 (0 |Omega|). R150 pulls ``PCIE_W_DISABLE2#`` up to 3.3 V.

.. _NXP LA9310: https://www.nxp.com/part/LA9310S7S11AA

JTAG
----

The LA9310 can be accessed for debugging through a 6-pin compression connector footprint (X9) on the bottom side of the board, compatible with the `Molex 788641001`_ connector. X9 is not fitted by default. The JTAG connector pinout, LA9310 pins and I/O standards are listed in Table 6.

.. list-table:: Table 6. JTAG connector (X9) pins
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
     - 1.8 V
     - Test Data Output

   * - 2
     - LA_TDI
     - M10
     - 1.8 V
     - Test Data Input

   * - 3
     - LA_TMS
     - M12
     - 1.8 V
     - Test Mode Select

   * - 4
     - VCC1P8
     -
     - 1.8 V
     - Reference voltage

   * - 5
     - LA_TCK
     - N10
     - 1.8 V
     - Test Clock

   * - 6
     - LA_HRESET
     - K13
     - 1.8 V
     - Reset, connected to HRESET_B via R88

GPIOs
-----

The board has no GPIO connector. Two TDD control signals, ``TDD0_GPIO`` and ``TDD1_GPIO``, are translated to 3.3 V by level converter IC13 and routed to mPCIe pins 17 and 20. Each signal can be driven from one of several LA9310 pins, selected by 0 |Omega| resistors, as listed in Table 7.

.. list-table:: Table 7. TDD control signal sources
   :header-rows: 1
   :stub-columns: 1

   * - Signal
     - mPCIe pin
     - Default source (resistor)
     - Alternative sources (resistor, not populated)

   * - TDD0_GPIO
     - 17
     - P14, PA_EN/GPIO_12 (R129)
     - M14, TXRX0/GPIO_07 (R118); L13, GPIO_05/TX_ACTIVE0 (R119)

   * - TDD1_GPIO
     - 20
     - K15, GPIO_06/TX_ACTIVE1 (R131)
     - P15, TXRX1/GPIO_08 (R130)

The two user LEDs are also driven by LA9310 GPIOs, as described in :doc:`leds`.

.. _Molex 788641001: https://www.molex.com/en-us/products/part-detail/788641001
