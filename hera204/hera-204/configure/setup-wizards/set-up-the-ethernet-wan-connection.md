---
description: Configure Ethernet WAN addressing in the Setup Wizard.
---

# Set up the Ethernet WAN connection

This page does not appear in **Cellular only** mode.

Configure the Ethernet WAN interface with DHCP or a static IP address.

![Set up the connection (Ethernet WAN)](https://733576849-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FY2LsJ6998Uo7AtYcmJWd%2Fuploads%2FE6B6fXYhxBEfizFx9uh9%2Faddress_figure.png?alt=media\&token=6da863a0-9f80-4e42-a804-ba455fa49978)

| Field | Type                            | Description                                                                                                           |
| ----- | ------------------------------- | --------------------------------------------------------------------------------------------------------------------- |
| 1     | Address assignment              | Select `Static` or `DHCP`. This setting determines whether the interface receives an address manually or dynamically. |
| 2     | WAN IP address                  | For static addressing, enter the Ethernet WAN address. For DHCP, this field shows the assigned address.               |
| 3     | Netmask                         | For static addressing, enter the subnet mask. For DHCP, this field shows the assigned netmask.                        |
| 4     | DNS addresses                   | For static addressing, enter one or more DNS server IP addresses.                                                     |
| 5     | Obtain gateway from DHCP        | Controls whether the DHCP server provides the gateway. Set this to `Yes` in most deployments.                         |
|       | Obtain DNS from DHCP            | Controls whether the DHCP server provides DNS server addresses.                                                       |
| 6     | Gateway                         | Gateway address for the site's access router.                                                                         |
| 7     | Use PPPoE/Username/Password/MTU | Enables a PPPoE connection and configures its username, password, and MTU.                                            |
