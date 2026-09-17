---
description: Download and restore configuration archives.
---

# File Management

Use File Management to create a configuration backup, restore a saved configuration, or install an approved software package.

#### Configuration backup

Open **Diagnostics & Maintenance > File Management > Configuration backup**, then select **Backup**.

<figure><img src="../../.gitbook/assets/Screenshot 2026-08-14 at 16.58.50.png" alt=""><figcaption></figcaption></figure>



The browser downloads the current running configuration as a `.tar.gz` file. Depending on browser security settings, you may be asked to enter the router administrator username and password before the download begins.

<figure><img src="../../.gitbook/assets/Screenshot 2026-08-14 at 16.59.01.png" alt=""><figcaption></figcaption></figure>



Store the backup securely. Label it with the router serial number, site, date, and software version so that operators can identify the correct file later. Configuration backups can contain network details and other sensitive settings.

#### Configuration upload

Open **Diagnostics & Maintenance > File Management > Configuration upload** to restore a compatible Hera 604 configuration archive.

<figure><img src="../../.gitbook/assets/Screenshot 2026-08-14 at 16.59.07.png" alt=""><figcaption></figcaption></figure>

To upload a configuration:

1. Confirm that the `.tar.gz` backup belongs to the correct Hera 604 and is compatible with its software version.
2. Record the current LAN address and active WAN connection.
3. Select **Upload**.
4. Enter the administrator username and password if the browser requests authentication.
5. Select **Choose file** and select the configuration archive.
6. Select **OK** to upload and apply the configuration, or **Cancel** to stop.
7. Reboot when prompted, either immediately or at the approved maintenance time.
8. Reconnect using the address contained in the restored configuration and verify the router status.

<figure><img src="../../.gitbook/assets/Screenshot 2026-08-14 at 16.59.17.png" alt=""><figcaption></figcaption></figure>



> **Warning:** Restoring a configuration can change LAN, WAN, mobile, wireless, routing, firewall, and administrator settings. Uploading the wrong archive may make the router unreachable.

#### Software upload

Open **Diagnostics & Maintenance > File Management > Software upload** to install an approved Hera 604 software package.

<figure><img src="../../.gitbook/assets/Screenshot 2026-08-14 at 16.59.25.png" alt=""><figcaption></figcaption></figure>

The page provides **Upload – keeping existing configuration**. This installs the selected software while retaining the router's current configuration; configuration settings contained in the software file do not overwrite the router's existing settings.

To upload software:

1. Confirm the package is supplied or approved for the Hera 604 model and current upgrade path.
2. Download a current configuration backup.
3. Connect the router to stable power. Do not begin when power may be interrupted.
4. Select **Upload – keeping existing configuration**.
5. Select **Choose file** and select the approved software archive.
6. Select **OK** to begin, or **Cancel** to stop before the upload starts.
7. Do not close the browser, remove power, disconnect the management cable, or restart the router during installation.
8. Allow the router to reboot when the installation completes.
9. Reconnect and confirm the software version, WAN connectivity, and configured services.

<figure><img src="../../.gitbook/assets/Screenshot 2026-08-14 at 16.59.30.png" alt=""><figcaption></figcaption></figure>



###
