---
description: Override Health Monitor values for a specific WAN interface.
---

# Overrides for each WAN interface

Replace global Health Monitor values for a specific WAN interface.

<figure><img src="../../.gitbook/assets/Screenshot 2026-08-14 at 16.58.36.png" alt="Health Monitor WAN interface overrides showing per-interface recovery and timeout settings."><figcaption></figcaption></figure>

Each interface can override:

* Recovery actions and thresholds for failed interface tests.
* Recovery actions and thresholds for zero-packet tests.
* Ping and DNS timeouts and unanswered-request thresholds.

Fields showing **Default** inherit the corresponding value from **General settings**. Add an override only when an interface needs different behaviour.
