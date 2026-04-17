LEDs
####

The board comes with two green indicator LEDs. These LEDs are soldered on the top of the board near RF shield (left edge). 

.. figure:: /images/LimeSDR-Micro_v1.2_components_LEDs.png
  :width: 600

  Figure 8. LimeSDR Micro mPCIe v1.2 indication LEDs (top)

LEDs are connected to baseband processors GPIOs hence their function may be programmed according to the user requirements. 
Default LEDs configuration and description are shown in Table 9.

.. list-table:: Table 9. Default LEDs configuration
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
