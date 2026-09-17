# Configuring an AnyNet APN on an Android device

Use one of the following methods to configure an Android device to work with an AnyNet APN:

* Manually add the APN to an Android device using the Access Point Name settings
* Replace the existing apns-conf.xml file with a file containing the correct APN settings

{% hint style="info" %}
For information about APNs, see [About Access Point Names (APNs)](https://eseye-v3.gitbook.io/eseye-docs/L25WdLp1CEZBZ0aOlPAR/connectivity/access-point-names).
{% endhint %}

## Manually adding the AnyNet APN to the device

{% hint style="info" %}
These instructions were tested on a Samsung Galaxy J3 with Android version 9. Instructions may vary by device and Android version.
{% endhint %}

To add the AnyNet APN to an Android device:

1. On the Android Settings menu, select Connections.
2. Select **Mobile networks**.
3. Ensure **Data roaming** is turned on.
4.  Select **Access Point Names**.

    A list of existing APNs is displayed.
5. Select **Add**.
6.  Enter the following information into the APN fields:

    | Field               | Value                                                                                                                                                                                        |
    | ------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
    | Name                | AnyNet APN                                                                                                                                                                                   |
    | APN                 | <p><em>&#x3C;APNname></em><br><br>where <em>&#x3C;APNname></em> is the APN specified in your contract</p>                                                                                    |
    | Username            | <p>Android - <em>&#x3C;username></em><br><br>where <em>&#x3C;username></em> is the name of your choice</p>                                                                                   |
    | Password            | <p>pass<br><br></p><div data-gb-custom-block data-tag="hint" data-style="info" class="hint hint-info"><p><br>Additional authentication is applied when you connect to the APN.<br></p></div> |
    | Authentication type | PAP or CHAP                                                                                                                                                                                  |
7.  Leave the default values for all other fields.

    <div data-gb-custom-block data-tag="hint" data-style="info" class="hint hint-info"><p>Most fields have a Not Set value. The MCC and MNC fields are fetched from the network profile for the IMSI that the device is currently using.</p></div>
8. Select the menu in the top-right corner.
9.  Select **Save**.

    The AnyNet APN appears in the Access Point Names list.

    <div data-gb-custom-block data-tag="hint" data-style="info" class="hint hint-info"><p>This process may take time.</p></div>

## Replacing the apns-conf.xml file

The **apns-conf.xml** file contains the settings for the AnyNet APN and the Mobile Country Code (MCC) and Mobile Network Code (MNC) for each network.

{% hint style="warning" %}
This option requires root access to the Android device. For more information, see [Rooting (Android)](https://en.wikipedia.org/wiki/Rooting_\(Android\)).
{% endhint %}

{% hint style="info" %}
These instructions are for Android Debug Bridge (ADB). You can use other apps to transfer the file to your device.
{% endhint %}

1.  Select the following link to access the AnyNet apns-conf.xml file:

    apns-conf.xml

    <div data-gb-custom-block data-tag="hint" data-style="info" class="hint hint-info"><p>Depending on your settings, your browser may download the file automatically, prompt you for a target destination for the file, or open the file in a new browser window. If the file opens in a browser window, save it to a local folder.</p></div>
2.  Copy the apns-conf.xml file to the device:

    ```bash
    adb -s <device> push <download-path>apns-conf.xml /system/etc/apns-conf.xml
    ```

    where `-s` indicates a device serial number is specified, `<device>` is the serial number of the device you want to update, and `<download-path>` is the path to your local copy of the configuration file.

    <div data-gb-custom-block data-tag="hint" data-style="info" class="hint hint-info"><p>For more information about the push command, see <a href="http://adbshell.com/commands/adb-push">ADB push command</a>.</p></div>

* For information about APNs, see [About Access Point Names (APNs)](./).
