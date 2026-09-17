# About custom DNS entries

Some customers require a customised DNS service for their devices, which overrides the domain name values set with the domain registrar.

This is most often required to enable devices to connect to a central network in different ways, such as when some devices use a VPN connection and others connect over the public internet. If both types of connection use the same domain name for the central network, the DNS service resolving the domain name needs to determine which IP address is required for each device.

{% hint style="warning" %}
While you can use custom DNS within a secure subnet to prevent unauthorised DNS lookups, customers must configure their devices correctly to prevent them from looking up DNS entries outside of the Allowlist during their normal operation. As many devices retry DNS lookups if they fail, this will cause high data usage and create a high load on Eseye's DNS server.
{% endhint %}

The examples below show scenarios in which this customised DNS service is required.

### Example 1 – cellular fallback connection:

A device can connect to a central network in two ways:

* Using a Digital Subscriber Line (DSL) to connect over the internet
* As a fallback, using a cellular connection to connect via a VPN

Both types of connection use the same domain name. Public DNS services resolve this to the IP address that the customer configured for the domain (the public IP address).

To enable the devices connecting via cellular to use the private IP address for the VPN, the devices must use a DNS service that can supply the private IP address, rather than resolving the domain name with the authoritative name server for the domain.

### Example 2 – VPN and non-VPN connections:

All the devices in an IoT deployment connect to the central network using a cellular connection. Some devices in the deployment use a VPN from the APN while others are NAT'd straight onto the internet.

The customer requires all devices to use the same software, so it is not possible for the devices to use different domain names for the different connection types. The devices must therefore use a DNS service that can supply the private IP address to devices that use the VPN. For other devices, it can resolve the domain name with the authoritative name server for the domain.

### Example 3 – test devices vs real devices:

Customers need to test if their DNS server settings work before rolling out the configuration to real devices. A DNS service can direct test device DNS lookups to a test server, while real devices are directed to the existing internet address.

## AnyNet Custom DNS entries

The AnyNet DNS service can include custom DNS entries for deployments that require customer-specific resolutions for domain names.

Using the AnyNet solution, devices are grouped into a secure subnet. This enables customers to configure security options for the devices, such as VPNs and ACL rules. In addition, custom DNS entries can be configured for a subnet. These custom entries enable mappings between Fully Qualified Domain Names (FQDNs) and the IP addresses that they should resolve to.

The AnyNet DNS service operates as follows:

* If a name resolution request is from a device in a subnet:
  * If there is a custom DNS entry for the requested domain name, it returns the IP address configured for that domain name to the device
  * If there isn’t a custom DNS entry for the requested domain name, it resolves the name using the Authoritative Name Server for the domain
* If the device is not in a subnet, it resolves the name using the Authoritative Name Server for the domain

### Alternatives to custom DNS entries

Configuring custom DNS entries can be avoided if different domain names can be used for different types of connections and the devices can be programmed to know which domain name they should use when they connect.

Some devices use hardcoded IP addresses to connect to a central network. This is not recommended as it prevents any changes to the server IP address being made in the future.

{% hint style="info" %}
Contact your Account Manager if you have specific DNS requirements.
{% endhint %}
