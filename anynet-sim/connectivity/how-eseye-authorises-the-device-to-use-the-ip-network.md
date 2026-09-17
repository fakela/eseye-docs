# How Eseye authorises the device to use the IP network

Eseye uses RADIUS authentication to control access to the Eseye network. The device is first verified as belonging to a customer and then either authorised to access specific resources (Access-Accept), or denied access (Access-Reject).

If the SIM is permitted access to the Eseye network, then Eseye assigns an IP address to the device, using the device details in the connection request to deliver the IP address to the correct device. These device details include the SIM and modem unique identifiers and the APN. For more information, see [Configuring a device to access the correct network](https://eseye-v3.gitbook.io/eseye-docs/L25WdLp1CEZBZ0aOlPAR/connectivity/connection-methods#configuring-a-device-to-access-the-correct-network).

{% hint style="info" %}
Customers can request PCAP Explorer to track device activity on the network. For more information, see [About network traffic analysis using PCAP Explorer](https://eseye-v3.gitbook.io/eseye-docs/L25WdLp1CEZBZ0aOlPAR/connectivity/monitoring-and-diagnostics/about-network-traffic-analysis-using-pcap-explorer).
{% endhint %}
