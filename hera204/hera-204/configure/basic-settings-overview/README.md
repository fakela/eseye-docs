# Basic Settings overview

Clicking the 'Basic Settings' button on the Hera web home page takes you to the Basic settings section. The Basic settings section allows the user to configure the Hera 204 in a user-friendly way. The sections below can be accessed by clicking the relevant header on this page. Some sections contain a 'Status (read only)' page, which is covered in the System Status page.

![Basic Settings](https://733576849-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FY2LsJ6998Uo7AtYcmJWd%2Fuploads%2FTv0tID4F74aIseFyNKCM%2Fbasic_settings_screenshot.png?alt=media\&token=30b80f9a-e94c-473a-a0ad-c2d7d868532b)

### In this section

{% content-ref url="/broken/spaces/Y2LsJ6998Uo7AtYcmJWd/pages/MC2FCJm7T7cLnBnkCwRr" %}
[Broken link](/broken/spaces/Y2LsJ6998Uo7AtYcmJWd/pages/MC2FCJm7T7cLnBnkCwRr)
{% endcontent-ref %}

{% content-ref url="/broken/spaces/Y2LsJ6998Uo7AtYcmJWd/pages/7r5UWRhZH7kkVbfuUFUC" %}
[Broken link](/broken/spaces/Y2LsJ6998Uo7AtYcmJWd/pages/7r5UWRhZH7kkVbfuUFUC)
{% endcontent-ref %}

{% content-ref url="/broken/spaces/Y2LsJ6998Uo7AtYcmJWd/pages/ei0acyA04xok1ibQAItU" %}
[Broken link](/broken/spaces/Y2LsJ6998Uo7AtYcmJWd/pages/ei0acyA04xok1ibQAItU)
{% endcontent-ref %}

{% content-ref url="/broken/spaces/Y2LsJ6998Uo7AtYcmJWd/pages/fcjQ242zmfbjWxQIRAp0" %}
[Broken link](/broken/spaces/Y2LsJ6998Uo7AtYcmJWd/pages/fcjQ242zmfbjWxQIRAp0)
{% endcontent-ref %}

{% content-ref url="/broken/spaces/Y2LsJ6998Uo7AtYcmJWd/pages/fneXzxhzhDskzmj9As1g" %}
[Broken link](/broken/spaces/Y2LsJ6998Uo7AtYcmJWd/pages/fneXzxhzhDskzmj9As1g)
{% endcontent-ref %}

{% content-ref url="/broken/spaces/Y2LsJ6998Uo7AtYcmJWd/pages/HWsGUcbk10tGLIPjtTtC" %}
[Broken link](/broken/spaces/Y2LsJ6998Uo7AtYcmJWd/pages/HWsGUcbk10tGLIPjtTtC)
{% endcontent-ref %}

## Name and location

| Field Name    | Sample value | Explanation                               |
| ------------- | ------------ | ----------------------------------------- |
| Site Name     | Eseye        | User defined Site Name.                   |
| Site Location | Eseye Office | User defined Site Location.               |
| GPS           | Disabled     | NOTE: GPS is not supported on the Hera204 |
| Notes         | 1038-2       | The running configuration version.        |

## Local Area Network (LAN)

This page is used to configure the LAN network, where all the devices and computers that connect to the router will reside. These settings are applied to the Wi-Fi if used in Access Point Mode and the Ethernet port if used as a LAN port.

### LAN IP Address

| Field name            | Sample value  | Explanation                                                                |
| --------------------- | ------------- | -------------------------------------------------------------------------- |
| 1. Address Assignment | Static/DHCP   | Determines whether the LAN subnet is statically or dynamically configured. |
| 2. IP address         | 192.168.1.1   | Address that the router uses on the LAN network.                           |
| 3. IP netmask         | 255.255.255.0 | A mask used to define how "large" the LAN network is.                      |

### DHCP Server

The DHCP server is the router's side service that can automatically configure the TCP/IP settings of any device that requests such a service. If a device connects that has been configured to obtain IP address automatically the DHCP server will lease an IP address, and the device will be able to fully communicate with the router.

| Field Name       | Sample value     | Explanation                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| ---------------- | ---------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1. DHCP Server   | Enable / Disable | Manage DHCP server                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| 2. Start Address | 100              | The starting address of the range that the DHCP server can use to give out to devices. E.g.: if the LAN IP is 192.168.2.1 and the subnet mask is 255.255.255.0 that means that in the network a valid IP address has to be in the range of \[192.168.2.1 – 192.168.2.254] (192.168.2.0 and 192.168.2.255 are special unavailable addresses). If the Start value is set to 100 then the DHCP server will only be able to lease out addresses starting from 192.168.2.100 |
| 3. End Address   | 249              | The end address of the range that the DHCP Server can use to give out to devices.                                                                                                                                                                                                                                                                                                                                                                                       |

### DHCP Fixed Hosts

DHCP Fixed Hosts are used to bind a specific DHCP device to an IP address. The entry enables devices using the specified MAC addresses to always use the specified IP address.

This page is used to configure static IP leases or fixed hosts.

| Field Name     | Sample Value      | Explanation                                    |
| -------------- | ----------------- | ---------------------------------------------- |
| 1. Name        | Host1             | An arbitrary name to call the fixed host entry |
| 2. IP address  | 192.168.0.101     | Device's IP address                            |
| 3. MAC address | 00:D0:4C:00:01:01 | Device's MAC address                           |

### DHCP allocated addresses

The DHCP allocated addresses page displays current DHCP leases of the Hera204.

| Field Name     | Sample Value        | Explanation                                                   |
| -------------- | ------------------- | ------------------------------------------------------------- |
| 1. Hostname    | Office-PC           | Hostname of the connected device                              |
| 2. IP address  | 192.168.0.100       | DHCP IP Address given to the connected device by the Hera 204 |
| 3. MAC address | eb:91:bc:d6:9d:de   | Connected device's MAC address                                |
| 4. Expires     | 2026/06/03 00:36:31 | Date/time that the DHCP lease expires                         |

## Wireless

### Wireless Configuration

This page is used to configure the Hera 204 wireless interface. The router uses a 2.4/5 GHz Dual-band radio.

| Field Name       | Sample Value                   | Explanation                                                                                                                                                             |
| ---------------- | ------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1. Hardware Mode | 802.11g                        | The 802.11 standard to be used. The options work in conjunction with the bandwidth options. Further details in the next section.                                        |
| 2. Status        | Enabled                        | Displays whether or not the radio is enabled or disabled.                                                                                                               |
| 3. Country       | USA (United States of America) | The country setting for the wireless interface, ensuring local compliance and compatibility. Note: Certain channels may be restricted or unavailable in some countries. |
| 4. Channel       | Auto                           | The Wi-Fi channel to be used by the Hera 204 radio. The channels available depend on the hardware mode and country selected.                                            |
| 5. Bandwidth     | 802.11ac rates 80MHz           | Selects which Bandwidth rates to use. These will vary depending on the hardware mode selected.                                                                          |

How wireless configuration works:

2.4 GHz Mode: The Wireless module will automatically select 2.4GHz mode when Hardware mode is configured to 802.11b or 802.11g.

Using the Bandwidth setting with 802.11g mode enables setting 802.11n mode using 2.4GHz with 20MHz or 40MHz Bandwidth options.

5 GHz Mode: The wireless module will automatically select 5GHz mode when Hardware mode is configured for 802.11a.

From this mode, the Bandwidth setting can be used to upgrade from 802.11a to 802.11n or 802.11ac modes with various additional bandwidth options up from 20 - 80MHz

### Access Points

The Access Points page is used to configure wireless access points on the Hera 204 router.

| Field name              | Sample value                                         | Explanation                                                                                                                                                                                                                                         |
| ----------------------- | ---------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1. Name                 | Default\_radio0                                      | An arbitrary name for the Access Point                                                                                                                                                                                                              |
| 2. Device               | Wifi0                                                | Always set to Wifi0                                                                                                                                                                                                                                 |
| 3. Status               | Enabled/Disabled                                     | Enable/Disable Access Point                                                                                                                                                                                                                         |
| 4. Network Name         | Hera200AccessPoint                                   | The wireless network's identification string. This is the name of the available Wi-Fi network. When other Wi-Fi capable computers or devices scan the area for Wi-Fi networks they will see the available network with this name.                   |
| 5. SSID Visibility      | Broadcast/Hidden                                     | Determines whether the Access Point is visible to nearby clients. If SSID visibility is configured to Hidden, then SSID will be required to be manually entered upon connection to Access Point.                                                    |
| 6. Security             | None/WEP Open System/WEP Shared Key/WPA-PSK/WPA-PSK2 | Selects the security level of the Wireless encryption. These are in the order of least to most secure.                                                                                                                                              |
| 7. Pass phrase          | Unique Password                                      | The password will be required for any clients attempting to connect to this SSID                                                                                                                                                                    |
| 8. MAC Filter           | No filtering/Allow/Deny                              | No filtering – all authenticated clients will be allowed to use the access point. Allow – Creates a whitelist of devices that are allowed to use the access point. Deny – Creates a blacklist to stop specific devices from using the access point. |
| 9. Filtered MAC address | One or more MAC addresses                            | Allows multiple MAC addresses to be specified.                                                                                                                                                                                                      |

For Wireless Client configuration, contact the Eseye Support/Device Management team.

## Mobile Network

### Connection

Configure mobile settings which are used when connecting to a cellular network.

| Field Name           | Sample value                                                              | Explanation                                                                                                                                                                                                                                                                                                                         |
| -------------------- | ------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1. Mobile Connection | Enabled/Disabled                                                          | Enabled enables the mobile connection to provide a data session. Disabled Disables the mobile data connection.                                                                                                                                                                                                                      |
| 2. Metric            | Value between 1 and 10                                                    | Sets the Default Route Priority. When working with multiple default routes, this value determines which default route is the primary link.                                                                                                                                                                                          |
| 3. Cellular Profiles | —                                                                         | Up to 10 Cellular Profiles can be created. Each profile can be manually selected for use. They can also be used in conjunction with the health monitor. The health monitor can be programmed to cycle through a selection of profiles until a good connection is achieved. The below parameters can be configured for each Profile. |
| a. APN               | "eseye1"                                                                  | Access Point Name (APN) is a configurable network identifier used by a mobile device when connecting to a GSM carrier.                                                                                                                                                                                                              |
| b. PIN number        | Up to an 8-digit number, e.g. 12345678                                    | A personal identification number is a secret numeric password shared between a user and a system that can be used to authenticate the user to the system. Use this only if the SIM card has PIN enabled.                                                                                                                            |
| c. Username          | "username"                                                                | The username that would be used to connect to the carrier's network. This field becomes available when an authentication method is selected (i.e. authentication method is not "none").                                                                                                                                             |
| d. Password          | "password"                                                                | The password that would be used to connect to the carrier's network. This field becomes available when an authentication method is selected (i.e. authentication method is not "none").                                                                                                                                             |
| e. SIM               | ChipSim/SIM1                                                              | Selects the SIM slot for the profile to use.                                                                                                                                                                                                                                                                                        |
| f. Promote           | —                                                                         | Changes the profiles order in the list. This would be used in conjunction with the 'Health monitor' when cycling through profiles.                                                                                                                                                                                                  |
| Advanced Settings    | This feature is only available by editing the configuration file directly | For more details on advanced settings, please contact Eseye Support.                                                                                                                                                                                                                                                                |
| Service mode         | 2G only, 3G only, 4G only or automatic.                                   | The network preference. If the local mobile network supports 2G 3G and 4G, specify which network to connect with e.g.: if 2G only is selected, the router will connect only to a 2G network. If Auto is selected, then the router will connect to the network that provides better connectivity.                                    |
| Provider             | MCC and MNC of locally available Cellular Providers                       | This feature fixes a cellular link to connect to a specific provider. This feature is not recommended on a roaming network as it limits failover if the network goes down.                                                                                                                                                          |

{% hint style="warning" %}
If an invalid PIN number was entered (i.e. the entered PIN does not match the one that was used to protect the SIM card), the SIM card will get blocked. To avoid this happening it is highly advised to use an SIM without a PIN. If a protected SIM is inserted and the PIN number is incorrect, the SIM card won't get blocked immediately, however it will be blocked after a couple of reboots OR when the configuration is saved.
{% endhint %}

## Wide Area Network (WAN)

### WAN IP address

If the Hera Router is configured to use an Ethernet WAN connection, then this section will be available to make further changes. To configure an Ethernet WAN, use the Setup Wizard section and select the appropriate settings.

| # | Type                     | Sample Value   | Explanation                                                                                  |
| - | ------------------------ | -------------- | -------------------------------------------------------------------------------------------- |
| 1 | Address Assignment       | Static         | Static/DHCP. Determines whether the IP address is assigned manually or dynamically.          |
| 2 | WAN IP Address           | 192.168.107.31 | For static, the IP address of the Ethernet WAN interface can be manually entered here.       |
| 3 | Netmask                  | 255.255.255.0  | For Static Mode, the Subnet Mask of the Ethernet WAN interface can be manually entered here. |
| 4 | DNS Addresses            | 192.168.111.2  | For Static, multiple DNS Server IP addresses can be entered here.                            |
| 5 | Obtain Gateway from DHCP | Yes/No         | Determines whether the gateway is delivered by the DHCP server or not.                       |
|   | Obtain DNS from DHCP     | Yes/No         | Determines whether the DNS Server(s) is(are) delivered by the DHCP server or not.            |
| 6 | Metric                   | 5              | Determines the Default Route Priority. Used when multiple default routes are present.        |
| 7 | Gateway                  | 192.168.107.1  | For Static Mode, the Router Default Ethernet Gateway (the interface's next-hop address).     |

{% hint style="info" %}
This table's Explanation column was wrapped/truncated in the source PDF; reconstructed based on context and phrasing used elsewhere in the manual — worth a quick check against the original.
{% endhint %}

## Active and static routes

### Active routes

The active routes page displays a list of active routes that the router has been configured to use.

| # | Field name  | Value            | Explanation                                                                                                        |
| - | ----------- | ---------------- | ------------------------------------------------------------------------------------------------------------------ |
| 1 | Destination | IP address       | The IP address of the destination network                                                                          |
| 2 | Netmask     | IP netmask       | Mask that is applied to the target to determine what actual IP addresses the routing rule applies to               |
| 3 | Interface   | ethwan / cellpri | The interface that the active route applies to                                                                     |
| 4 | Gateway     | IP address       | Where the router will send all the traffic that applies to the rule                                                |
| 5 | Cost        | Numerical value  | Corresponds to the 'weight' of the route. Routes with a lower cost will take priority over other identical routes. |

### Static Routes

Routes can be configured using the table under the 'Static routes:' heading.

Routes can be applied to a single IP address, or a range of addresses by altering the netmask option. See below for a list of sample routes:

| Destination IP | Subnet Mask     | Outcome                                                 |
| -------------- | --------------- | ------------------------------------------------------- |
| 192.168.55.161 | 255.255.255.255 | Only applies to 192.168.55.161                          |
| 192.168.55.0   | 255.255.255.0   | Applies to IPs in range 192.168.55.0-192.168.55.255     |
| 192.168.55.240 | 255.255.255.240 | Applies to IPs in range 192.168.55.240 - 192.168.55.255 |
| 192.168.55.161 | 255.255.255.0   | 192.168.55.0 - 192.168.55.255                           |
| 192.168.0.0    | 255.255.0.0     | 192.168.0.0 - 192.168.255.255                           |

| # | Field name  | Value            | Explanation                                                                                                        |
| - | ----------- | ---------------- | ------------------------------------------------------------------------------------------------------------------ |
| 1 | Name        | String           | A friendly name for the static route                                                                               |
| 2 | Destination | IP address       | The IP address of the destination network                                                                          |
| 3 | Netmask     | IP netmask       | Mask that is applied to the target to determine what actual IP addresses the routing rule applies to               |
| 4 | Interface   | ethwan / cellpri | The interface that the active route applies to                                                                     |
| 5 | Gateway     | IP address       | Where the router will send all the traffic that applies to the rule                                                |
| 6 | Cost        | Numerical value  | Corresponds to the 'weight' of the route. Routes with a lower cost will take priority over other identical routes. |

## Firewall

In this section we will look over the various firewall features that come with the Hera 204.

### Inbound rules

The router's firewall is a standard Linux iptables package, which uses routing chains and policies to facilitate control over inbound and outbound traffic.

| # | Field Name                  | Sample value               | Explanation                                                                                                                                                     |
| - | --------------------------- | -------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1 | Firewall Enable             | Enable/Disable             | Switches the firewall on and off                                                                                                                                |
| 2 | Rule Name                   | Allow-Ping                 | Arbitrary name to identify the rule                                                                                                                             |
| 3 | Protocol                    | Drop down list             | Determines the underlying protocol to be applied to the rule. These are protocols that can't be identified by a specific port number e.g. UDP/TCP/ICMP/ESP      |
| 4 | Source IP Address/Netmask   | 172.16.84.0/255.255.255.0  | Limits the rule to hosts that are within the specified subnet range                                                                                             |
| 5 | Source Port Start/End       | 10080/10082                | Limits the rule to hosts that use the specified Source port range. The same value in both Start and End port will limit to one port.                            |
| 6 | Destination IP Address/Mask | 10.16.43.1/255.255.255.255 | This rule is applicable to solutions running multiple WAN interfaces. By choosing the subnet of one WAN interface, rules are only applied to the WAN specified. |
| 7 | Destination Port Start/End  | 443/443                    | Defines the port or port range that will be accessible on the Device.                                                                                           |
| 8 | Permission                  | Allowed/Denied             | Determines what happens to the packet when it reaches the Hera WAN Port                                                                                         |

{% hint style="info" %}
Inbound rules basically open up ports to enable communication with the router services. Enabling Destination port 443 opens up HTTPS to be able to connect to the Hera GUI. Destination Port 22 allows SSH to connect to the Hera CLI. If ICMP is selected in the Protocol section, then ICMP Ping will be allowed.
{% endhint %}

DEFAULT: When a packet goes through a firewall chain it is matched against all the rules for that specific chain. If no rule matches said packet, an according Action (either Drop or Reject or Accept) is performed. Accept – Packet gets to continue down the next chain. Drop – Packet is stopped and deleted. Reject – Packet is stopped, deleted and, differently from Drop, an ICMP packet containing a message of rejection is sent to the source of the dropped packet.

### Outbound rules

| # | Field Name                  | Sample value                  | Explanation                                                                                                                                                |
| - | --------------------------- | ----------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1 | Rule Name                   | HTTPS-Block                   | Arbitrary name to identify the rule                                                                                                                        |
| 2 | Protocol                    | Drop down list                | Determines the underlying protocol to be applied to the rule. These are protocols that can't be identified by a specific port number e.g. UDP/TCP/ICMP/ESP |
| 3 | Source IP Address/Netmask   | 192.168.0.102/255.255.255.255 | This rule can be used to apply the rule to only specific LAN side devices.                                                                                 |
| 4 | Source Port Start/End       | 10080/10082                   | Limits the rule to hosts that use the specified Source port range. The same value in both Start and End port will limit to one port.                       |
| 5 | Destination IP Address/Mask | 10.16.43.1/255.255.255.255    | These settings define the IP address or range to be blocked on the outbound rule. No IP ranges are blocked by default.                                     |
| 6 | Destination Port Start/End  | 443/443                       | These settings define the port range to be blocked on the outbound rule. No ports are blocked outbound by default.                                         |
| 7 | Permission                  | Allowed/Denied                | Denied will block traffic from leaving the router. Allowed will allow outbound traffic. As Allow is the default it is not expected to be used              |
| 8 | Enabled                     | Enabled/Disabled              | Enables or Disables specified rule                                                                                                                         |

Outbound rules block the LAN side devices from communicating with specific IP ranges or protocols. E.g. a HTTP block will block TCP port 80 to limit web browsing to HTTP sites.

### Redirections

This allows the definition of custom port forwarding / redirect rules.

| # | Field Name              | Sample value   | Explanation                                                                                                                                                           |
| - | ----------------------- | -------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1 | Redirection Name        | SSHLAN         | Descriptive name to identify the specific Redirect rule                                                                                                               |
| 2 | Destination IP Address  | 192.168.0.101  | The IP address of the LAN device that this port forward rule is designed for.                                                                                         |
| 3 | Protocol                | Drop down list | Determines the underlying protocol to be applied to the rule. These are protocols that can't be identified by a specific port number e.g. UDP/TCP/ICMP/ESP            |
| 4 | External Port Start/End | 10443/10443    | This is the destination port or port range to use when connecting to an external port. The Router uses this port to determine which local port to send the packet to. |
| 5 | Internal Port Start/End | 443/443        | This is the final destination port to use for connecting to the LAN device. Use the same port number for Start/End as range is not used here.                         |

Port forwarding/Redirects allow remote connection to LAN side devices. This is achieved by specifying the LAN device IP address and internal port number for the required application. This local IP address/Port is reached by sending a packet to the external WAN IP using one of the external port numbers.

`<External WAN IP:External Port>` is redirected or forwarded to `<Internal/Destination IP:Internal Port>`
