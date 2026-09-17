---
description: Investigate SIM network attachment events.
---

# Authentication metrics

Authentication records capture attempts by a SIM to authenticate onto the cellular network. This is the first thing that has to succeed before anything else can happen, so it is usually the first place to look when a device is silent.

> **Question answered:** Did the device successfully attach to the network?

### What the records show

* Initial network attach attempts.
* Re-attachments following coverage loss.
* Network or roaming changes.
* Successful and rejected authentication events.

Every attempt is captured, including the failures, you get the shape of the behaviour rather than just its outcome. A device that authenticates cleanly once looks very different from one that cycles through accepts and rejects all day, even though both may appear connected at a given moment.

### Common uses

* **Identifying flapping devices:** Repeated accept and reject cycles are visible directly in the record stream, which makes it possible to find unstable devices across an estate rather than one at a time.
* **Diagnosing provisioning, roaming and APN issues:** Rejection patterns and network changes narrow down whether the problem sits with the SIM configuration, the device, or the network it is trying to use.
* **Correlating attach failures with later usage or session data:** An authentication record on its own tells you a device tried to connect when joined to [Accounting Metrics](accounting-metrics.md), it tells you whether that attempt turned into a usable session.

### Interpretation

Authentication data describes whether the device reached the network successfully. It does not show how long the resulting session remained active or where traffic travelled. Accounting and traffic flow records provide that later-stage context.
