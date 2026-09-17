---
description: Upload supported software to the Hera 604.
---

# Network time protocol (NTP)

<figure><img src="../../.gitbook/assets/Screenshot 2026-08-14 at 16.59.41.png" alt=""><figcaption></figcaption></figure>



Open **Diagnostics & Maintenance > System Settings > Network time protocol (NTP)** to configure clock synchronisation.

| Field                                   | Description                                                                                                                                 |
| --------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------- |
| Local NTP server                        | Enables or disables the router's local NTP server. This does not disable the router's NTP client.                                           |
| NTP servers                             | Lists the NTP servers used to synchronise the router clock. The screenshot shows `0.openwrt.pool.ntp.org` through `3.openwrt.pool.ntp.org`. |
| NTP pools                               | Lists any configured NTP pool sources.                                                                                                      |
| Use IPv4 for NTP server name resolution | When enabled, limits NTP hostname resolution to IPv4.                                                                                       |
| Minimum poll time                       | Minimum interval between NTP polls.                                                                                                         |
| Maximum poll time                       | Maximum interval between NTP polls.                                                                                                         |

If every NTP server is removed, the NTP client is disabled. Keep at least one reachable, approved time source. Accurate time is required for logs, certificates, and fault investigation.

###
