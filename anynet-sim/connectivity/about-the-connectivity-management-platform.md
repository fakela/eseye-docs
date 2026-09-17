# About the Connectivity Management Platform

With access to over 700 mobile networks across the world, the AnyNet managed connectivity solution provides global coverage for a wide range of IoT devices. AnyNet SIMs are pre-loaded with multiple bootstrap profiles, each of which can contain multiple IMSIs for roaming. SIMs can connect out-of-the-box wherever they are, switching to different networks to maintain connectivity, for example, if they move location. Eseye can load new profiles to devices for localisation (avoiding permanent roaming) or to achieve better service.

This sophisticated network-switching capability maximises the opportunity for achieving high levels of connectivity. It requires a powerful application – the Connectivity Management Platform – to manage the complexity of devices and networks, ensuring the best outcomes for all deployments.

The AnyNet Connectivity Management Platform (CMP) is at the heart of the AnyNet solution. Integrated with the AnyNet SIMs, the CMP ensures that devices have optimum connectivity within any legislative, commercial, and service constraints that apply.

The CMP provides the environment for secure connections and data transfer between devices and back-end systems. The metrics it records about connections and data flows are used for monitoring performance, resolving issues, triggering alerts, and generating accurate billing records.

## Profiles and communications

The CMP manages the network profiles. SIMs are pre-loaded with bootstrap profiles and the CMP can download additional profiles over-the-air (OTA). For example, new profiles are downloaded to switch a device to a local network to avoid roaming restrictions, or to use a better or most cost-effective service in a particular location.

The CMP manages the interconnects to the Mobile Network Operator (MNO) networks. When a SIM is provisioned on a network, the CMP notifies the relevant MNO of the services that need to be activated for that SIM.

A sophisticated rules engine within the CMP determines the conditions under which to steer a device to roam on another network, or switch the IMSI on a device. Rules are configured with parameters that control when and how often an action should be attempted. The CMP operates GSMA-compliant systems for steering and switching profiles.

A messaging module within the CMP enables SMS messages to be sent to and from devices. This module has two uses:

* Customers can use it to send application messages to their devices
* Eseye uses it to deliver encrypted OTA instructions to SIMs to improve connectivity performance

The CMP supports Block Lists and Allow Lists to ensure unauthorised messages are not sent to the device.

## Connections and metrics

As devices connect to the AnyNet core network, the CMP authenticates them to ensure that only legitimate devices can connect and assigns them their pre-allocated IP addresses.

The CMP records comprehensive device connection and data flow metrics. This data is used for monitoring performance, and investigating connectivity, operational or device issues. It can trigger pre-configured alerts to notify customers of threshold breaches or unexpected behaviour.

Device data can be aggregated by estate for a customer or for all devices for CMP analysis. Visibility on global traffic flows, device connections across different network operators, and throughput metrics can highlight patterns, problems, and anomalies with network or estate performance. The CMP uses this analysis to determine when devices should switch networks.

Individual device metrics can be analysed to investigate issues with a device. The CMP records a variety of data for each device, including network connections, last location, events (such as when an SMS was sent or received), and data sessions and usage. This data can highlight trends, such a device constantly switching networks or periods of unexpectedly high (or low) data transfer.

## Billing

The AnyNet solution provides customers with a single global invoice for their IoT estate, simplifying financial management and administration.

The metrics recorded by the CMP feed into the billing engine to create accurate, detailed billing records for each device. Billing data is calculated using the locations, networks, and services that each device has used.

## User facilities

The CMP provides a range of tools for users to manage their IoT estates. These tools can be accessed from AnyNet web-based interfaces or integrated with customer systems using AnyNet APIs.

The tools include:

* Managing users and accounts
* Ordering and activating SIMs
* Configuring alerts to trigger on different threshold events (such as data usage or overage values) and take different actions (such as notifying users or suspending a SIM)
* Viewing the connection and data flow metrics for an individual SIM or aggregated for the estate
* Configuring ad hoc or scheduled reports for areas such as finance, data usage, and lifecycle
* Managing SIMs (suspending, terminating, re-activating)

## Service and support

The AnyNet 24\*7 support service complements the CMP and self-service facilities. Different levels of support are available, so customers can choose the level they need.

Experienced technical staff have access to advanced CMP tools to resolve issues and ensure that each customer’s devices maintain the high levels of connectivity that they need for successful IoT deployments.
