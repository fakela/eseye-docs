# Local Area Network (LAN)

Configure the LAN network for connected devices. These settings apply to Wi-Fi access-point mode and Ethernet LAN mode.

## LAN IP Address

| Field name            | Sample value  | Explanation                                                                |
| --------------------- | ------------- | -------------------------------------------------------------------------- |
| 1. Address Assignment | Static/DHCP   | Determines whether the LAN subnet is statically or dynamically configured. |
| 2. IP address         | 192.168.1.1   | Address that the router uses on the LAN network.                           |
| 3. IP netmask         | 255.255.255.0 | Defines the size of the LAN network.                                       |

![LAN IP Address](https://733576849-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FY2LsJ6998Uo7AtYcmJWd%2Fuploads%2F2voxRbmjVb6JhmJ5lNKU%2Flan_ip_address_figure.png?alt=media\&token=f93241c6-ca79-4fe7-8c26-50b4ed96f6df)

## DHCP Server

The DHCP server automatically assigns TCP/IP settings to requesting devices.

| Field name       | Sample value     | Explanation                                                                                                  |
| ---------------- | ---------------- | ------------------------------------------------------------------------------------------------------------ |
| 1. DHCP Server   | Enable / Disable | Manages the DHCP server.                                                                                     |
| 2. Start Address | 100              | First address the DHCP server can lease. For a `192.168.2.1/24` LAN, `100` starts leases at `192.168.2.100`. |
| 3. End Address   | 249              | Last address the DHCP server can lease.                                                                      |

![DHCP Server](https://733576849-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FY2LsJ6998Uo7AtYcmJWd%2Fuploads%2FKBO74C49HIqFcWQbUc77%2Fdhcp_server_figure.png?alt=media\&token=8ecfbcd3-7eb8-4ee8-a908-ab95413203ee)

## DHCP Fixed Hosts

Bind a device MAC address to a fixed IP address.

| Field name     | Sample value      | Explanation                    |
| -------------- | ----------------- | ------------------------------ |
| 1. Name        | Host1             | Name for the fixed-host entry. |
| 2. IP address  | 192.168.0.101     | Device IP address.             |
| 3. MAC address | 00:D0:4C:00:01:01 | Device MAC address.            |

![DHCP Fixed Hosts](https://733576849-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FY2LsJ6998Uo7AtYcmJWd%2Fuploads%2FTsGPLaOgIxdVWjrohpqu%2Fdhcp_fixed_hosts_figure.png?alt=media\&token=13c93038-c208-4cdd-9378-d71271d16766)

## DHCP allocated addresses

View current DHCP leases.

| Field name     | Sample value        | Explanation                            |
| -------------- | ------------------- | -------------------------------------- |
| 1. Hostname    | Office-PC           | Hostname of the connected device.      |
| 2. IP address  | 192.168.0.100       | DHCP address assigned by the Hera 204. |
| 3. MAC address | eb:91:bc:d6:9d:de   | Connected device MAC address.          |
| 4. Expires     | 2026/06/03 00:36:31 | DHCP lease expiration date and time.   |

![DHCP allocated addresses](https://733576849-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FY2LsJ6998Uo7AtYcmJWd%2Fuploads%2FxEzvtawwZyk0Hc3hf9Df%2Fdhcp_allocated_addresses_figure.png?alt=media\&token=0e30f911-00b5-4bb4-841f-274272b24f5a)
