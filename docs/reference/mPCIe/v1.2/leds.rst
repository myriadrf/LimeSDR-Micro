LEDs
####

The LimeSDR Micro mPCIe v1.2 board has two green indicator LEDs, located on the top side of the board near the RF shield (left edge). 

.. figure:: /images/LimeSDR-Micro_v1.2_components_LEDs.png
  :width: 600

  Figure 8. LimeSDR Micro mPCIe v1.2 indication LEDs (top)

The LEDs are connected to baseband processor GPIOs, so their function can be programmed to suit user requirements. 
The default LED configuration is shown in Table 14.

.. list-table:: Table 14. Default LED configuration
  :header-rows: 1

  * - Board Reference
    - Schematic Name
    - Board Label
    - BB Processor Pin
    - Description
  * - LED1
    - LA_LED1 
    - LED1
    - R11 (GPIO_17)
    - User defined
  * - LED2
    - LA_LED2
    - LED2
    - P12 (GPIO_18)
    - User defined

