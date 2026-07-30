VSPA Firmware Tracing
#####################

Tracing may prove useful for debugging and performance analysis of VSPA firmware.

.. warning::
   Tracing has a performance impact and enabling this in firmware which is already resource constrained may make the problem worse.

.. warning::
   The tracing functionality is bare bones, and does not account for edge cases, like losing markers to due DMA unavailability, or generating too many markers before submitting for transfer. Use with caution and at your own risk!

Each VSPA trace marker store consumes ~30 cycles, therefore tracing is disabled by default so as to not affect performance.

Enabling
********

VSPA tracing has to be `enabled in the firmware source`_.

Markers `buffer capacity is set here`_.

.. warning::
   The number of added markers should not exceed this capacity within a single ``main()`` execution.

.. warning::
   DMA transfers tracing is approximate; it only indicates the DMA descriptor submit moment, not the actual start of DMA activity, and the end is not the actual hardware completion moment, but the moment that firmware checks the completion status.

Capture
*******

To capture the trace:

1. Enable tracing in firmware
2. Load VSPA firmware
3. Run ``LimeSuiteNG/build/bin/limeVSPA -d /dev/limesdr_micro0/control0 -t``
4. Run the application to be traced
5. Terminate ``limeVSPA`` with Ctrl+C, it will produce a ``trace.json`` file in the working directory.
6. Load the ``trace.json`` file to https://ui.perfetto.dev/, example attached screenshot and trace json file.

limeVSPA captures markers indefinitely — until stopped — and depending on VSPA activity it can result in huge output files.

Markers data can only have integers, so the translation from integers to names is `done within the limeVSPA application`_. This is currently hardcoded, but there are plans to extend it to load external dictionary for firmware specific markers.

Example
*******

.. figure:: /images/VSPAtrace.png
   :alt: VSPA trace
   :align: center
   :width: 1024

   Click on the image to enlarge it.

The above example was generated from this :download:`capture file </_static/downloads/trace.json.zip>`.

.. _enabled in the firmware source: https://github.com/myriadrf/LimeSDR-Micro_VSPA/blob/0c5eb13446bb4e0120619a479133533cbecdb234/Sources/l1-trace.h#L10

.. _buffer capacity is set here: https://github.com/myriadrf/LimeSDR-Micro_VSPA/blob/0c5eb13446bb4e0120619a479133533cbecdb234/Sources/l1-trace.c#L14

.. _done within the limeVSPA application: https://github.com/myriadrf/LimeSuiteNG/blob/cf54024de8f8c169ede711a3d999c553df579826/cli/limeVSPA/profiler.cpp#L73-L238
