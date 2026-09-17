# Measuring latency

Latency is the time data takes to travel from its source to its destination. The source can be an IoT device.

You can assess latency using a ping test, which measures the round-trip time for a message to travel from a source to its destination and be echoed back to the source.

Your deployment may require different latency measurements. You might measure latency from your device to:

* The [AnyNet PoP](../about-eseye-pops.md) that your device connects to.
* A destination cloud service, such as AWS or Azure.
* A server at your data centre or premises.

### Measuring latency to an AnyNet PoP

The AnyNet Ping service is available through the connectivity managed service. It lets IoT devices confirm connectivity to an AnyNet PoP. The service shows latency from the device across the cellular network to its connected PoP. For more information, see [About the AnyNet Ping service](about-the-anynet-ping-service.md).

### Measuring latency to a cloud service

Cloud services, such as AWS and Azure, provide tools to assess device connectivity and latency within a connected region. Available tools include:

| Cloud service | Latency test tool                                                                             |
| ------------- | --------------------------------------------------------------------------------------------- |
| AWS           | [ping.psa.fun](https://ping.psa.fun) and [www.awsspeedtest.com](https://www.awsspeedtest.com) |
| Azure         | [Azure latency test](https://www.azurespeed.com/Azure/Latency)                                |

Contact your cloud service provider for details of its latency test tools.

{% hint style="info" %}
If the test runs in a browser, you may need to insert the SIM into a device such as a cellular gateway and connect a laptop to run the test.
{% endhint %}

### Measuring latency to a customer location

Check whether your infrastructure or service provider offers a latency test tool or can provide the IP address of a suitable server that your devices can ping to determine latency.

### Ping test warning

Use a reliable test tool or ping server to understand the latency your devices experience.

Some public servers use anycast routing. For example, Google DNS uses the IP address `8.8.8.8`. With anycast, multiple servers in different locations share one IP address. This enables faster responses for end users. However, pinging an anycast IP address does not show how data is routed to its destination.

Do not ping an anycast IP address to test or compare latency values.
