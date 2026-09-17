# Understanding the AnyNet Domain Name Service (DNS)

The Domain Name System (DNS) is a system for mapping human-readable domain names, such as those used in URLs or email addresses, to the IP addresses that are required to access resources on the internet. For example, DNS translates and maps the domain **eseye.com** to the IP address **13.224.227.134.**

DNS is a hierarchical, decentralised and distributed system, with millions of servers throughout the world combining to offer a service that performs like a single, integrated database. Each DNS server contains a small portion of the domain name to IP address mappings, contacting other DNS servers to resolve the mappings that it doesn’t store.

Many DNS service options are available, including ISP services, free services (such as those from OpenDNS and Google DNS), and premium paid-for services that can offer greater security and other features.

The AnyNet DNS service is available as part of our connectivity-managed service.

## About the AnyNet DNS service

The AnyNet DNS service is provided by highly available, fully redundant DNS servers in all our PoPs. The DNS service is always available to customer IoT devices with correctly configured APNs, no matter which mobile network they’re using.

For information about PoPs, see [About Eseye PoPs](../about-eseye-pops.md).

For information about AnyNet APNs, see [Current AnyNet APN list](../access-point-names/current-anynet-apn-list.md).

### Benefits of using the AnyNet DNS service

* **Security:** Using a private DNS service provides greater protection against protocol and DNS server vulnerabilities that might lead to cyber-attacks, such as denial of service attacks. Eseye can also deploy new security features or upgrades when required, without relying on third parties to do so.
* **Cybersecurity testing:** For customers using a third party company to perform cybersecurity testing, Eseye can route traffic through a testing server by using DNS rules to override the DNS resolution on specific IP addresses. For more information, see [About custom DNS entries](about-custom-dns-entries.md).
* **Performance:** Using a local DNS server reduces latency, as device DNS requests are not sent to remote DNS servers. DNS servers also cache results, resulting in better performance for DNS requests over time, as the servers become increasingly customised to the DNS requests they receive from IoT devices.
* **Service:** As part of our managed service, Eseye can respond quickly and flexibly to customer requirements. For example:
  * If devices have restricted internet access, they're guaranteed access to the AnyNet DNS service, whereas their restrictions might prevent them from accessing other services.
  * We can configure DNS filters to ensure that devices cannot access restricted internet content.
  * If required, we can create custom DNS entries for your IoT devices, which override the domain name values set with the domain registrar. For more information, see [About custom DNS entries](about-custom-dns-entries.md).
