Beta Programme
##############

This is the documentation for the LimeSDR Micro Beta Programme. 

Beta hardware is provided as-is for evaluation and testing purposes only and is not intended for production use. The Beta Programme hardware and software support may contain bugs or issues that are not present in the final production version of the LimeSDR Micro.

Status
******

LimeSDR Micro uses the Lime Suite NG driver stack and hardware support is currently in heavy development, hence not all features are fully implemented yet. Recent developments:

* **01/01/2026**. Kernel module automatically loaded at boot and no longer requires manual insertion.
* **17/12/2025**. Fixes to resolve transmit hang/fail and Tx timestamping issues, which also means that TDD operation is now possible.

The current status as of **17th December 2025** is as follows:

Platform Support
================

Intel
-----

MSI capabilities detection is not yet implemented in the driver, which may result in issues on some Intel platforms.

ARM
---

Basic testing has been performed on Raspberry Pi 5 and NXP FRDM-IMX8MPLUS.

Cache coherency is currently implemented using polling, which may impact performance on some ARM platforms. Work is ongoing to implement proper cache maintenance operations.

General
=======

Channel Configuration
---------------------

Only 1 transmit + 1 receive channel (1T1R) is currently supported.

Support for additional receive channels will be added in due course.

Sampling Rate
-------------

The sampling rate is currently hardcoded in the firmware. See the Advanced Topics section for details on changing this. 

Support for dynamic sampling rate configuration is planned.

Sample Timestamp and TDD
------------------------

Receive timestamping and timestamped transmit streaming have been implemented, and TDD operation has been verified with the Amarisoft cellular stack.  

However, there are limitations: transmission is done in 512 samples chunks and if less data is provided, it gets padded with zeroes. 

In addition to which, the RF switches cannot be controlled based on the timer with the current board version. Hence while Tx has no data to transmit, the DAC is still connected to the antenna and is transmitting zeroes. 

.. note::
   The hardware design has been updated, so that with the next batch of boards the RF switches can be controlled based on the timer.

Decimation and Interpolation
----------------------------

Support for this is present in the VSPA firmware, but not yet implemented in the driver.

Firmware Loading
----------------

At present the ARM M4 and VSPA firmware are loaded when the driver module is inserted. Support for dynamic firmware loading is planned, which will include loading different firmware images based on user configuration.  

Getting Started
***************

Install Lime Suite NG
=====================

.. warning::
   The kernel headers for your current kernel must be installed prior to building Lime Suite NG. If Secure Boot is enabled on your system, you should also ensure that DKMS is installed and configured to sign kernel modules.

.. note::
   If you would like SoapySDR support, please ensure you have SoapySDR installed prior to building Lime Suite NG. Similarly, if you would like GNU Radio support, ensure you have GNU Radio installed prior to building Lime Suite NG, otherwise the *gr-limesuiteng* source/sink blocks will not be built.

At the present time the *limesdr-micro* branch should be used.

.. code:: bash

    git clone -b limesdr-micro https://github.com/myriadrf/LimeSuiteNG
    cd LimeSuiteNG
    sudo ./install_dependencies.sh
    cmake -B build && cd build
    make
    sudo make install
    sudo ldconfig

Basic Test
==========

To verify operation:

1. Configure the board

.. code:: bash

   limeConfig --initialize --rxen=1 --txen=1 --rxlo=1.2e9 --txlo=1.2e9 --txpath=Band2 --rxpath=LNAL --rxgain=0 --txgain=60

2. Configure internal RF loopback

.. code:: bash

   ./bin/limeSPI write -c LMS7002M -s 010C88C5,010D0117,0113017D,01016001 

3. Run test

.. code:: bash

   ./bin/frontendDelayTest --plot 

   Tx chirp sent @ 30720 length: 10241
   Rx Ch0 chirp found @ 30753, samples diff:33, time diff: 1us , signal correlation: 354.889 

If you have GNUPlot installed it will output two graphs: all received data, and zoomed in section where expected signal should be.

.. figure:: /images/chirp.png
   :alt: Frontend Delay Test Output

   Frontend Delay Test Output

Simple Tx, Rx and TRX
=====================

The following assumes that the board has been configured using limeConfig as shown in the Basic Test section above.

To continuously transmit samples from file (little endian 16-bit interleaved IQ values):

.. code:: bash

   limeTRX --input SamplesFile.bin --looptx

To receive samples to file (capture duration 3000ms):

.. code:: bash

   limeTRX --output RxDataFile --time=3000

To act as repeater Rx->Tx:

.. code:: bash

   limeTRX --repeater=0

Advanced Topics
***************

Debugging
=========

For testing there is the :code:`build/bin/iqmonitor` application that monitors the DMEM_PROXY section where hardware data counters are placed.

Counters represent 2048 byte blocks.

.. code::

   RX stats :
    DMA_AXIQ_RD    0x00000000(00000000 MB/s) // data got from ADC
    DMA_DDR_WR    0x00000000(00000000 MB/s) // data sent to host
    APP_DDR_WR    0x00000000  // data consumed by host application
    DMA_DDR_WR_OVR    0x00000000 // data overruns, host is reading to slow
   TX stats :
    DMA_AXIQ_WR    0x00000000(00000000 MB/s) // data sent to DAC
    DMA_DDR_RD    0x00000000(00000000 MB/s) // data received from host
    APP_DDR_WR    0x00000000 // data produced by host application 

After firmware boot, the first transmission attempt might not transmit anything, seems to be an issue within VSPA, how the Tx AXIQ enable and Tx DMA allowed signals interact. Depending on their order Tx AXIQ can get stuck. You can use limesuiteng/build/bin/iqmonitor to see the VSPA counters.

For example, the first run of frontendDelayTest, the app has provided the data, VSPA has read it from RAM, but the enqueued DMA transfers to DAC do not complete even though the PHYTimer11 (DAC IQ Tx DMA Allowed) is enabled.

.. code::

   TX stats :
   DMA_AXIQ_WR    0x00000000(00000000 MB/s)
   DMA_DDR_RD    0x00000007(00000000 MB/s)
   APP_DDR_WR    0x00000207         

Changing the Sampling Rate
==========================

At the time of writing, LimeSDR Micro uses a hardcoded sampling rate which is defined in the firmware. The default firmware is set to have a 30.72MHz sampling rate ~122.88MB/s. To change the sampling rate it is neccessary to recompile firmware from source, which can be found here:

https://github.com/myriadrf/LimeSDR-Micro_FW

The sampling rate will be half of the reference clock frequency set by cmake. E.g.: 

.. code:: bash

   cmake .. -DLA9310_REF_CLK_FREQ=61440000

Built firmware file will be placed in :code:`LimeSDR-Micro_FW/build/Release/la9310.bin`.

The driver loads firmware from :code:`/lib/firmware/la9310.bin` location, so either overwrite it, or replace it with a symlink to your custom firmware build.

In order to load new firmware, it will be neccessary to restart the system.

.. note::
   This is just a temporary situation until dynamic sampling rate configuration is implemented, along with support also for dynamic firmware loading.