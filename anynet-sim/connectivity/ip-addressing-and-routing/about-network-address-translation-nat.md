# About Network Address Translation (NAT)

Eseye uses Network Address Translation (NAT) to map the many private IP addresses within a [secure subnet](about-secure-subnets.md) to a single public IP address and port number for communication across the internet, whether through a VPN or direct access to the internet.

APN routers at each Eseye PoP manage how data is transferred from a device, as well as ensure that any responses to that data find their way back to the correct device. Any data that is not part of a session created from a customer device is dropped, ensuring that unsolicited data cannot route directly to the devices.

{% hint style="info" %}
Devices whose IP addresses are processed using NAT must initiate communication so that the APN routers can set up the reverse route.
{% endhint %}

### Advantages of using NAT <a href="#advantagesofusingnat" id="advantagesofusingnat"></a>

We use NAT for several reasons:

* Increased security: Private IP addresses ensure that customer devices remain unrouteable from the internet, thereby preventing unauthorised access to those devices. This means that at all times, each device must initiate communication with other systems and users, which is in keeping with IoT best practices. For more information, see [Configuring devices to initiate communication](../device-configuration-best-practices.md).
*   Cost and scalability: IPv4 address exhaustion means that obtaining public IP addresses in large numbers is expensive, difficult, and restricts scalability. Using NAT ensures that the number of devices within a customer subnet can easily grow, and the cost is minimal.

    For more information, see [IPv4 address exhaustion](https://en.wikipedia.org/wiki/IPv4_address_exhaustion).
* Flexibility and resilience: Using NAT ensures that a device can connect on any available mobile network. It also ensures continued connectivity in the event of an Eseye PoP outage. For more information, see [About Eseye PoPs](../about-eseye-pops.md).

### Alternative to NAT for egress onto the internet <a href="#alternativetonatforegressontotheinternet" id="alternativetonatforegressontotheinternet"></a>

If a device must use a static public IP address, it is restricted to a single network that connects to a single PoP. It cannot benefit from Eseye’s network switching to ensure high levels of connectivity. A static public IP address also means that the device cannot benefit from PoP failover in the event of an outage. For more information, see [Assigning static public IP addresses to devices](./#assigning-static-public-ip-addresses-to-devices).

<br>
