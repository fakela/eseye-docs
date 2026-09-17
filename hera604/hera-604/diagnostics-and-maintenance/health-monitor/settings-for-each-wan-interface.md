---
description: Configure Health Monitor tests for each WAN interface.
---

# Settings for each WAN interface

Configure the tests performed on each available WAN interface.

<figure><img src="../../.gitbook/assets/Screenshot 2026-08-14 at 16.58.30.png" alt="Health Monitor WAN interface settings showing interface priority and connectivity tests."><figcaption></figcaption></figure>

| Field                        | Description                                                                              |
| ---------------------------- | ---------------------------------------------------------------------------------------- |
| Priority                     | Determines which interface is preferred when multiple WAN interfaces exist.              |
| Interface                    | Name of the WAN interface being monitored.                                               |
| Ping address                 | Address used for connectivity tests. Enter multiple addresses as a comma-separated list. |
| DNS lookup                   | Domain name resolved to check DNS operation.                                             |
| Time between interface tests | Interval between tests for this interface.                                               |
| Health monitoring            | Enables or disables monitoring for this interface.                                       |

Use **Promote** to increase an interface's priority. Use **Remove** only when an interface should no longer be monitored.

A new interface appears after you create its corresponding physical interface. Use values approved for the installation.
