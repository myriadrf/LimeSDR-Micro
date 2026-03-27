LimeSDR Micro
#############

.. toctree::
   :hidden:

   user/index
   reference/index
   beta/index

.. tab:: LimeSDR Micro M.2

   .. figure:: /images/limesdr-micro-m2-2280_ISO.jpg
      :align: center
      :width: 600

The LimeSDR Micro represents a breakthrough in software-defined radio technology, delivering professional-grade RF capabilities in M.2 2280 form factor. 
This innovative design enables seamless integration into embedded systems while maintaining the power and flexibility demanded by modern wireless applications. 
Powered by the NXP LA9310 baseband processor and the Lime Microsystems LMS7002M RF transceiver, it provides a flexible and powerful platform for developing wireless systems and solutions. 
Designed for seamless integration with a wide range of digital processors—including ASICs, general-purpose processors (GPPs), and GPUs—it supports applications across narrowband and broadband air interfaces. 

Specifications
**************

RF
==

.. list-table:: 
   :header-rows: 1
   :stub-columns: 1

   * - Parameter
     - Value
     - Notes
   * - Configuration
     - MISO (1T2R)
     - Full-duplex
   * - Frequency Range
     - 30 MHz – 3.8 GHz
     - Non-continuous coverage
   * - Bandwidth
     - > 100 MHz
     - Software configurable
   * - Sample depth
     - 12 bit
     - 
   * - Sample rate
     - up to 160 MSPS
     - 
   * - Max. Safe Rx Input Power
     - 10 dBm
     - Absolute maximum
   * - Rx Gain Range
     - 89 dB
     - LNA + TIA + PGA combined

Digital Interface
=================

M.2 B+M key edge connector with PCIe Gen 3 x1.

Power Supply
============

.. list-table:: 
   :header-rows: 1
   :stub-columns: 1

   * - Parameter
     - Value
     - Notes
   * - Input Voltage 
     - 3.3 V DC
     - Via M.2 connector
   * - Maximum Power 
     - 8 W
     - M.2 limit

.. note::
   Power consumption depends on configuration.

.. warning::
   Incorrect voltage or inadequate current capacity may cause damage or unstable operation.

Environmental
=============

.. list-table:: 
   :header-rows: 1
   :stub-columns: 1

   * - Parameter
     - Value
     - Notes
   * - Operating Temperature
     - -40 °C to +85 °C
     - Industrial-grade
   * - Storage Temperature
     - -40 °C to +85 °C
     - N/A
   * - Operating Humidity
     - 10% to 90% RH  
     - Non-condensing   

Mechanical
==========

M.2 2280 form factor, 22 × 80 mm, <20g weight.

Features
********


Devices
=======

* RF transceiver: Lime Microsystems LMS7002M
* BB processor: NXP Semiconductors LA9310X7S11AA

  * 157-pin LFBGA package (8mm x 8mm, 1.25mm)
  * Core type Arm Cortex-M4.
  * 307 MHz Operating frequency 
  * Integrated ADC/DAC (160 MSPS)
  * 66 kB SRAM
  * Configuration via JTAG

* Temperature sensor: TMP1075NDRLR
* EEPROM Memory: 128Kb EEPROM for LMS MCU firmware (optional); 512Kb EEPROM for BB processor data (optional)

Clock system
============

* 30.72 MHz on board VCTCXO
* VCTCXO may be tuned by GPSDO function or external PPS reference
* Reference clock input and output connectors (MHF4 and M.2)
* 1PPS input and output (MHF4 and M.2) 

General user inputs/outputs:
============================

* 2x Green LEDs
* 4x GPIOs in GPIO connector

Connections
===========

* Coaxial RF (MHF4 female) connectors
* BB processor JTAG connector (unpopulated)
* M.2 B+M key edge connector
* RF Baseband 15-pin FPC connectors

Purchasing
**********

Please see the  `Lime Micro website`_ for purchasing options.

Regulatory
**********

RoHS
====

This product is RoHS compliant and does not contain hazardous substances as defined by Directive 2011/65/EU.

WEEE
====

This product must be disposed of properly according to local regulations. Do not dispose of with general household waste.

RF Transmission Notice
======================

.. warning::
   Operating RF transmitting equipment may require appropriate licensing. Users are responsible for ensuring compliance with local regulations. Unauthorised transmission may result in legal penalties.


.. _Lime Micro Website: https://www.crowdsupply.com/lime-micro/limesdr-micro