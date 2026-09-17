# Updating AnyNet SMARTconnect™ software and host module firmware

### Before you begin

* Using a terminal emulator, ensure AnyNet SMARTconnect™ is connected to the network, with an ETMSTATE of 7. For more information, see [etmstate-check-current-state.md](../at-command-reference/management-at-commands/etmstate-check-current-state.md "mention").
* Use AT+ETMINFO="imei" to find out and note the Quectel BG95 module IMEI. For more information, see [etminfo-displays-anynet-smartconnect-tm-and-device-information.md](../at-command-reference/management-at-commands/etminfo-displays-anynet-smartconnect-tm-and-device-information.md "mention").
*   Eseye supplies the following files for updating AnyNet SMARTconnect™:

    * Configuration file (eseyeconfig.ini)
    *   Quectel BG95 module firmware update file (BG95M3LARxxAxx\_xx.xxx.xx.xxx-BG95M3LARxxAxx\_xx.xxx.xx.xxx.bin)

        Quectel modem firmware update packages are Delta FOTA (DFOTA) type, which are designed to update the firmware from a specific version to another specific version.
    * AnyNet SMARTconnect™ application (etm\_application.ota)

    To request these files, speak to your Account Manager.

    You may choose to create your own configuration file for updating the Quectel BG95 module. For information about the configuration file, see [using-the-anynet-smartconnect-tm-configuration-file.md](../getting-started/using-the-anynet-smartconnect-tm-configuration-file.md "mention").
* If required, store the update files on a server and note the URLs to each file.
* If required, store the host firmware update on a server and note the URL to the file.

## About AnyNet SMARTconnect™ update

Each AnyNet SMARTconnect™ software version is developed for a specific Quectel BG95 module firmware version. When an AnyNet SMARTconnect™ update occurs, the older version remains stored in the ../datatx folder.

At each boot, AnyNet SMARTconnect™ checks that the currently running AnyNet SMARTconnect™ version is correct for the current Quectel BG95 module firmware version. If it is not correct, the older version is used instead. If no older version is found, AnyNet SMARTconnect™ uses the available version.

## Updating the AnyNet SMARTconnect™ application and Quectel BG95 module firmware

For information about the AT commands used in this procedure, see [management-at-commands](../at-command-reference/management-at-commands/ "mention").

To update AnyNet SMARTconnect™ application and Quectel BG95 module firmware at the same time:

1.  Set the URL from which to download AnyNet SMARTconnect™ application. Send:

    AT+ETMCFG="application","updateurl","\<http(s)://ETMappURL>"

    where \<http(s)://ETMappURL> is the absolute URL for downloading etm\_application.ota.

    OK
2.  Set the URL from which to download the Quectel BG95 module update package. Send:

    AT+ETMCFG="application","fotaurl",""

    where is the absolute URL for downloading .bin.

    OK
3.  Save the configuration changes. Send:

    AT+ETMCFG="save"

    OK
4.  Trigger AnyNet SMARTconnect™ application and Quectel BG95 module firmware download and update. Send:

    AT+ETMFWCHECK

    AnyNet SMARTconnect™ downloads the new application, then performs a CRC32 check to ensure the file is valid and the new AnyNet SMARTconnect™ version is different from the existing AnyNet SMARTconnect™ version.

    If the file is not valid, or AnyNet SMARTconnect™ version is the same as a previously stored version, no AnyNet SMARTconnect™ update will occur.

    If the download completes successfully and the versions are different, then AnyNet SMARTconnect™ updates the datatx/oem\_app\_path.ini file to apply the new application.

    The Quectel BG95 module firmware then downloads.

    The following response occurs:

    +ETMFWCHECK: complete

    After the download completes, the Quectel BG95 module firmware is updated.

    If the update is successful, the Quectel BG95 module will automatically reboot.

    If only AnyNet SMARTconnect™ is successfully updated, the modem will reboot according to the configuration file \[operation] update\_autoreboot parameter setting:

    * 0 – The system requires a manual reboot
    * 1 – The system reboots automatically

For information about how AnyNet SMARTconnect™ application is stored and used in the datatx folder, see About AnyNet SMARTconnect™.

## Updating the AnyNet SMARTconnect™ application only

For information about the AT commands used in this procedure, see [management-at-commands](../at-command-reference/management-at-commands/ "mention").

To update AnyNet SMARTconnect™ application:

1.  Clear the current URL configuration for the Quectel BG95 module firmware update. Send:

    AT+ETMCFG="remove","application","fotaurl"

    OK
2.  Set the URL from which to download AnyNet SMARTconnect™ application. Send:

    AT+ETMCFG="application","updateurl","\<http(s)://ETMappURL>"

    where \<http(s)://ETMappURL> is the absolute URL for downloading etm\_application.ota.

    OK
3.  Save the configuration changes. Send:

    AT+ETMCFG="save"

    OK
4.  Trigger AnyNet SMARTconnect™ application to download and update AnyNet SMARTconnect™ application. Send:

    AT+ETMFWCHECK

    AnyNet SMARTconnect™ downloads the new application, then performs a CRC32 check to ensure the file is valid and the new AnyNet SMARTconnect™ version is different from the existing AnyNet SMARTconnect™ version.

    If the file is not valid, or AnyNet SMARTconnect™ version is the same as a previously stored version, no AnyNet SMARTconnect™ update will occur.

    If the download completes successfully and the versions are different, then AnyNet SMARTconnect™ updates the datatx/oem\_app\_path.ini file to apply the new application.

    The following response occurs:

    +ETMFWCHECK: complete

    If the configuration file \[operation] update\_autoreboot parameter is set to 1, then AnyNet SMARTconnect™ sends the +ETM: REBOOTING URC and will reboot automatically, otherwise AnyNet SMARTconnect™ sends the +ETM: REBOOT REQUIRED URC.
5.  If required, reboot the system. Send:

    AT+ETMRESET

Downloading the device host firmware

For information about the AT commands used in this procedure, see [management-at-commands](../at-command-reference/management-at-commands/ "mention").

To download device host firmware:

1.  Set the URL from which to download the device host firmware. Send:

    AT+ETMCFG="host","updateurl","\<http(s)://HostFirmwareURL>"

    where \<http(s)://HostFirmwareURL> is the absolute URL for downloading the host firmware.

    OK
2.  Save the configuration changes. Send:

    AT+ETMCFG="save"

    OK
3.  Trigger the host firmware download. Send:

    AT+ETMHFWGET

    The response is either:

    * +ETMHFWGET: available – AnyNet SMARTconnect™ successfully downloaded the file.
    * +ETMHFWGET: none – the file download was not successful. Check the URL is correct and accessible, then try AT+ETMHFWGET again.

To read the file, use the AT+ETMHFWREAD command. For more information, see [etmhfwread-reads-a-section-of-the-new-host-firmware-image.md](../at-command-reference/management-at-commands/etmhfwread-reads-a-section-of-the-new-host-firmware-image.md "mention").

To delete the downloaded file from datatx folder, use the AT+ETMHFWCONF command. For more information, see [etmhfwconf-confirms-the-new-host-firmware-is-applied.md](../at-command-reference/management-at-commands/etmhfwconf-confirms-the-new-host-firmware-is-applied.md "mention").

## Updating the AnyNet SMARTconnect™ configuration file

For information about the AT commands used in this procedure, see [management-at-commands](../at-command-reference/management-at-commands/ "mention").

To update AnyNet SMARTconnect™ configuration file:

1.  Set the URL from which to download AnyNet SMARTconnect™ configuration file. Send:

    AT+ETMCFG="config","updateurl","http(s)://eseyeconfigURL"

    where \<http(s)://eseyeconfigURL> is the absolute URL for downloading _eseyeconfig_.ini.

    OK
2.  Save the configuration changes. Send:

    AT+ETMCFG="save"

    OK
3.  Trigger the download and update of the configuration file. Send:

    AT+ETMCFGCHECK

    +ETMCFGCHECK: complete

    AnyNet SMARTconnect™ either reboots automatically (+ETM: REBOOTING) or requires manual rebooting (+ETM: REBOOT REQUIRED) according to the newly updated configuration file \[operation] update\_autoreboot parameter:

    * 0 – The system requires a manual reboot
    * 1 – The system reboots automatically

    If the download process fails, check the URL is correct and accessible, then try AT+ETMCFGCHECK again.
4.  If required, reboot the system. Send:

    AT+ETMRESET

## Using the MQTT broker to update files

AnyNet SMARTconnect™ can accept some commands sent by the MQTT broker on the topic \[mqtt] mqttsettingstopic/\[mqtt] topicsuffix.

Send all commands in plain text format (ASCII).

AnyNet SMARTconnect™ accepts the following commands:

| Command                                         | Function                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| ----------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| config,,,                                       | Sets the specified configuration file parameter to the specified value.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| default                                         | Sets the configuration file to default values.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| fwupdate where is the Quectel BG95 module IMEI. | Triggers the specified update when the following parameters are set: - \[application] updateurl – triggers only AnyNet SMARTconnect™ application update - \[application] fotaurl – triggers both AnyNet SMARTconnect™ application and the Quectel BG95 module firmware update, but only if \[application] updateurl is also set. If the update includes the Quectel BG95 module firmware and is successful, the Quectel BG95 module will automatically reboot. If only AnyNet SMARTconnect™ is successfully updated, the modem will reboot according to the configuration file \[operation] update\_autoreboot parameter setting: - 0 – The system requires a manual reboot - 1 – The system reboots automatically For information about how AnyNet SMARTconnect™ application is stored and used in the datatx folder, see About AnyNet SMARTconnect™. |
| reboot                                          | Reboots the Quectel BG95 module and AnyNet SMARTconnect™.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| revert                                          | Returns the configuration file to the previously saved state, losing any unsaved changes.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| save                                            | Saves any changes to the configuration file.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |

## Using SMS to update files

AnyNet SMARTconnect™ can accept some commands sent via SMS.

SMS is only accepted if it is sent from a number found in the configuration file \[SMS] allowedlist.

Send all commands in plain text format (ASCII).

AnyNet SMARTconnect™ accepts the following commands in the SMS body:

| Command                                                                                                                                                         | Function                                                                                                                                                                                                                                                                                                                                                                                                                     |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| config save                                                                                                                                                     | Saves any changes to the configuration file.                                                                                                                                                                                                                                                                                                                                                                                 |
| config,,,                                                                                                                                                       | Sets the specified configuration file parameter to the specified value.                                                                                                                                                                                                                                                                                                                                                      |
| download application \<http(s)://ETMappURL> where \<http(s)://ETMappURL> is the absolute URL for downloading etm\_application.ota.                              | Triggers AnyNet SMARTconnect™ application update. If the update is successful, , the modem will reboot according to the configuration file \[operation] update\_autoreboot parameter setting: - 0 – The system requires a manual reboot - 1 – The system reboots automatically For information about how AnyNet SMARTconnect™ application is stored and used in the datatx folder, see About AnyNet SMARTconnect™.           |
| download combo \<http(s)://ETMappURL>,\<http(s)://QuectelDFOTAfirmwareURL> where \<http(s)://QuectelDFOTAfirmwareURL> is the absolute URL for downloading .bin. | Triggers both AnyNet SMARTconnect™ application and Quectel BG95 module firmware updates. If the update is successful, the Quectel BG95 module will automatically reboot. If only AnyNet SMARTconnect™ is successfully updated, the modem will reboot according to the configuration file \[operation] update\_autoreboot parameter setting: - 0 – The system requires a manual reboot - 1 – The system reboots automatically |
| download config \<http(s)://eseyeconfigURL> where \<http(s)://eseyeconfigURL> is the absolute URL for downloading _eseyeconfig_.ini.                            | Triggers AnyNet SMARTconnect™ configuration file update.                                                                                                                                                                                                                                                                                                                                                                     |
| download host \<http(s)://HostFirmwareURL> where \<http(s)://HostFirmwareURL> is the absolute URL for downloading the host firmware.                            | Triggers the device host file download.                                                                                                                                                                                                                                                                                                                                                                                      |
| get cfg                                                                                                                                                         | Returns the specified configuration file parameter in the following format::=                                                                                                                                                                                                                                                                                                                                                |
| get swver                                                                                                                                                       | Returns the current AnyNet SMARTconnect™ software version in the following format: ver:\<ETM\_version>                                                                                                                                                                                                                                                                                                                       |
| ping                                                                                                                                                            | AnyNet SMARTconnect™ responds with the following SMS: pingreply                                                                                                                                                                                                                                                                                                                                                              |
| reboot                                                                                                                                                          | Reboots the Quectel BG95 module and AnyNet SMARTconnect™.                                                                                                                                                                                                                                                                                                                                                                    |
| revert                                                                                                                                                          | Returns the configuration file to the previously saved state, losing any unsaved changes.                                                                                                                                                                                                                                                                                                                                    |
| save                                                                                                                                                            | Saves any changes to the configuration file.                                                                                                                                                                                                                                                                                                                                                                                 |
| stats                                                                                                                                                           | Returns the device signal level, AnyNet SMARTconnect™ version and Quectel BG95 module firmware version in the following format: sig: \<signal\_level>dBm app: v\<ETM\_version> fw: \<Quectel BG95 module\_firmware\_version>                                                                                                                                                                                                 |
