Update Bootloader
##################

.. warning::

   This procedure should only be performed if specifically advised to do so by Lime Microsystems support. Do not attempt it otherwise.

This guide describes the bootloader update procedure for LimeSDR Micro M.2 boards, using the LimeSuiteNG command line interface (CLI).

.. note::

   For general installation and usage instructions for LimeSuiteNG, see the :external+suiteng:doc:`LimeSuiteNG User Guide <index>`.

Updating the Bootloader
=======================

1. Ensure that the host computer is powered off.
2. Set the board's boot source to PCIe. See :doc:`/advanced/boot_source/index` for instructions specific to your board's form factor and version.
3. Install the DUT into the host computer's M.2 connector and secure it with the retaining screw.

   .. warning::

      Ensure there is no unintended conductive or bare metal-to-metal contact between the LimeSDR Micro and any host hardware.

4. Power on the host computer and allow the operating system to boot completely.
5. Open a terminal window and confirm that the DUT is enumerated and communicating correctly with the host computer. Since the DUT is running from its bootloader ROM, which only includes PCIe drivers, verify this using the ``lspci`` command instead of LimeSuiteNG's own device discovery:

   .. code-block:: shell

      lspci -d 1957:1c12

   If the DUT is detected, it will be listed in the command output, with NXP vendor ID ``1957`` and device ID ``1c12``. If no devices are listed, check the DUT's connection and seating in the host computer's M.2 connector before continuing.

6. Execute the following command to flash the bootloader to the EEPROM memory:

   .. code-block:: shell

      limeFLASH -t EEPROM [PATH_TO_EEPROM_FOLDER/]limesdr-micro-eeprom.bin

7. Wait for the programming process to complete.

   .. warning::

      Do not power off the computer or remove the DUT while programming is in progress.

   If the programming completes successfully, the utility will display the following message:

   .. code-block:: text

      VSPA no clock
      VSPA firmware not running?
      File size : 832 bytes.
      Remaining: 0
      Programming completed. Power cycle the device to boot updated gateware

   If any other message is displayed, or if the utility reports an error, copy the error message and contact the Lime Microsystems support team for further assistance.

8. After successful programming, shut down the host computer using the normal operating system shutdown procedure.
9. Once the computer has completely powered off, set the board's boot source back to I\ :sup:`2`\ C EEPROM. See :doc:`/advanced/boot_source/index` for instructions specific to your board's form factor and version.
10. The board is now ready for the subsequent functional test procedure.

.. note::

   The boot source should only be set to PCIe for the duration of the bootloader programming procedure.
