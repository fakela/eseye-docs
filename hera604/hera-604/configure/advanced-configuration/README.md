---
description: Safely edit UCI configuration files for general and WAN interface settings.
---

# Advanced configuration

Use **Advanced Settings** to view and edit the configuration files used by the Hera 604.

This area is intended for experienced operators who understand the router's UCI configuration. An incorrect entry can interrupt network access, prevent an interface from starting, or make the router unavailable.

> **Important:** Back up the working configuration before editing a file. Make changes during an approved maintenance window and confirm that you have local access to the router if the network configuration fails.

<figure><img src="../../.gitbook/assets/Screenshot 2026-08-14 at 16.57.58.png" alt=""><figcaption></figcaption></figure>

### File Editor

The **File Editor** provides access to two groups of configuration files:

* **General configuration** — files in `/etc/config`.
* **WAN interface** — files in `/etc/wanif`.

The page displays a **Contents** list and a **File** pane. Select a file in the contents list to view it. The file remains read only until you select **Edit**.

### General configuration

Open **Advanced Settings > File Editor > General configuration** to view the router's general UCI configuration files.

<figure><img src="../../.gitbook/assets/Screenshot 2026-08-14 at 16.58.03.png" alt=""><figcaption></figcaption></figure>



These files control core router services and interfaces. Only edit a file when you have an approved configuration change or instructions from Eseye Support.

To edit a general configuration file:

1. Back up the current router configuration from **Diagnostics & Maintenance > File Management > Configuration backup**.
2. Open **Advanced Settings > File Editor > General configuration**.
3. Select the required file from **Contents**.
4. Review the complete file before making a change.
5. Select **Edit**.
6. Make the smallest required change.
7. Check the syntax, option names, quotation marks, and section structure.
8. Select **Save** to save that file, or **Save all** if approved changes were made to several files.
9. Confirm that the affected service or interface still operates correctly.

Select **Reset** before saving to discard the unsaved edits displayed in the editor. Do not assume that **Reset** restores a previously working router configuration after changes have already been saved; use a known-good configuration backup when recovery is required.

### WAN interface

Open **Advanced Settings > File Editor > WAN interface** to view configuration files associated with the router's WAN interfaces.

<figure><img src="../../.gitbook/assets/Screenshot 2026-08-14 at 16.58.08.png" alt=""><figcaption></figcaption></figure>

WAN interface files can affect Ethernet WAN, mobile connectivity, routing, failover, and remote access. A syntax or addressing error may disconnect the router from the network.

To edit a WAN interface file:

1. Record the active WAN interface and its current IP address.
2. Download a current configuration backup.
3. Open **Advanced Settings > File Editor > WAN interface**.
4. Select the required file from **Contents**.
5. Confirm that the file belongs to the interface being changed.
6. Select **Edit** and make the approved change.
7. Validate all interface names, addresses, routes, and referenced profiles.
8. Select **Save**.
9. Check that the interface reconnects and that the router remains reachable.

> **Remote access:** Do not change the interface carrying your current management session unless a second access path or an on-site recovery operator is available.

### File Editor controls

| Control  | Purpose                                                        |
| -------- | -------------------------------------------------------------- |
| Contents | Lists the files available in the selected configuration group. |
| File     | Displays the contents of the selected file.                    |
| Edit     | Makes the selected file editable.                              |
| Save     | Saves changes to the current file.                             |
| Save all | Saves approved changes made to multiple files.                 |
| Reset    | Discards edits that have not been saved.                       |

### After changing a configuration file

Confirm all of the following before closing the maintenance task:

* The router interface remains accessible.
* LAN, WAN, mobile, and Wi-Fi services affected by the change operate normally.
* The expected routes and firewall rules are present.
* The updated configuration survives any required service restart or router reboot.
* A new configuration backup has been downloaded and labelled with the router serial number and change date.

If the router behaves unexpectedly, stop making further edits and restore the approved backup or contact Eseye Support with the router's serial number, software version, firmware version, and details of the file changed.
