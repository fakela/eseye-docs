# Local Area Network (LAN)

Use the LAN pages to configure the local network used by equipment connected to the Hera 604 over Ethernet or Wi-Fi.

#### Status (read only)

Open **Basic Settings > Local Area Network (LAN) > Status (read only)** to view the address currently used by the LAN interface.

<figure><img src="../../.gitbook/assets/Screenshot 2026-08-14 at 15.36.14.png" alt=""><figcaption></figcaption></figure>

| Field              | Example       | Description                                                          |
| ------------------ | ------------- | -------------------------------------------------------------------- |
| Address assignment | STATIC        | Shows whether the current LAN address is static or assigned by DHCP. |
| LAN IP address     | 192.168.0.1   | Address currently used by the Hera 604 on the local network.         |
| Net mask           | 255.255.255.0 | Subnet mask currently applied to the LAN interface.                  |

The values on this page cannot be edited. Select the **refresh** icon to retrieve the latest information.

> **Important:** Changing the LAN IP address can end the current browser session. Record the new address and make sure the operator device can join the new subnet before saving.

#### LAN IP address

Open **Basic Settings > Local Area Network (LAN) > LAN IP address**.

<figure><img src="../../.gitbook/assets/Screenshot 2026-08-14 at 15.36.24.png" alt=""><figcaption></figcaption></figure>



| Field              | Example            | Description                                                                                                          |
| ------------------ | ------------------ | -------------------------------------------------------------------------------------------------------------------- |
| Address assignment | `Static` or `DHCP` | Determines whether the router's LAN address is entered manually or assigned by another DHCP server.                  |
| LAN IP address     | 192.168.0.1        | Address used by the Hera 604 on the local network. Operators normally use this address to open the router interface. |
| Net mask           | 255.255.255.0      | Defines which IP addresses belong to the local subnet.                                                               |

**Static address assignment**

Select **Static** when the Hera 604 must use a fixed LAN address.

1. Set **Address assignment** to **Static**.
2. Enter the **LAN IP address** defined for the installation.
3. Enter the **Net mask**.
4. Select **Save**.
5. If the address changed, reconnect to the router using the new LAN IP address.



**DHCP address assignment**

Select **DHCP** when another DHCP server on the local network will assign the Hera 604 LAN address.

1. Set **Address assignment** to **DHCP**.
2. Select **Save**.
3. Open **Status (read only)** after the address has been assigned to view the current LAN IP address and net mask.



> **Important:** A DHCP-assigned LAN address can change. Confirm how operators will find the router's current address before using this option.

#### DHCP server

The Hera 604 DHCP server can automatically assign IP settings to devices on the local network.

Open **Basic Settings > Local Area Network (LAN) > DHCP server**.

<figure><img src="../../.gitbook/assets/Screenshot 2026-08-14 at 15.36.35.png" alt=""><figcaption></figcaption></figure>

| Field         | Example                 | Description                                                                                                         |
| ------------- | ----------------------- | ------------------------------------------------------------------------------------------------------------------- |
| DHCP server   | `Enabled` or `Disabled` | Enables or disables automatic IP address allocation on the LAN.                                                     |
| Start address | 20                      | First host number in the DHCP allocation range. With LAN prefix `192.168.0`, this example begins at `192.168.0.20`. |
| End address   | 219                     | Last host number in the DHCP allocation range. With LAN prefix `192.168.0`, this example ends at `192.168.0.219`.   |

> **Note:** Keep fixed addresses used by infrastructure or field equipment outside the automatic DHCP range, unless you create a matching fixed-host reservation.

Select **Save** after configuring the range.

#### DHCP fixed hosts

Use **DHCP fixed hosts** to ensure that a device receives the same IP address whenever it connects using DHCP.

Open **Basic Settings > Local Area Network (LAN) > DHCP fixed hosts**, then select **Create**.

<figure><img src="../../.gitbook/assets/Screenshot 2026-08-14 at 15.36.40.png" alt=""><figcaption></figcaption></figure>



| Field       | Example           | Description                                         |
| ----------- | ----------------- | --------------------------------------------------- |
| Name        | Sensor-01         | Descriptive name for the reservation.               |
| IP address  | 192.168.0.50      | LAN address reserved for the device.                |
| MAC address | 00:D0:4C:00:01:01 | Hardware address of the device's network interface. |

Confirm that the reserved IP address is in the LAN subnet and is not already used by another device. Select **Save** after creating or editing the reservation.

#### DHCP allocated addresses

Open **Basic Settings > Local Area Network (LAN) > DHCP allocated addresses** to view current DHCP leases.

This page is read-only. Select the **refresh** icon to retrieve the latest values.

<figure><img src="../../.gitbook/assets/Screenshot 2026-08-14 at 15.36.45.png" alt=""><figcaption></figcaption></figure>

| Field       | Example             | Description                                         |
| ----------- | ------------------- | --------------------------------------------------- |
| Hostname    | MacBookPro          | Name reported by the connected device.              |
| IP address  | 192.168.0.20        | Address allocated to the device by the Hera 604.    |
| MAC address | c2:ff:8b:e1:4a      | Hardware address of the device's network interface. |
| Expires     | 2026/08/15 14:33:03 | Date and time when the current DHCP lease expires.  |
