---
description: Analyse network sessions and data usage.
---

# Accounting metrics

Accounting metrics describe network sessions after a device has authenticated successfully. Where authentication records tell you whether a device got onto the network, accounting records tell you what happened during the time it stayed there.

> **Question answered:** How long was the device connected, and how much data did it use?

### What the records show

* Session start and end times.
* Session duration.
* Uplink and downlink data usage.
* Serving network context, where available.

Uplink and downlink are reported separately, which matters for IoT estates where the traffic profile is usually asymmetric and a change in that balance is often the first sign that something on the device has changed.

### Common uses

* **Per-SIM and per-fleet usage tracking:** Usage can be rolled up however your estate is organised, by device type, by customer, by region, without depending on how an operator chooses to group it.
* **Internal billing and cost reconciliation:** Session-level records give you a basis for allocating cost internally and for checking it against what you are invoiced.
* **Detecting abnormal session duration or usage patterns:** Sessions that run far longer than expected, or consume far more than their peers, stand out once you have the full population to compare against.
* **Verifying roaming and network behaviour:** Serving network context, where available, shows which network a session actually ran on rather than which one you expected.

### Interpretation

Accounting data confirms what happened during a network session. Pair it with authentication data to understand how the session started and with traffic flow data to understand where communication occurred.
