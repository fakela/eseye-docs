# Network Reliability

## Problem

Devices experience unreliable network connectivity. This may manifest itself in one of following ways:

* Networking tools show that a device is continually requesting authentication but fails to establish any data sessions. Log files show the device registration is denied. If the device is moved to a different location, it can register and connect without issue. This may occur for a new device or a device that has previously had no connection issues.
* A device connects briefly (for around 30 seconds) but then is disconnected and can't re-connect for a lengthy period (around 20 minutes). This cycle can be repeated indefinitely. If the carrier for this network can be avoided (for example, using a Blocklist), the device can connect successfully with another carrier.

{% hint style="info" %}
Repeated registration failures can indicate carrier steering or network restrictions.
{% endhint %}

## Causes

Unreliable network connections are usually caused by one of the following issues.

### Steering of roaming

Some Mobile Network Operators (MNOs) calculate their roaming fees based on consumer mobile phones. They assume that they will get almost all the connections onto a single, low-cost network. To ensure their profit margins, they only permit a small percentage of devices to use other, more expensive networks. [Steering of roaming](https://eseye-v3.gitbook.io/eseye-docs/L25WdLp1CEZBZ0aOlPAR/anynet-sims/how-anynet-sims-work/understanding-roaming#steering-of-roaming) is the method that carriers use to move devices onto their preferred networks. It can severely impact the connectivity of IoT devices.

Carriers usually operate Steering of Roaming in one of the following ways:

* Permit a device to register on the network only once every five attempts
* Regularly disconnect devices that aren't connected on the preferred network

Consumers experiencing connection problems with their mobile phones will often move, persist with connection attempts or issue a manual network selection request. One of these methods will work eventually, even if the consumer has to make repeated connection attempts.

IoT devices, however, experience poor network availability, either failing to connect or experiencing regular disconnections once they have connected. The connection methods that work for consumers don't work for IoT devices.

### Legislative and commercial restrictions

Legislative and commercial landscapes are changing, preventing devices from roaming easily, either on a temporary or permanent basis.

### Device design and performance

The design of a device can affect its connectivity performance. In particular, creating a convoluted connection methodology in order to circumvent carrier operations, such as steering of roaming, can have a detrimental impact on devices, making the firmware unmanageable and unreliable.

## Solution

The solution is to use a high quality connectivity provider with the ability to ensure optimum levels of device connectivity. For example, the provider should:

* Use high performance tools to manage devices, steering them to different networks if they're experiencing connectivity problems.
* [Localise devices](https://eseye-v3.gitbook.io/eseye-docs/L25WdLp1CEZBZ0aOlPAR/anynet-sims/how-anynet-sims-work/understanding-localisation) to mitigate legislative and commercial restrictions. This is the process of downloading new profiles to SIMs so they can connect to a local network wherever they are located.
* Work with customers to understand devices and advise on how to ensure they have optimum connectivity.
* Not operate steering of roaming to protect profit margins.

{% hint style="info" %}
The [AnyNet Connectivity Management Platform](https://eseye-v3.gitbook.io/eseye-docs/L25WdLp1CEZBZ0aOlPAR/connectivity/about-the-connectivity-management-platform) steers devices to networks that offer the best connectivity. AnyNet SIMs include multiple IMSIs, which allow devices to switch network profiles or routing paths.
{% endhint %}
