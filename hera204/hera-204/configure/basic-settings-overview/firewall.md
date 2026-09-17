# Firewall

Configure firewall rules and port redirections.

## Inbound rules

The router firewall uses Linux `iptables` routing chains and policies.

![Inbound rules](https://733576849-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FY2LsJ6998Uo7AtYcmJWd%2Fuploads%2FQmgjpWaXY4n4AsRsr9GF%2Finbound_rules_figure.png?alt=media\&token=36ae7cd0-43bb-4463-864f-cf4f6650ff63)

| # | Field name                  | Sample value               | Explanation                                                   |
| - | --------------------------- | -------------------------- | ------------------------------------------------------------- |
| 1 | Firewall Enable             | Enable/Disable             | Turns the firewall on or off.                                 |
| 2 | Rule Name                   | Allow-Ping                 | Name used to identify the rule.                               |
| 3 | Protocol                    | Drop-down list             | Protocol applied to the rule, such as UDP, TCP, ICMP, or ESP. |
| 4 | Source IP Address/Netmask   | 172.16.84.0/255.255.255.0  | Limits the rule to the specified source subnet.               |
| 5 | Source Port Start/End       | 10080/10082                | Limits the rule to a source port or port range.               |
| 6 | Destination IP Address/Mask | 10.16.43.1/255.255.255.255 | Selects the WAN subnet where the rule applies.                |
| 7 | Destination Port Start/End  | 443/443                    | Device port or port range made accessible.                    |
| 8 | Permission                  | Allowed/Denied             | Action when matching traffic reaches the Hera WAN port.       |

{% hint style="info" %}
Inbound rules open ports for router services. Port `443` enables HTTPS. Port `22` enables SSH. Select ICMP to allow ping.
{% endhint %}

If no rule matches, the default action applies. **Accept** continues processing. **Drop** stops and deletes the packet. **Reject** also sends an ICMP rejection to its source.

## Outbound rules

![Outbound rules](https://733576849-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FY2LsJ6998Uo7AtYcmJWd%2Fuploads%2FrNcHP1ckLEWdC5QagSHj%2Foutbound_rules_figure.png?alt=media\&token=7d350176-9d29-4669-8345-d9133594096a)

| # | Field name                  | Sample value                  | Explanation                                                   |
| - | --------------------------- | ----------------------------- | ------------------------------------------------------------- |
| 1 | Rule Name                   | HTTPS-Block                   | Name used to identify the rule.                               |
| 2 | Protocol                    | Drop-down list                | Protocol applied to the rule, such as UDP, TCP, ICMP, or ESP. |
| 3 | Source IP Address/Netmask   | 192.168.0.102/255.255.255.255 | Limits the rule to specific LAN devices.                      |
| 4 | Source Port Start/End       | 10080/10082                   | Limits the rule to a source port or port range.               |
| 5 | Destination IP Address/Mask | 10.16.43.1/255.255.255.255    | Destination address or range to block.                        |
| 6 | Destination Port Start/End  | 443/443                       | Destination port or range to block.                           |
| 7 | Permission                  | Allowed/Denied                | `Denied` blocks outbound traffic. `Allowed` permits it.       |
| 8 | Enabled                     | Enabled/Disabled              | Enables or disables the rule.                                 |

Outbound rules restrict LAN devices from reaching specific IP ranges or protocols. For example, block TCP port `80` to prevent HTTP browsing.

## Redirections

Define custom port-forwarding and redirect rules.

![Redirections — SSHLAN example](https://733576849-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FY2LsJ6998Uo7AtYcmJWd%2Fuploads%2FFovh6PClKt4mrJfhBpFT%2Fredirection_name_sshlan_figure.png?alt=media\&token=27a5c5d5-047b-4038-a239-20db643da2c0)

| # | Field name              | Sample value   | Explanation                                                         |
| - | ----------------------- | -------------- | ------------------------------------------------------------------- |
| 1 | Redirection Name        | SSHLAN         | Name for the redirect rule.                                         |
| 2 | Destination IP Address  | 192.168.0.101  | LAN device address for this forwarding rule.                        |
| 3 | Protocol                | Drop-down list | Protocol applied to the rule.                                       |
| 4 | External Port Start/End | 10443/10443    | External destination port or port range.                            |
| 5 | Internal Port Start/End | 443/443        | Final LAN-device port. Use matching values when no range is needed. |

Port forwarding allows remote connections to LAN devices. Traffic sent to `<External WAN IP:External Port>` is forwarded to `<Internal/Destination IP:Internal Port>`.
