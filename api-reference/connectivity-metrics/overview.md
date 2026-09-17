---
description: Deliver connectivity telemetry to analytics and monitoring systems.
tags:
  - tag: paid-add-on
    primary: true
---

# Overview

Connectivity Metrics provides near real-time visibility into how IoT devices connect, communicate and consume data across cellular networks.

The service delivers structured connectivity data derived from network authentication events, session accounting records and traffic flow metadata. This data helps you understand whether devices can connect, how long they remain connected, how much data they consume and where their traffic flows.

Connectivity Metrics is designed for organisations that want to ingest raw connectivity telemetry into their own data lakes, monitoring tools, business intelligence systems, security platforms or other analytics environments.

> **Delivery:** Connectivity Metrics is delivered as a secure file-based data feed through SFTP. It is not a traditional REST API

### When to use Connectivity Metrics

Connectivity Metrics provides more detailed information than standard portal dashboards. It is suitable when you need to investigate individual device behaviour or analyse connectivity patterns across a large IoT estate.

The service can help you:

* Investigate why devices fail to attach or repeatedly reconnect.
* Correlate data usage with network sessions and roaming behaviour.
* Understand where connected devices send traffic.
* Compare connectivity behaviour across countries and operator networks.
* Identify unusual session durations, traffic volumes or communication patterns.
* Analyse device connectivity centrally across a large estate.
* Send connectivity data to monitoring, analytics or security platforms.

## Use cases

Connectivity Metrics supports operational monitoring, large-scale analytics, advanced troubleshooting and security validation.

* **IoT operations monitoring:** Track how devices authenticate, maintain sessions and consume data across a distributed estate.
* **Fleet analytics:** Analyse consistent connectivity telemetry across devices, countries and operator networks.
* **Advanced troubleshooting:** Investigate problems that cannot be explained by summary dashboards alone.
* **Cost and usage analysis:** Compare session and usage behaviour for internal reporting, billing reconciliation or anomaly detection.
* **Security and governance:** Review traffic destinations and validate whether devices communicate only with expected services.
* **Enterprise data integration:** Feed connectivity telemetry into SIEM, SOC, monitoring, business intelligence or data lake environments.

### Available datasets

Connectivity Metrics consists of three complementary datasets. Each dataset describes a different stage of a device’s connectivity journey.

| Dataset                | What it describes                                              | Operational question                                             |
| ---------------------- | -------------------------------------------------------------- | ---------------------------------------------------------------- |
| Authentication metrics | Attempts by a SIM to authenticate onto the cellular network    | Did the device successfully attach to the network?               |
| Accounting metrics     | Network sessions created after successful authentication       | How long was the device connected, and how much data did it use? |
| Traffic flow metrics   | Traffic behaviour after a network session has been established | Where did the device send traffic, and how much?                 |

### How datasets work together

The three datasets can be correlated using the IMSI and timestamp to create a time-aligned view of device connectivity.

A typical investigation follows this sequence:

1. Review authentication records to confirm whether the device attached successfully.
2. Review accounting records to determine whether a session was established, how long it remained active and how much data was transferred.
3. Review traffic flow records to identify where the device communicated during the session.

Together, the datasets provide a more complete connectivity narrative than any individual dataset can provide on its own.

### Typical use cases

Use Connectivity Metrics for:

* Enterprise IoT operations monitoring and fleet analytics.
* Advanced troubleshooting beyond portal views.
* Compliance, governance, and security validation.
* Feeding data into SIEM, SOC, and data lake environments.

Connectivity Metrics shows how devices authenticate, connect, and communicate across networks and geographies.
