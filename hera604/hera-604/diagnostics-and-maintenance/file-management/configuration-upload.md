---
description: Upload a router configuration backup.
---

# Configuration upload

Open **Diagnostics & Maintenance → File Management → Configuration upload** to restore a compatible Hera 604 configuration archive.

<figure><img src="../../.gitbook/assets/Screenshot 2026-08-14 at 16.59.07.png" alt="File Management configuration upload page."><figcaption></figcaption></figure>

To upload a configuration:

1. Confirm the `.tar.gz` backup belongs to the correct router and software version.
2. Record the current LAN address and active WAN connection.
3. Select **Upload**.
4. Select **Choose file**, and select the configuration archive.
5. Select **OK** to upload and apply the configuration.
6. Reboot at the approved maintenance time when prompted.
7. Reconnect using the address in the restored configuration.

{% hint style="warning" %}
Restoring a configuration can change LAN, WAN, mobile, wireless, routing, firewall, and administrator settings. An incorrect archive can make the router unreachable.
{% endhint %}
