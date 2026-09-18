# Updating AnyNet SMARTconnect™ software and host module firmware

### Before you begin

* Using a terminal emulator, ensure AnyNet SMARTconnect™ is connected to the network, with an ETMSTATE of 7. For more information, see [ETMSTATE – check current state](../at-command-reference/management-at-commands/etmstate-check-current-state.md).
* Use `AT+ETMINFO="imei"` to find and record the Quectel BG95 module IMEI. For more information, see [ETMINFO – displays AnyNet SMARTconnect™ and device information](../at-command-reference/management-at-commands/etminfo-displays-anynet-smartconnect-tm-and-device-information.md).
* Eseye supplies the following files for updating AnyNet SMARTconnect™:
  * Configuration file: `eseyeconfig.ini`.
  * Quectel BG95 module firmware update file: `BG95M3LARxxAxx_xx.xxx.xx.xxx-BG95M3LARxxAxx_xx.xxx.xx.xxx.bin`.
  * AnyNet SMARTconnect™ application: `etm_application.ota`.

{% hint style="info" %}
Quectel modem firmware update packages are Delta FOTA (DFOTA) type. Each package updates one specific firmware version to another.
{% endhint %}

To request these files, speak to your Account Manager.

{% hint style="info" %}
You may create your own configuration file for updating the Quectel BG95 module. For information about the configuration file, see [Using the AnyNet SMARTconnect™ configuration file](../getting-started/using-the-anynet-smartconnect-tm-configuration-file.md).
{% endhint %}

* If required, store the update files on a server and note the URLs to each file.
* If required, store the host firmware update on a server and note the URL to the file.

### About AnyNet SMARTconnect™ update

Each AnyNet SMARTconnect™ software version is developed for a specific Quectel BG95 module firmware version. When an AnyNet SMARTconnect™ update occurs, the older version remains stored in the ../datatx folder.

At each boot, AnyNet SMARTconnect™ checks that the currently running AnyNet SMARTconnect™ version is correct for the current Quectel BG95 module firmware version. If it is not correct, the older version is used instead. If no older version is found, AnyNet SMARTconnect™ uses the available version.

### Updating the AnyNet SMARTconnect™ application and Quectel BG95 module firmware

For information about the AT commands used in this procedure, see [Management AT commands](../at-command-reference/management-at-commands/).

<details open>

<summary>To update AnyNet SMARTconnect™ application and Quectel BG95 module firmware at the same time</summary>

1.  Set the URL from which to download the AnyNet SMARTconnect™ application. Send:

    ```
    AT+ETMCFG="application","updateurl","<http(s)://ETMappURL>"
    OK
    ```

    `<http(s)://ETMappURL>` is the absolute URL for downloading `etm_application.ota`.
2.  Set the URL from which to download the Quectel BG95 module update package. Send:

    ```
    AT+ETMCFG="application","fotaurl",""
    OK
    ```

    The URL is the absolute URL for downloading the `.bin` file.
3.  Save the configuration changes. Send:

    ```
    AT+ETMCFG="save"
    OK
    ```
4.  Trigger the AnyNet SMARTconnect™ application and Quectel BG95 module firmware download and update. Send:

    ```
    AT+ETMFWCHECK
    ```

    AnyNet SMARTconnect™ downloads the new application, then performs a CRC32 check to ensure the file is valid and the new AnyNet SMARTconnect™ version is different from the existing AnyNet SMARTconnect™ version.

    <div data-gb-custom-block data-tag="hint" data-style="info" class="hint hint-info"><p>If the file is invalid, or the version matches a stored version, no update occurs.</p></div>

    If the download completes and versions differ, AnyNet SMARTconnect™ updates `datatx/oem_app_path.ini`.

    The Quectel BG95 module firmware then downloads.

    The following response occurs:

    ```
    +ETMFWCHECK: complete
    ```

    After the download completes, the Quectel BG95 module firmware is updated.

    If the update succeeds, the Quectel BG95 module reboots automatically.

    If only AnyNet SMARTconnect™ updates, the modem reboots according to `[operation] update_autoreboot`:

    * `0` – The system requires a manual reboot.
    * `1` – The system reboots automatically.

</details>

For information about how AnyNet SMARTconnect™ application is stored and used in the datatx folder, see About AnyNet SMARTconnect™.

### Updating the AnyNet SMARTconnect™ application only

For information about the AT commands used in this procedure, see [Management AT commands](../at-command-reference/management-at-commands/).

<details open>

<summary>To update AnyNet SMARTconnect™ application</summary>

1.  Clear the current URL configuration for the Quectel BG95 module firmware update. Send:

    ```
    AT+ETMCFG="remove","application","fotaurl"
    OK
    ```
2.  Set the URL from which to download the AnyNet SMARTconnect™ application. Send:

    ```
    AT+ETMCFG="application","updateurl","<http(s)://ETMappURL>"
    OK
    ```

    `<http(s)://ETMappURL>` is the absolute URL for downloading `etm_application.ota`.
3.  Save the configuration changes. Send:

    ```
    AT+ETMCFG="save"
    OK
    ```
4.  Trigger the AnyNet SMARTconnect™ application download and update. Send:

    ```
    AT+ETMFWCHECK
    ```

    AnyNet SMARTconnect™ downloads the new application, then performs a CRC32 check to ensure the file is valid and the new AnyNet SMARTconnect™ version is different from the existing AnyNet SMARTconnect™ version.

    <div data-gb-custom-block data-tag="hint" data-style="info" class="hint hint-info"><p>If the file is invalid, or the version matches a stored version, no update occurs.</p></div>

    If the download completes and versions differ, AnyNet SMARTconnect™ updates `datatx/oem_app_path.ini`.

    The following response occurs:

    ```
    +ETMFWCHECK: complete
    ```

    If `[operation] update_autoreboot` is `1`, AnyNet SMARTconnect™ sends the `+ETM: REBOOTING` URC and reboots. Otherwise, it sends the `+ETM: REBOOT REQUIRED` URC.
5.  If required, reboot the system. Send:

    ```
    AT+ETMRESET
    ```

</details>

### Downloading the device host firmware

For information about the AT commands used in this procedure, see [Management AT commands](../at-command-reference/management-at-commands/).

<details open>

<summary>To download device host firmware</summary>

1.  Set the URL from which to download the device host firmware. Send:

    ```
    AT+ETMCFG="host","updateurl","<http(s)://HostFirmwareURL>"
    OK
    ```

    `<http(s)://HostFirmwareURL>` is the absolute URL for downloading the host firmware.
2.  Save the configuration changes. Send:

    ```
    AT+ETMCFG="save"
    OK
    ```
3.  Trigger the host firmware download. Send:

    ```
    AT+ETMHFWGET
    ```

    The response is either:

    * `+ETMHFWGET: available` – AnyNet SMARTconnect™ downloaded the file.
    * `+ETMHFWGET: none` – The download failed. Check that the URL is correct and accessible, then run `AT+ETMHFWGET` again.

To read the file, use `AT+ETMHFWREAD`. For more information, see [ETMHFWREAD – reads a section of the new host firmware image](../at-command-reference/management-at-commands/etmhfwread-reads-a-section-of-the-new-host-firmware-image.md).

To delete the downloaded file from the `datatx` folder, use `AT+ETMHFWCONF`. For more information, see [ETMHFWCONF – confirms the new host firmware is applied](../at-command-reference/management-at-commands/etmhfwconf-confirms-the-new-host-firmware-is-applied.md).

</details>

### Updating the AnyNet SMARTconnect™ configuration file

For information about the AT commands used in this procedure, see [Management AT commands](../at-command-reference/management-at-commands/).

<details open>

<summary>To update AnyNet SMARTconnect™ configuration file</summary>

1.  Set the URL from which to download the AnyNet SMARTconnect™ configuration file. Send:

    ```
    AT+ETMCFG="config","updateurl","<http(s)://eseyeconfigURL>"
    OK
    ```

    `<http(s)://eseyeconfigURL>` is the absolute URL for downloading `eseyeconfig.ini`.
2.  Save the configuration changes. Send:

    ```
    AT+ETMCFG="save"
    OK
    ```
3.  Trigger the configuration file download and update. Send:

    ```
    AT+ETMCFGCHECK
    +ETMCFGCHECK: complete
    ```

    The newly updated `[operation] update_autoreboot` setting determines whether AnyNet SMARTconnect™ reboots automatically:

    * `0` – The system requires a manual reboot.
    * `1` – The system reboots automatically.

    If the download fails, check that the URL is correct and accessible. Then run `AT+ETMCFGCHECK` again.
4.  If required, reboot the system. Send:

    ```
    AT+ETMRESET
    ```

</details>

### Using the MQTT broker to update files

AnyNet SMARTconnect™ can accept some commands sent by the MQTT broker on the topic \[mqtt] mqttsettingstopic/\[mqtt] topicsuffix.

{% hint style="warning" %}
Send all commands in plain text format (ASCII).
{% endhint %}

<details open>

<summary>AnyNet SMARTconnect™ accepts the following commands</summary>

| Command                                                                                                         | Function                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| --------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `config,<section>,<name>,<value>`                                                                               | Sets the specified configuration file parameter to the specified value.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| `default`                                                                                                       | Sets the configuration file to default values.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| <p><code>fwupdate &#x3C;IMEI></code><br><br>Where <code>&#x3C;IMEI></code> is the Quectel BG95 module IMEI.</p> | <p>Triggers the specified update when the following parameters are set:<br><br>• <code>[application] updateurl</code> – Triggers only the AnyNet SMARTconnect™ application update.<br><br>• <code>[application] fotaurl</code> – Triggers both the AnyNet SMARTconnect™ application and Quectel BG95 module firmware updates. <code>[application] updateurl</code> must also be set.<br><br>If the update includes Quectel BG95 module firmware, the module reboots automatically.<br><br>If only the application updates, <code>[operation] update_autoreboot</code> determines the reboot behavior:<br><br>• <code>0</code> – The system requires a manual reboot.<br>• <code>1</code> – The system reboots automatically.<br><br>For more information, see <a href="updating-anynet-smartconnect-tm-software-and-host-module-firmware.md#about-anynet-smartconnect-update">About AnyNet SMARTconnect™ update</a>.</p> |
| `reboot`                                                                                                        | Reboots the Quectel BG95 module and AnyNet SMARTconnect™.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| `revert`                                                                                                        | Returns the configuration file to the previously saved state. Unsaved changes are lost.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| `save`                                                                                                          | Saves changes to the configuration file.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |

</details>

### Using SMS to update files

AnyNet SMARTconnect™ can accept some commands sent via SMS.

{% hint style="info" %}
SMS is accepted only from numbers in the `[SMS] allowedlist` configuration file.
{% endhint %}

{% hint style="warning" %}
Send all commands in plain text format (ASCII).
{% endhint %}

<details open>

<summary>AnyNet SMARTconnect™ accepts the following commands in the SMS body</summary>

| Command                                                                                                                                                                                                                       | Function                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `config save`                                                                                                                                                                                                                 | Saves changes to the configuration file.                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `config,<section>,<name>,<value>`                                                                                                                                                                                             | Sets the specified configuration file parameter to the specified value.                                                                                                                                                                                                                                                                                                                                                                                                              |
| <p><code>download application &#x3C;http(s)://ETMappURL></code><br><br>Where <code>&#x3C;http(s)://ETMappURL></code> is the absolute URL for downloading <code>etm_application.ota</code>.</p>                                | <p>Triggers an AnyNet SMARTconnect™ application update.<br><br>If the update succeeds, <code>[operation] update_autoreboot</code> determines the reboot behavior:<br><br>• <code>0</code> – The system requires a manual reboot.<br>• <code>1</code> – The system reboots automatically.<br><br>For more information, see <a href="updating-anynet-smartconnect-tm-software-and-host-module-firmware.md#about-anynet-smartconnect-update">About AnyNet SMARTconnect™ update</a>.</p> |
| <p><code>download combo &#x3C;http(s)://ETMappURL>,&#x3C;http(s)://QuectelDFOTAfirmwareURL></code><br><br>Where <code>&#x3C;http(s)://QuectelDFOTAfirmwareURL></code> is the absolute URL for the <code>.bin</code> file.</p> | <p>Triggers AnyNet SMARTconnect™ application and Quectel BG95 module firmware updates.<br><br>If the update succeeds, the Quectel BG95 module reboots automatically.<br><br>If only the application updates, <code>[operation] update_autoreboot</code> determines the reboot behavior:<br><br>• <code>0</code> – The system requires a manual reboot.<br>• <code>1</code> – The system reboots automatically.</p>                                                                   |
| <p><code>download config &#x3C;http(s)://eseyeconfigURL></code><br><br>Where <code>&#x3C;http(s)://eseyeconfigURL></code> is the absolute URL for downloading <code>eseyeconfig.ini</code>.</p>                               | Triggers an AnyNet SMARTconnect™ configuration file update.                                                                                                                                                                                                                                                                                                                                                                                                                          |
| <p><code>download host &#x3C;http(s)://HostFirmwareURL></code><br><br>Where <code>&#x3C;http(s)://HostFirmwareURL></code> is the absolute URL for downloading the host firmware.</p>                                          | Triggers the device host firmware download.                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| `get cfg <section> <name>`                                                                                                                                                                                                    | Returns the specified configuration file parameter as `<section>:<name>=<value>`.                                                                                                                                                                                                                                                                                                                                                                                                    |
| `get swver`                                                                                                                                                                                                                   | Returns the current AnyNet SMARTconnect™ software version as `ver:<ETM_version>`.                                                                                                                                                                                                                                                                                                                                                                                                    |
| `ping`                                                                                                                                                                                                                        | Returns the SMS response `pingreply`.                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| `reboot`                                                                                                                                                                                                                      | Reboots the Quectel BG95 module and AnyNet SMARTconnect™.                                                                                                                                                                                                                                                                                                                                                                                                                            |
| `revert`                                                                                                                                                                                                                      | Returns the configuration file to the previously saved state. Unsaved changes are lost.                                                                                                                                                                                                                                                                                                                                                                                              |
| `save`                                                                                                                                                                                                                        | Saves changes to the configuration file.                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `stats`                                                                                                                                                                                                                       | <p>Returns signal level, AnyNet SMARTconnect™ version, and Quectel BG95 module firmware version:<br><br><code>sig: &#x3C;signal_level>dBm</code><br><code>app: v&#x3C;ETM_version></code><br><code>fw: &#x3C;Quectel BG95 module_firmware_version></code></p>                                                                                                                                                                                                                        |

</details>
