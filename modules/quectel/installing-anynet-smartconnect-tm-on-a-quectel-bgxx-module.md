# Installing AnyNet SMARTconnect™ on a Quectel BGxx module

You can optionally install AnyNet SMARTconnect™ on a BG9x Quectel module to facilitate data transfer from your device to the cloud. For more information, see [About AnyNet SMARTconnect™](https://app.gitbook.com/s/TZG4LrCHVlGSXoDpMgo3/getting-started/about-anynet-smartconnect-tm).

### Before you begin

Ensure you have completed updating the modem firmware. For more information, see [Upgrading the Quectel module firmware](upgrading-the-quectel-module-firmware.md).

Contact your Account Manager to receive a dropbox link to AnyNet SMARTconnect™ files. Specify if you require Windows or Linux-based files.

If you are using AnyNet SMARTconnect™, you must install the Eseye-supplied ... firmware file in place of the Quectel-supplied ... file, where is the module variant, for example: BG96.

Using the supplied dropbox link, download and extract the following zip files:

* For Windows users:
  * Quectel EFS-Explorer for Windows – Quectel\_EFS\_Explorer\_V<_version_>\_Windows.zip.
  * Eseye-supplied ...zip firmware file.
  * AnyNetSMARTconnect\_<_version_>\_for\_\<module\_version>.zip, which contains AnyNet SMARTconnect™ application bin and ini files.
* For Linux users:
  * QExplorer for Linux and Android – QExplorer\_\_Linux\_Android\_V<_version_>.zip.
  * Eseye-supplied ...zip firmware file.
  * AnyNetSMARTconnect\_<_version_>\_for\_\<module\_version>.zip, which contains AnyNet SMARTconnect™ application bin and ini files.

## Installation overview

1. Create the five essential AnyNet files. For more information, see [Creating the essential AnyNet files](installing-anynet-smartconnect-tm-on-a-quectel-bgxx-module.md#creating-the-essential-anynet-files).
2. Add headers to the five AnyNet files. For more information, see Adding a header to AnyNet files.
3. Install the AnyNet files and AnyNet SMARTconnect™ on the Quectel module. For more information, see Uploading files to the Quectel module.

## Creating the essential AnyNet files

Each device must contain the following five files to connect with cloud services:

* anynet\_rootca\_store – the root CA certificate
* anynet\_pubcert\_store – the public certificate of the device
* anynet\_privkey\_store – the public private key of the device
* anynet\_thingname\_store – the Device ID, defined by the user during the device creation phase in the IoT Hub or AWS portal.
* anynet\_url\_store – the URL (hostname/endpoint) that is found on the IoT Hub and AWS portal.

To generate the essential AnyNet files

1.  Use instructions from your cloud services provider to generate a root ca, public certificate and private key for each device.

    AnyNet SMARTconnect™ supports both PEM and DER formats.
2. Rename these files as follows, with no extension:
   * anynet\_rootca\_store
   * anynet\_pubcert\_store
   * anynet\_privkey\_store
3. Use a text editor to create the following:
   *   anynet\_thingname\_store file – must only contain the Device ID.

       For example: MyDevice
   *   anynet\_url\_store file – must only contain the host endpoint.

       For example: my-hub.azure-devices.net or a2fguj321joea3-ats.iot.eu-west-1.amazonaws.com.
4. Next, you must add a header to each file.

### Adding a header to AnyNet files

To complete the file generation process, you must add a 6-byte binary header to the beginning of each file. The header consists of the length (2 bytes) followed by the CRC-32 (4 bytes).

For example, for anynet\_thingname\_store, the file appears as follows when opened in a text editor:

The same file appears as follows in a binary editor:

For information about calculating the checksum, see CRC-32 code example.

To add the header to an AnyNet file using the supplied Windows (PowerShell) script:

1. If you are using Windows, select here to download the windows\_header\_gen.ps1 script.
2.  Using Windows Powershell, run the script:

    ```
    .\windows_header_gen.ps1 <anynetfile_path>
    ```

    where anynetfile\_path is the AnyNet file path and filename.

    For example:

    ```
    .\windows_header_gen.sh .\anynetfiles\anynet_rootca_store
    ```

To add the header using the supplied Linux script:

1. If you are using Linux, select here to download the linux\_header\_gen.sh script.
2.  Using a Linux terminal, run the script:

    ```
    ./linux_header_gen.sh <anynetfile_path>
    ```

    where anynetfile\_path is the AnyNet file path and filename.

    For example:

    ```
    ./linux_header_gen.sh anynetfiles/anynet_rootca_store
    ```

## Uploading files to the Quectel module

Use Windows to install AnyNet SMARTconnect™ files on the Quectel module

To copy AnyNet SMARTconnect™ files onto the Quectel module:

1.  Ensure you have installed the required drivers and files for Windows.

    For more information, see [Upgrading the Quectel module firmware](upgrading-the-quectel-module-firmware.md).
2. In the extracted AnyNetSMARTconnect\_<_version_>\_for\_\<module\_version> folder, locate:
   * EseyeTelemetryModule.bin
   * oem\_app\_path.ini
3. Also locate the five AnyNet files you created.
4. Using a separate File Explorer, in the extracted Quectel\_EFS\_Explorer\_V<_version_>\_Windows folder, locate and run QEFS\_Explorer.exe to launch the application.
5. In QEFS Explorer, on the left hand side, select .
6. If the Please Select DM Port dialog box appears, select File > Device > Quectel USB DM Port to set the DM Port to the connected Quectel module, then select .
7. Double-click the datatx folder to expand it.
8.  Drag and drop the following files into the QEFS Explorer datatx folder:

    * EseyeTelemetryModule.bin
    * oem\_app\_path.ini
    * anynet\_rootca\_store
    * anynet\_pubcert\_store
    * anynet\_privkey\_store
    * anynet\_thingname\_store
    * anynet\_url\_store

    A dialog box appears for each file you transfer.
9. Select OK on each dialog box to transfer the files onto the connected Quectel module.
10. Reboot the Quectel module to load and start AnyNet SMARTconnect™ application.

Use Linux to install AnyNet SMARTconnect™ files on the Quectel module

To copy ETM application files into /datatx/ on the Quectel module:

1. Navigate to the extracted QExplorer\_\_Linux\_Android\_V<_version_> folder.
2.  Run:

    ```
    sudo make
    ```

    This command compiles QExplorer. If it is successful, you will see the QExplorer file.
3.  Run:

    ```
    sudo ./QExplorer -f <_filename_>
    ```

    where `<_filename_>` is the path to the following files:

    * EseyeTelemetryModule.bin
    * oem\_app\_path.ini
    * anynet\_rootca\_store
    * anynet\_pubcert\_store
    * anynet\_privkey\_store
    * anynet\_thingname\_store
    * anynet\_url\_store

These commands send AnyNet SMARTconnect™ files to the connected Quectel module.

4. Reboot the Quectel module.
5. Use a [terminal emulator](connecting-to-the-quectel-module-using-a-terminal-emulator.md) such as PuTTY to connect to the relevant USB interface, for example: `ttyUSB2`.
6.  Send:

    ```
    AT+ETMINFO="version"
    ```

    If the connection is valid, AnyNet SMARTconnect™ version is returned. This should match the version you installed.

## Where to next?

* [Connecting to the cloud](connecting-to-the-cloud.md)
* [Management AT commands](https://app.gitbook.com/s/TZG4LrCHVlGSXoDpMgo3/at-command-reference/management-at-commands)
* +ETM Unsolicited Response Codes (URCs)
* [General AT commands](https://app.gitbook.com/s/TZG4LrCHVlGSXoDpMgo3/at-command-reference/general-at-commands)
* [Updating AnyNet SMARTconnect™ software and host module firmware](https://app.gitbook.com/s/TZG4LrCHVlGSXoDpMgo3/updates/updating-anynet-smartconnect-tm-software-and-host-module-firmware)
* 8618 Eseye-enabled Quectel BG96 module Developer Guide (PDF)
