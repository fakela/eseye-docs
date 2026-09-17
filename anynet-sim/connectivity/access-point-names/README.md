# Access Point Names

An Access Point Name (APN) defines the network path between a mobile network and an IP network (the public internet or a private network, for example, Eseye's [MPLS](https://app.gitbook.com/s/hPiB0Z0YdVhl1D9teuS7/) network). Each Eseye APN consists of:

* Pre-existing configurations between Eseye and the operator to enable a connection between the networks
* A RADIUS server and billing function
* The DNS – For more information, see [Understanding the AnyNet Domain Name Service (DNS)](../ip-addressing-and-routing/understanding-the-anynet-domain-name-service-dns.md).

Any device that connects to an IP network using a mobile network must specify an APN as part of their configuration. The APN assigns an IP address to a device, and routes data between the device and its destination over the mobile network and internet.

Your IoT devices must always use the same AnyNet APN, regardless of which mobile network they use to send data.

{% hint style="warning" %}
Eseye may preconfigure multiple APNs to link to an MNO. Always use the APN specified in your contract.
{% endhint %}

### About public and private APNs <a href="#aboutpublicandprivateapns" id="aboutpublicandprivateapns"></a>

Mobile Network Operators (MNOs) provide public APNs for their customers to connect to. Enterprises that need better security or configuration options can set up private APNs for their customers or internal use.

Public APNs provide basic internet access, mainly for consumer devices to access commonly-used apps and websites. The services are designed based on typical levels of consumer use. Operators often apply mechanisms such as network throttling or rate limiting to manage overloading. Public APNs offer limited flexibility for configuring or differentiating services that enterprises might need for critical business systems or want to offer their customers.

With private APNs, such as the AnyNet APNs, enterprises can offer services that meet specific requirements. For example, IoT devices can have very different connectivity needs to consumer mobile phones.

#### Advantages of using AnyNet private APNs <a href="#eseyes" id="eseyes"></a>

Eseye provides a number of private APNs to meet the needs of different IoT deployments. All AnyNet APNs:

* Provide the same services at all PoPs to all IoT devices, regardless of where the devices are located or which mobile network they are connected to. Using the same APN across all devices simplifies device configuration.
* Use the same subnet configurations, IP address allocations and routing rules. With public APNs, a device is allocated a different IP address whenever it connects, which increases the complexity of managing devices and diagnosing connectivity issues. AnyNet APNs have pre-allocated IP addresses, so devices are assigned the same IP address whenever they connect on a particular network.
* Authenticate devices to ensure only authorised devices connect to Eseye PoPs.
* Manage and record device data sessions, activity and network usage, logging data for use in device management and monitoring, and billing. Our network management tools enable you to monitor and manage device connections. Our technical consultants have access to additional tools and can provide support to resolve complex connectivity issues.
*   Route data according to configured security options, such as NAT, VPNs, and ACL rules.

    For more information, see [About Network Address Translation (NAT)](../ip-addressing-and-routing/about-network-address-translation-nat.md), [Configuring AnyNet VPNs](../security/understanding-vpns.md#configuring-anynet-vpns), and [About the AnyNet ACL service](../ip-addressing-and-routing/routing-non-vpn-network-traffic.md#about-the-anynet-acl-service).
* Prevent SIM-SIM traffic, which has been observed on consumer and non-specialist IoT APNs, and creates a major security risk.

{% hint style="info" %}
See [Current AnyNet APN list](current-anynet-apn-list.md) for a list of available private AnyNet APNs.

For a list of public IP addresses to add to your company firewall allowed list, see [Egress IP addresses](../ip-addressing-and-routing/egress-ip-addresses.md).
{% endhint %}

#### About custom APNs

Some customers want to use their own domain name as their APN name. Using a custom APN (also known as a 'vanity APN') is not recommended unless it is essential. The disadvantages are:

* Expense: we need to make arrangements for custom APNs with each MNO, adding complexity and cost to customer onboarding.
* Restrictions: some MNOs limit the number of custom APNs we can configure with them. If we can't configure the custom APN with an MNO, the customer's devices can't use the m
