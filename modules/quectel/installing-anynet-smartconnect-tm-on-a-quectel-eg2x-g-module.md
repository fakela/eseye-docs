# Installing AnyNet SMARTconnect™ on a Quectel EG2x-G module

You can optionally install AnyNet SMARTconnect™ on a Quectel EG2x-G module to facilitate data transfer from your device to the cloud. For more information, see [About AnyNet SMARTconnect™](https://app.gitbook.com/s/TZG4LrCHVlGSXoDpMgo3/getting-started/about-anynet-smartconnect-tm).

### Before you begin

Ensure you have completed updating the modem firmware, which includes installing the required drivers and files for Windows. For more information, see [Upgrading the Quectel module firmware](upgrading-the-quectel-module-firmware.md).

Contact your Account Manager to receive a dropbox link to AnyNet SMARTconnect™ files. Specify if you require Windows or Linux-based files.

If you are using AnyNet SMARTconnect™, you must install the Eseye-supplied ... firmware file in place of the Quectel-supplied ... file, where is the module variant, for example: EG21G....

Using the supplied dropbox link, download and extract the following zip files:

* For Windows users:
  * Quectel Windows adb driver – Quectel\_ADB\_Drivers\_V.zip
  * Eseye-supplied Android-specific SDK platform tools (adb and fastboot) – platform-tools\_-windows.zip
* For Linux users:
  * Eseye-supplied Android-specific SDK platform tools (adb and fastboot) – platform-tools\_-linux.zip
*   Quectel firmware:

    Eseye-supplied ...zip firmware file – for example, EG21...zip.
* AnyNet SMARTconnect™, which includes:
  * AnyNet SMARTconnect™ files
  * A kernel image – EG2...img
  * For some modules, a rootfs image – EG2...ubi

We recommend you use a [terminal emulator](connecting-to-the-quectel-module-using-a-terminal-emulator.md) (such as PuTTY or Tera Term) to connect to the relevant USB interface. Use the following serial settings: `115200 8-N-1`.

## Installation overview

These instructions presume that you have set up your computer and development board containing the Quectel EG2x-G module to upgrade the firmware, and that the board remains connected to the computer via USB and a separate serial port for developer purposes.

The USB port is for loading the firmware onto the Quectel EG2x-G module. The serial port is for sending AT commands to the module.

1. Choose the Windows or Linux installation.
2. For Windows installation only, install the adb driver on your computer.
3. Use a terminal emulator to enable the adb endpoint on the Quectel EG2x-G module.
4. Use adb and fastboot to update the Quectel EG2x-G module kernel and rootfs so that they are AnyNet SMARTconnect™ compatible.
5. Use adb to install AnyNet SMARTconnect™ on the Quectel EG2x-G module.

After installation, you can configure AnyNet SMARTconnect™, as well as change the Quectel EG2x-G module root password so that you can log into the debug UART console.

## Installing AnyNet SMARTconnect™ using Windows

### Installing the Windows adb driver

To install the Windows adb driver on your computer:

1. In the extracted Quectel\_ADB\_Drivers\_V folder, locate and run **Adb\_Installer.exe** to start the installation wizard.
2.  Select Install Adb Driver.

    The adb driver installs.

### Installing and using Windows SDK platform tools

Eseye has tested the module firmware and AnyNet SMARTconnect™ using a particular version of the Windows SDK platform tools, which we supply. We recommend you use the supplied version to ensure compatibility with AnyNet SMARTconnect™.

### Enabling adb on the Quectel EG2x-G module

Use a [terminal emulator](connecting-to-the-quectel-module-using-a-terminal-emulator.md) connected to the USB AT endpoint. Serial settings: `115200 8-N-1`.

To enable adb on the Quectel EG2x-G module:

1.  Using a terminal emulator, send:

    ```
    AT+QCFG="usbcfg"
    ```
2.  For an EG21 Quectel module, if the module returns:

    ```
    +QCFG: "usbcfg",0x2C7C,0x121,1,1,1,1,1,0,0
    OK
    ```

    where the highlighted value is 0, then send the following to enable the adb endpoint:

    ```
    AT+QCFG="usbcfg",0x2C7C,0x121,1,1,1,1,1,1,0
    OK
    ```

    If the value is already 1, make no change.
3.  For an EG25 Quectel module, if the module returns:

    ```
    +QCFG: "usbcfg",0x2C7C,0x125,1,1,1,1,1,0,0
    OK
    ```

    where the highlighted value is 0, then send the following to enable the adb endpoint:

    ```
    AT+QCFG="usbcfg",0x2C7C,0x125,1,1,1,1,1,1,0
    OK
    ```

    If the value is already 1, make no change.

### Uploading AnyNet SMARTconnect™ to the Quectel EG2x-G module

To load AnyNet SMARTconnect™ files onto the Quectel module:

1.  In the extracted platform-tools\_-windows folder, navigate to the adb application, then use the right-click MS Explorer menu to Open in Terminal.

    A Windows Powershell terminal opens with the directory path to the Windows platform tools folder.
2.  Place the Quectel EG2x-G module into bootloader mode. Enter the command:

    ```
    .\adb reboot bootloader
    ```

    The daemon starts successfully.
3.  Update the Quectel EG2x-G module kernel image. Enter the command:

    ```
    .\fastboot flash boot \EG2-mdm9607-boot.img
    ```

    where is the path to your local copy of the kernel image, and is the EG2x variant, for example EG21-mdm9607-boot.img.
4.  If Eseye supplied you with a rootfs\_image folder alongside the kernel\_image folder, update the Quectel EG2x-G module root file system.

    This step does not apply to all modules.

    Enter the command:

    ```
    .\fastboot flash system \EG2-mdm9607-sysfs.ubi
    ```

    where is the path to your local copy of the rootfs image, and is the EG2x variant, for example EG21-mdm9607-sysfs.ubi.
5.  Reboot the Quectel EG2x-G module to load and start the AnyNet SMARTconnect™ application. . Enter the command:

    ```
    .\fastboot reboot
    ```
6.  Load the AnyNet SMARTconnect™ application. Enter the following four commands:

    ```
    .\adb push \client_console /usrdata
    .\adb push \etm /usrdata
    .\adb push \etmrun /usrdata
    .\adb push \eseye_telemetry_module /etc/init.d/
    ```

    where is the path to your local copy of the AnyNet SMARTconnect™ files.
7.  Set the access permissions to AnyNet SMARTconnect™. Enter the following four commands:

    ```
    .\adb shell chmod +x /usrdata/client_console
    .\adb shell chmod +x /usrdata/etm
    .\adb shell chmod +x /usrdata/etmrun
    .\adb shell chmod +x /etc/init.d/eseye_telemetry_module
    ```
8.  Ensure that AnyNet SMARTconnect™ is running. Enter the command:

    ```
    .\adb shell /usrdata/etmrun start
    ```

    You should see the following response:

    ```
    Starting Eseye-Telemetry-module: done
    ```

    For more information, see Running AnyNet SMARTconnect™ (Windows).
9.  Use a terminal emulator connected to the physical AT UART port on your developer board to send the following:

    ```
    AT+ETMINFO=version
    ```

    The returned version should match the AnyNet SMARTconnect™ version you installed.

### Running AnyNet SMARTconnect™ (Windows)

When AnyNet SMARTconnect™ runs, you can use the client\_console application to issue AT commands directly to the AnyNet SMARTconnect™ application. For more information, see [AT commands](https://app.gitbook.com/s/TZG4LrCHVlGSXoDpMgo3/at-command-reference/at-commands).

You can enable different trace levels for debug purposes to monitor AnyNet SMARTconnect™ operation. For more information, see [Using the AnyNet SMARTconnect™ configuration file](https://app.gitbook.com/s/TZG4LrCHVlGSXoDpMgo3/getting-started/using-the-anynet-smartconnect-tm-configuration-file).

Use the following commands to start, stop, and persist the AnyNet SMARTconnect™ application:

| Command                             | Description                                                              |
| ----------------------------------- | ------------------------------------------------------------------------ |
| .\adb shell /usrdata/etmrun start   | Starts the AnyNet SMARTconnect™ application running.                     |
| .\adb shell /usrdata/etmrun stop    | Terminates the AnyNet SMARTconnect™ application.                         |
| .\adb shell /usrdata/etmrun enable  | Persists the application to run after reboot (for Linux, this is rc5.d). |
| .\adb shell /usrdata/etmrun disable | Terminates the application at reboot.                                    |

## Installing AnyNet SMARTconnect™ using Linux

### Installing and using Linux SDK platform tools

Eseye has tested the module firmware and AnyNet SMARTconnect™ using a particular version of the Linux SDK platform tools, which we supply. We recommend you use the supplied version to ensure compatibility with AnyNet SMARTconnect™.

### Enabling adb on the Quectel EG2x-G module

Use a [terminal emulator](connecting-to-the-quectel-module-using-a-terminal-emulator.md) connected to the USB AT endpoint. Serial settings: `115200 8-N-1`.

To enable adb on the Quectel EG2x-G module:

1.  Using a terminal emulator, send:

    ```
    AT+QCFG="usbcfg"
    ```
2.  If the module returns:

    ```
    +QCFG: "usbcfg",0x2C7C,0x121,1,1,1,1,1,0,0
    OK
    ```

    where the highlighted value is 0, then send the following to enable the adb endpoint:

    ```
    AT+QCFG="usbcfg",0x2C7C,0x121,1,1,1,1,1,1,0
    OK
    ```

### Uploading AnyNet SMARTconnect™ to the Quectel EG2x-G module

To load AnyNet SMARTconnect™ files onto the Quectel module:

1. In the extracted platform-tools\_-linux folder, navigate to the adb application, then open a terminal shell from this location.
2.  Place the Quectel EG2x-G module into bootloader mode. Enter the command:

    ```
    sudo ./adb reboot bootloader
    ```

    The daemon starts successfully.
3.  Update the Quectel EG2x-G module kernel image. Enter the command:

    ```
    sudo ./fastboot flash boot /EG21-mdm9607-boot.img
    ```

    where is the path to your local copy of the kernel image.
4.  If Eseye supplied you with a rootfs\_image folder alongside the kernel\_image folder, update the Quectel EG2x-G module root file system.

    This step does not apply to all modules.

    Enter the command:

    ```
    sudo ./fastboot flash system /EG21-mdm9607-sysfs.ubi
    ```

    where is the path to your local copy of the rootfs image.
5.  Reboot the Quectel EG2x-G module to load and start the AnyNet SMARTconnect™ application. Enter the command:

    ```
    sudo ./fastboot reboot
    ```
6.  Load the AnyNet SMARTconnect™ application. Enter the following four commands:

    ```
    sudo ./adb push /etm /usrdata
    sudo ./adb push /client_console /usrdata
    sudo ./adb push /etmrun /usrdata
    sudo ./adb push /eseye_telemetry_module /etc/init.d/
    ```

    where is the path to your local copy of the AnyNet SMARTconnect™ files.
7.  Ensure that AnyNet SMARTconnect™ is running. Enter the command:

    ```
    sudo ./adb shell /usrdata/etmrun start
    ```

    You should see the following response:

    ```
    Starting Eseye-Telemetry-module: done
    ```

    For more information, see Running AnyNet SMARTconnect™ (Linux).
8.  Use a terminal emulator connected to the physical UART port on your developer board to send the following:

    ```
    AT+ETMINFO=version
    ```

    The returned version should match the AnyNet SMARTconnect™ version you installed.

### Running AnyNet SMARTconnect™ (Linux)

When AnyNet SMARTconnect™ runs, you can use the client\_console application to issue AT commands directly to the AnyNet SMARTconnect™ application. For more information, see [AT commands](https://app.gitbook.com/s/TZG4LrCHVlGSXoDpMgo3/at-command-reference/at-commands).

You can enable different trace levels for debug purposes to monitor AnyNet SMARTconnect™ operation. For more information, see [Using the AnyNet SMARTconnect™ configuration file](https://app.gitbook.com/s/TZG4LrCHVlGSXoDpMgo3/getting-started/using-the-anynet-smartconnect-tm-configuration-file).

Use the following commands to start, stop, and persist the AnyNet SMARTconnect™ application:

| Command                                  | Description                                                              |
| ---------------------------------------- | ------------------------------------------------------------------------ |
| sudo ./adb shell /usrdata/etmrun start   | Starts the AnyNet SMARTconnect™ application running.                     |
| sudo ./adb shell /usrdata/etmrun stop    | Terminates the AnyNet SMARTconnect™ application.                         |
| sudo ./adb shell /usrdata/etmrun enable  | Persists the application to run after reboot (for Linux, this is rc5.d). |
| sudo ./adb shell /usrdata/etmrun disable | Terminates the application at reboot.                                    |

## Where to next?

* [Connecting to the cloud](connecting-to-the-cloud.md)
* [Management AT commands](https://app.gitbook.com/s/TZG4LrCHVlGSXoDpMgo3/at-command-reference/management-at-commands)
* +ETM Unsolicited Response Codes (URCs)
* [General AT commands](https://app.gitbook.com/s/TZG4LrCHVlGSXoDpMgo3/at-command-reference/general-at-commands)
* [Updating AnyNet SMARTconnect™ software and host module firmware](https://app.gitbook.com/s/TZG4LrCHVlGSXoDpMgo3/updates/updating-anynet-smartconnect-tm-software-and-host-module-firmware)
* 8618 Eseye-enabled Quectel BG96 module Developer Guide (PDF)
