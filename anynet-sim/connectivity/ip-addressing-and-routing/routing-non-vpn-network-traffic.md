# Routing non-VPN network traffic

Some customers may choose to route only some, or no network traffic through [VPN](https://app.gitbook.com/o/ewPVTh5Hmb64cZjruxy6/s/hPiB0Z0YdVhl1D9teuS7/) tunnels. For example, they may not require a VPN, or may have some data for transferring to destinations other than their central system, such as partner systems.

The AnyNet solution provides two options for routing non-VPN traffic:

* If full internet access is allowed, the traffic is permitted to egress onto the internet for onward routing to its destination, with no restrictions.
* With restricted internet access, the traffic is checked against a customer-supplied Access Control List (ACL) and discarded unless the destination matches one of the destinations in the list.

### About the AnyNet ACL service <a href="#about" id="about"></a>

Access Control List (ACL) rules are configured on the Eseye PoP and customer firewalls to control non-VPN traffic from devices:

* Rules on Eseye PoP firewalls determine whether incoming non-VPN traffic from devices is allowed to egress onto the internet

{% hint style="info" %}
If you want to use ACL rules for this, Eseye must configure secure subnets for your devices. You must supply the configuration information for the rules, using the [AnyNet Subnet and Security Options Order Form (XLS, download)](https://app.gitbook.com/o/ewPVTh5Hmb64cZjruxy6/s/X0cODzoDlWNEI5nvG9sX/).

_Contact your Account Manager if you want to configure ACL rules at the Eseye PoPs._
{% endhint %}

* Rules on customer firewalls permit non-VPN traffic received from an Eseye PoP to route to its destination

{% hint style="info" %}
If you want to use ACL rules for this, you must add the Eseye PoP public IP addresses or address ranges to your rules to ensure that device traffic can route to its destination. For more information, see [Egress IP addresses](egress-ip-addresses.md).

If your devices have static (fixed) [IP addresses](./#assigning-static-public-ip-addresses-to-devices), you must also add these addresses to your ACL rules.
{% endhint %}
