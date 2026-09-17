---
description: Analyse device traffic metadata with NetFlow records.
---

# Traffic flow (NetFlow) metrics

Traffic flow metrics describe device communication after a network session has been established.

> **Question answered:** Where did the device send traffic, and how much?

### What the records show

* Source and destination IP addresses.
* Ports and protocols.
* Traffic volumes and packet counts.
* High-level application classification, where available.

> **Privacy boundary:** Traffic flow data contains metadata only. It does not include packet payloads.

### Metadata only

NetFlow records contain metadata about traffic. They do not contain packet payloads, and the service does not perform deep application-layer inspection. You can see that a device sent a given volume of traffic to a given endpoint over a given protocol. You cannot see the contents of that traffic, by design. Scope and boundaries covers this in full.

### Common uses

* **Understanding traffic destinations:** Seeing the actual endpoints a fleet talks to often surfaces services nobody remembered were still in the picture.
* **Identifying unexpected or unauthorised endpoints:** Traffic to an endpoint outside your approved list is visible without needing anything installed on the device.
* **Traffic volume and behaviour analysis:** Volumes and packet counts per flow show how consumption is distributed across destinations, which is usually more useful than a single per-SIM total.
* **Security posture validation:** The practical version of the question is simple: are these devices only talking to the services they are supposed to talk to? NetFlow data answers it directly, which is why this dataset commonly feeds SIEM and SOC environment
