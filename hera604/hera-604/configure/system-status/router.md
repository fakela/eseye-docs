---
description: View router identification, activity, and site information.
---

# Router

The **Router** page provides the following information:

* Router model and serial number
* Installed software and firmware versions
* Last restart time, uptime and processing load
* Assigned site name and location

> The displayed values do not update automatically. Select the refresh icon beside the page heading to retrieve the latest information.

<figure><img src="../../.gitbook/assets/system-status-router (1).png" alt=""><figcaption></figcaption></figure>

### Router information

| **Field**        | **Example or possible values** | **Description**                                                                                      |
| ---------------- | ------------------------------ | ---------------------------------------------------------------------------------------------------- |
| Model            | Hera600v6                      | Model identifier displayed by the Hera 604 interface.                                                |
| Serial number    | 04425600823330100094           | Unique serial number of the router. The serial number also appears on the label underneath the unit. |
| Software version | Hera600v6 2.0.2GA              | Version of the Eseye router software installed on the router.                                        |
| Hostname         | Hera600v6                      | Name that identifies the router on the local network.                                                |
| Firmware version | OpenWrt Chaos Calmer 15.05.1   | Version of the underlying router firmware.                                                           |
| Kernel version   | 4.4.60                         | Version of the operating-system kernel running on the router.                                        |
| Local time       | Fri Aug 14 2026 13:34:49       | Current date and time reported by the router. The time is obtained from the configured NTP servers.  |
| Last restart     | Fri Aug 14 2026 09:20:47       | Date and time when the router last started.                                                          |
| Uptime           | 4h 14m 2s                      | Time elapsed since the last restart. This value resets when the router restarts.                     |
| Load average     | 0.17; 0.09; 0.02               | Average processing load during the previous one, five and 15 minutes.                                |
| Site name        | Default                        | Name assigned to the installation site.                                                              |
| Site location    | Default                        | Address or description assigned to the installation site.                                            |
| Site notes       | 1038-6\_Wifi                   | Configuration version running on the router.                                                         |

You can change **Site name** and **Site location** under **Basic settings** > **Router** > **Name and location**.

> **Important:** Do not change **Site notes**. This value identifies the configuration version running on the router and is required for device management.
