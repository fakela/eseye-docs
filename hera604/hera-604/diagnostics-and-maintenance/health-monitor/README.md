---
description: Test WAN connectivity and define automatic recovery actions.
---

# Health monitor

The Health Monitor checks the router's WAN interfaces and can take recovery actions when connectivity tests repeatedly fail. Depending on the configuration, it can reprioritise WAN routes, restart or reset an interface, change the active mobile profile, or reboot the router.

Use thresholds that allow for short periods of latency or packet loss. Aggressive thresholds can cause unnecessary interface restarts or router reboots.

### Configure Health Monitor

* [General settings](general-settings.md) — Configure system-wide monitoring and recovery behaviour.
* [Settings for each WAN interface](settings-for-each-wan-interface.md) — Configure interface priorities and connectivity tests.
* [Overrides for each WAN interface](overrides-for-each-wan-interface.md) — Override global values for a specific interface.
