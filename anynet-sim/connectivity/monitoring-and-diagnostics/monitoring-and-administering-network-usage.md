# Monitoring and administering network usage

Use the Push API to stream raw network data to a web-based endpoint. Use this data to monitor and administer network usage.

You can subscribe to one or more network data stream services:

* NetFlow Raw Push
* RADIUS Authentication
* RADIUS Accounting

{% hint style="info" %}
To subscribe to Push API streams, contact your Account Manager.
{% endhint %}

<details>

<summary>About NetFlow Raw Push</summary>

NetFlow collects active IP traffic data as it flows through an interface, such as an IoT device. The data includes:

* Source and destination IP addresses and port numbers.
* The number of bytes and IP packets in the traffic flow.

Eseye captures real-time NetFlow data for every device across its data centres. Eseye processes this high-volume data through its cloud infrastructure using Amazon Kinesis. Eseye then enriches the data with valid SIM ID and IMSI information.

Eseye sends subscribed customers a constant, aggregated stream through the Push API. Each NetFlow payload links to a specific SIM in the customer's Infinity Classic account. To receive NetFlow messages, see the 8725 Push API Developer Guide (PDF).

Network administrators can analyse this data to understand traffic flow and volume across their SIM estate. This analysis can inform business decisions. For example, it can identify where to add hardware or retire unused devices.

</details>

<details>

<summary>About RADIUS Authentication</summary>

RADIUS authentication controls a user's access to network resources. The service verifies users before authorizing access to specific resources.

The user requests access from the Network Access Server (NAS). The NAS sends a RADIUS `Access-Request` to the RADIUS server. The Eseye RADIUS server returns one of these responses:

* **Access-Accept:** The user receives access to network resources. The RADIUS server checks that the user remains authorized to use the requested service. For example, a user might access the wireless network but not the VPN service. The authorization information is stored locally on the RADIUS server or in an external service, such as LDAP or Active Directory.
* **Access-Reject:** The user is denied access to network resources. Reasons include:
  * Failure to provide proof of identification.
  * An unknown or inactive user account.

Eseye captures real-time RADIUS authentication data for every device across its data centres. Eseye processes this high-volume data through its cloud infrastructure using Amazon Kinesis. Eseye then enriches the data with valid SIM ID and IMSI information.

Eseye sends subscribed customers a constant, aggregated stream through the Push API. Each RADIUS authentication payload links to a specific SIM in the customer's Infinity Classic account. To receive RADIUS authentication messages, see the 8725 Push API Developer Guide (PDF).

Use this data to track network and device usage and investigate network issues. For example, you can identify devices that remain disconnected for long periods or monitor authentication frequency.

</details>

<details>

<summary>About RADIUS Accounting</summary>

RADIUS accounting measures a RADIUS user's start and stop times and traffic usage. Use this information for billing and network monitoring.

RADIUS accounting has the following flow:

| Accounting type        | Description                                                                                                                                                                                                                                                                                                                                                                                |
| ---------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Accounting-Start**   | The accounting session starts after the user is authorized to access the RADIUS server. The NAS sends a RADIUS Accounting Request packet to the RADIUS server. This packet indicates that the user's network session has begun. It usually contains the user ID, point of access, network address, and a unique session identifier.                                                        |
| **Accounting-Interim** | Depending on session length, the NAS can send one or more Accounting-Interim updates. These updates contain the session duration and current data usage. The first update occurs 30 minutes after Accounting-Start.                                                                                                                                                                        |
| **Accounting-Stop**    | <p>The accounting session ends when the SIM disconnects from the network. Reasons include:<br><br>* The user signs off manually.<br>* The user is denied access because of role-level restrictions.<br>* A network error occurs, such as a port error.<br>* A session times out because of inactivity or the maximum session length.<br>* An administrator stops the session manually.</p> |

Eseye captures real-time RADIUS accounting data for every device across its data centres. Eseye processes this high-volume data through its cloud infrastructure using Amazon Kinesis. Eseye then enriches the data with valid SIM ID and IMSI information.

Eseye sends subscribed customers a constant, aggregated stream through the Push API. Each RADIUS accounting payload links to a specific SIM in the customer's Infinity Classic account. To receive RADIUS accounting messages, see the 8725 Push API Developer Guide (PDF).

Use this data to generate network usage and billing reports.

</details>
