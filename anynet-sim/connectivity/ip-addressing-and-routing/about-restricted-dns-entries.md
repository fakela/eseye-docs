# About restricted DNS entries

## About restricted DNS entries <a href="#aboutrestricteddnsentries" id="aboutrestricteddnsentries"></a>

Some customers require restricted internet access for their devices, to ensure that the devices cannot access the internet beyond a limited set of trusted IP addresses.

Eseye can restrict internet access using two separate filters:

* **Allowed List** – a customer-defined list of permitted domains or IP addresses. Only queries for the permitted domains and IP addresses are resolved. All other traffic is dropped.
* **Blocked List** – an Eseye-defined list of harmful domains or IP addresses. If a domain is on the Blocked List, Eseye will not resolve the corresponding IP addresses for that domain. If an IP address is on the Blocked List, Eseye will drop all traffic from that address.

Having both lists ensures that compromised devices cannot access malicious web content that might be used to gain control of the device.

{% hint style="info" %}
The lists can use domain names or fully qualified domain names (FQDNs).
{% endhint %}

The examples below show scenarios in which this customised DNS service is required.

#### Example 1 – router sending debug data to router manufacturer

If the router manufacturer URL or FQDN is not on the Allowed List, the request is dropped. We recommend you prevent your router from performing these lookups within its normal operation.

#### Example 2 – domains permitted but forwarded to other servers for resolution

Certain domains are permitted. However, the request is forwarded to designated DNS servers to ultimately resolve and return the response.

{% hint style="info" %}
Contact your Account Manager if you have specific DNS requirements.
{% endhint %}
