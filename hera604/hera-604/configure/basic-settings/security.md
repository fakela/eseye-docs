# Security

Open **Basic Settings > Security > Firewall** to control traffic entering, leaving, or passing through the Hera 604.

<figure><img src="../../.gitbook/assets/Screenshot 2026-08-14 at 15.37.52.png" alt=""><figcaption></figcaption></figure>



> **Warning:** Disabling the firewall or creating an unrestricted inbound rule can expose the router and connected equipment. Make firewall changes only from an approved network design and keep access limited to the required sources, protocols, and ports.

Use the **Firewall** control to enable or disable firewall processing. Keep it enabled for operational deployments unless the security design explicitly requires otherwise.

#### Inbound rules

Inbound rules control traffic arriving at the router or its exposed services.

| Field                              | Description                                                                         |
| ---------------------------------- | ----------------------------------------------------------------------------------- |
| Rule name                          | Descriptive name for the rule.                                                      |
| Protocol                           | Protocol to which the rule applies, such as TCP, UDP, or ICMP.                      |
| Source IP address and netmask      | Limits the rule to a source host or network.                                        |
| Source port start and end          | Limits the rule to a source port or range. Enter the same value twice for one port. |
| Destination IP address and netmask | Limits the rule to a destination host, interface address, or network.               |
| Destination port start and end     | Destination service port or range. Enter the same value twice for one port.         |
| Permission                         | Allows or denies matching traffic.                                                  |
| Status                             | Enables or disables the individual rule.                                            |

The default configuration can include rules for SSH, HTTPS, ICMP, and CWMP. Do not remove or broaden these rules unless the change has been approved.

#### Outbound rules

Outbound rules control traffic sent from LAN devices through the router.

They use the same rule name, protocol, source, destination, port, permission, and status fields as inbound rules. Use them to allow or block defined traffic from specific local devices or networks.

#### Redirections

Redirections forward traffic received on an external WAN port to a service on a LAN device.

| Field                       | Description                                                |
| --------------------------- | ---------------------------------------------------------- |
| Redirection name            | Descriptive name for the forwarding rule.                  |
| Destination IP              | LAN address of the device receiving the forwarded traffic. |
| Protocol                    | Protocol used by the forwarded service.                    |
| External port start and end | Port or range reached on the router's WAN address.         |
| Internal port start and end | Port or range used by the destination LAN service.         |

> **Important:** A redirection exposes a LAN service through a WAN interface. Limit the rule to the required protocol and ports, and confirm that the destination device is secured before enabling it.

Use **Create** to add a firewall rule or redirection, **Remove** to delete one, and **Promote** to move a rule higher in its table. Select **Save** after making changes.
