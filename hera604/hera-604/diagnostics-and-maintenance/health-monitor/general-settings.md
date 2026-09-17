---
description: Configure system-wide monitoring and recovery behaviour.
---

# General settings

Configure system-wide monitoring and recovery behaviour.

<figure><img src="../../.gitbook/assets/Screenshot 2026-08-14 at 16.58.24.png" alt="Health Monitor general settings showing global monitoring and recovery options."><figcaption></figcaption></figure>

### Global settings

| Field                                  | Description                                                   |
| -------------------------------------- | ------------------------------------------------------------- |
| Interface prioritisation               | Allows Health Monitor to change WAN route priority.           |
| Metric shift                           | Amount applied to route metrics after a priority change.      |
| Time between system polls              | Interval between global Health Monitor checks.                |
| Restart WAN interfaces                 | Restarts interfaces after the configured failed system polls. |
| Reboot router                          | Reboots the router after the configured failed system polls.  |
| Method for choosing best WAN interface | Selects an interface using priority, response time, or both.  |

Confirm recovery thresholds with the deployment owner before enabling automatic router reboots.

### Actions for failed interface tests

Configure these recovery actions for repeated interface-test failures:

* Restart the interface.
* Restart a mobile interface with another profile.
* Reset the interface.

Set a consecutive-failure threshold for each enabled action.

### Actions for zero-packet interface tests

These settings apply when an interface reports no packets across consecutive tests. Configure restart, profile change, or reset actions only when required.

### Ping and DNS requests

| Field                            | Description                                                |
| -------------------------------- | ---------------------------------------------------------- |
| Ping timeout                     | Time to wait for a ping response.                          |
| Number unanswered before failure | Consecutive unanswered ping requests before a failed test. |
| DNS timeout                      | Time to wait for a DNS response.                           |
| Number unanswered before failure | Consecutive unanswered DNS requests before a failed test.  |

A single unanswered request does not necessarily indicate a failed connection.
