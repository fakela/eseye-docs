# Over-the-air (OTA) updates

AnyNet SMARTconnect™ supports over the air (OTA) updates for the following software, using parameters set in the configuration file:

* Host
* Kernel (Module operating firmware)
* AnyNet SMARTconnect™ application
* Configuration file

For more information, see [Using the AnyNet SMARTconnect™ configuration file](../getting-started/using-the-anynet-smartconnect-tm-configuration-file.md).

## Updating host firmware

Modify the AnyNet SMARTconnect™ configuration file to contain the URL for the host firmware. The host must request AnyNet SMARTconnect™ to check for updates. If an update is available, AnyNet SMARTconnect™ will download it into flash memory and send a URC to the host, indicating that new firmware is available. The host then reads the firmware image in chunks, using AT commands. A checksum is provided to ensure the copy from AnyNet SMARTconnect™ to host has completed without errors.

For more information, see [Updating AnyNet SMARTconnect™ software and host module firmware](updating-anynet-smartconnect-tm-software-and-host-module-firmware.md).

## Updating kernel, AnyNet SMARTconnect™ application and configuration software

Trigger updates to the modem kernel, AnyNet SMARTconnect™ application and configuration using either the host, cloud IoT service, or SMS.

The URL used to download the images is set in the AnyNet SMARTconnect™ configuration file. In order to apply updates, AnyNet SMARTconnect™ must reboot. For more information, see [update\_autoreboot in the configuration file](../getting-started/using-the-anynet-smartconnect-tm-configuration-file.md).

For more information, see [Updating AnyNet SMARTconnect™ software and host module firmware](updating-anynet-smartconnect-tm-software-and-host-module-firmware.md).
