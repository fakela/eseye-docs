---
description: Diagnose common Hera 600 connectivity and management issues.
---

# Data Logging & Performance

Open **Diagnostics & Maintenance > Data Logging > Settings** to control periodic collection of performance data.

<figure><img src="../../.gitbook/assets/Screenshot 2026-08-14 at 17.00.08.png" alt=""><figcaption></figcaption></figure>

| Field      | Value shown   | Description                                                                                    |
| ---------- | ------------- | ---------------------------------------------------------------------------------------------- |
| Logging    | `Enabled`     | Enables or disables data logging.                                                              |
| Log period | `900` seconds | Time between data-capture events. Shorter periods provide more detail but create more records. |

#### Performance

Open **Diagnostics & Maintenance > Data Logging > Performance** to view logged mobile signal and traffic data over time.

<figure><img src="../../.gitbook/assets/Screenshot 2026-08-14 at 17.00.13.png" alt=""><figcaption></figcaption></figure>



Use the date and time controls to select the period displayed. The graphs show:

* Mobile signal strength over time, measured in dBm.
* Mobile data sent and received over time.
* The mobile network operator associated with the selected period.

Hover over a graph point to view its exact value and timestamp. Hover over the network-operator bar to view the operator name. Use the data to identify recurring loss of signal, changes of mobile network, or unusual traffic patterns; compare any event with router logs and site activity before drawing a conclusion.
