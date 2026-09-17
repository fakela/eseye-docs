# Wide Area Network (WAN)

The **WAN IP address** page is available when an Ethernet port has been configured as a WAN interface.

Open **Basic Settings > Wide Area Network (WAN) > WAN IP address**.

<figure><img src="../../.gitbook/assets/Screenshot 2026-08-14 at 15.36.53.png" alt=""><figcaption></figcaption></figure>



| Field                    | Example                  | Description                                                                                                                                |
| ------------------------ | ------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------ |
| Address assignment       | `DHCP` or `Static`       | Determines whether the upstream network assigns the Ethernet WAN settings or the operator enters them manually.                            |
| WAN IP address           | ---                      | IP address used by the Ethernet WAN interface. With DHCP, this remains blank until an address is assigned.                                 |
| Net mask                 | ---                      | Subnet mask used by the Ethernet WAN interface.                                                                                            |
| DNS addresses            | One or more IP addresses | DNS servers used for hostname resolution. Use the add control to enter additional addresses.                                               |
| Obtain gateway from DHCP | `Yes` or `No`            | Determines whether DHCP supplies the default gateway.                                                                                      |
| Obtain DNS from DHCP     | `Yes` or `No`            | Determines whether DHCP supplies the DNS server addresses.                                                                                 |
| Gateway                  | IP address               | Upstream router address. This field is used when the gateway is entered manually.                                                          |
| Metric                   | 1                        | Route metric assigned to the Ethernet WAN interface. When multiple WAN routes are available, the route with the lower metric is preferred. |

> **Warning:** Selecting **Remove ethernet WAN** deletes the Ethernet WAN interface and can immediately remove the router's wired upstream connection. Use Setup Wizards to create the interface again if it is removed.

Select **Save** after changing the Ethernet WAN settings.

