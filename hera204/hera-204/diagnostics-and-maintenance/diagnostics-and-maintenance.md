---
hidden: true
---

# Diagnostics & Maintenance

## Health Monitor

The Health Monitor continually monitors the network connectivity and system state of each Hera WAN interface. If the network performance changes, the Health Monitor can:

* Seamlessly switch WAN interfaces to maintain connectivity
* Stop and restart the affected WAN interface
* Reset the cellular connection
* Change to a different SIM profile
* Monitor status files or execute test applications (for example, the Health Monitor can activate Shell scripts)
* Perform a system reboot if required

### General settings – Global Health Monitor

**Health Monitor Architecture**

The Health Monitor system on the HERA Router operates across multiple levels to ensure robust data connectivity monitoring and recovery.

**Global Health Monitor**

* Operates at the highest level of the monitoring hierarchy.
* Executes connectivity tests at configurable periodic intervals.
* Serves as the central controller for overall health status.
* Global monitor runs across all interfaces when multiple interfaces are configured.
* Global actions are only performed if all interfaces are down.

| # | Field name                                 | Value                              | Explanation                                                                                                                                                                                    |
| - | ------------------------------------------ | ---------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1 | Interface Prioritization                   | Enabled/Disabled                   | Used for devices with multiple WAN Interfaces – Not relevant here                                                                                                                              |
| 2 | - with this value of metric shift          | Number between 1-9                 | Used to switch Route Priority when multiple Default Routes are used. The effect is that the Secondary Route will temporarily become the Primary Route during the detected connectivity outage. |
| 3 | Time (in seconds) between system polls     | Value in seconds                   | Determines the periodic frequency of the health monitor connectivity test                                                                                                                      |
| 4 | Restart WAN interface                      | Enabled/Disabled                   | Determines the action to take when a health monitor failure is detected. This action forces the WAN interface to be administratively forced 'down' then 'up'.                                  |
| 5 | - after this number of failed system polls | Number between 1-10                | Determines how many consecutive failed polls are required before the WAN interface is restarted.                                                                                               |
| 6 | Reboot Router                              | Enabled/Disabled                   | Determines the action to take when a health monitor failure is detected. This action reboots the Router.                                                                                       |
| 7 | - after this number of failed system polls | Number between 1-10                | Determines how many consecutive failed polls are required before the router is rebooted.                                                                                                       |
| 8 | Method for choosing the best WAN interface | Priority, Round Trip Time or both. | Priority will take actions depending on interface failures. Round Trip Time will take link quality into account.                                                                               |

### General Settings – Interface Monitors

**Interface-Level Health Monitors**

* One or more lower-level monitors can be configured for each active WAN interface.
* Each monitor runs independently and has its own interval settings.
* These monitors provide granular visibility and control over individual WAN connections.

**1) For interface tests that fail.**

These actions will be performed for each interface that fails.

| # | Field name                                     | Value               | Explanation                                                                                                                                      |
| - | ---------------------------------------------- | ------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------ |
| 1 | Restart Interface                              | Enabled/Disabled    | Determines the action to take when an interface test fails. This action forces the WAN interface to be administratively forced 'down' then 'up'. |
| 2 | - after this number of failed interface tests. | Number between 1-9  | Number of consecutive failed tests required to initiate action.                                                                                  |
| 3 | Restart interface with a new profile           | Enabled/Disabled    | Determines the action to take when an interface test fails. This action switches to the next available cellular profile.                         |
| 4 | - after this number of failed system polls     | Number between 1-10 | Determines how many consecutive failed polls are required before a new profile is selected.                                                      |
| 5 | Reset Interface                                | Enabled/Disabled    | Determines the action to take when an interface test fails. This action resets the WAN interface.                                                |
| 6 | - after this number of failed system polls     | Number between 1-10 | Determines how many consecutive failed polls are required before the WAN interface is reset.                                                     |

**2) For interface tests that receive zero packets.**

In addition to ping testing, the interfaces are also monitored for the presence of data packets. If no data packets are determined on a monitored interface for consecutive polls, then a failure is determined.

| # | Field name                                          | Value               | Explanation                                                                                                                                                 |
| - | --------------------------------------------------- | ------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1 | Restart Interface                                   | Enabled/Disabled    | Determines the action to take when an interface receives zero packets. This action forces the WAN interface to be administratively forced 'down' then 'up'. |
| 2 | - after this number of zero packet interface tests. | Number between 1-9  | Number of consecutive failed tests required to initiate action.                                                                                             |
| 3 | Restart interface with a new profile                | Enabled/Disabled    | Determines the action to take when an interface receives zero packets. This action switches to the next available cellular profile.                         |
| 4 | - after this number of zero packet interface tests  | Number between 1-10 | Determines how many consecutive zero packet tests are required before a new profile is selected.                                                            |
| 5 | Reset Interface                                     | Enabled/Disabled    | Determines the action to take when an interface test receives zero packets. This action resets the WAN interface.                                           |
| 6 | - after this number of zero packet interface tests. | Number between 1-10 | Determines how many consecutive zero packet interface tests are required before the WAN interface is reset.                                                 |

### General Settings Miscellaneous

An interface or global health monitor failure is determined by the below settings. A single unanswered ping is not necessarily deemed a failure at the health monitor level, as congestion or latency could cause a dropped/unanswered ping during a normal data session.

| # | Field name                          | Value            | Explanation                                                                                                      |
| - | ----------------------------------- | ---------------- | ---------------------------------------------------------------------------------------------------------------- |
| 1 | Ping Requests - Timeout             | Value in seconds | Determines how long to wait before an unreturned ping response is deemed a ping fail                             |
| 2 | Number of unanswered before failure | Default 3        | Determines how many consecutive unreturned pings are required to be determined as a failed interface test.       |
| 3 | DNS Requests - Timeout              | Value in seconds | Determines how long to wait before an unreturned dns response is deemed a fail.                                  |
| 4 | Number of unanswered before failure | —                | Determines how many consecutive unreturned dns requests are required to be determined as a failed interface test |

### Settings for each WAN interface

Additional parameters to configure each independent health monitor interface.

| # | Field name                   | Value                                | Explanation                                                                                                                                                                                            |
| - | ---------------------------- | ------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| 1 | Priority                     | Integer                              | When multiple interfaces are present, the priority value determines which interface should be used for the primary default route.                                                                      |
| 2 | Interface                    | cellpri/ethwan                       | The interface name that the health monitor test is running on.                                                                                                                                         |
| 3 | Ping Address                 | Comma separated list of IP addresses | This is the address of the ping server. If a list is present, then the health monitor will always try the first server in the list. The 2nd server is only tried if the first server does not respond. |
| 4 | DNS Lookup                   | Domain Name                          | The DNS name to be looked up to determine DNS is working correctly.                                                                                                                                    |
| 5 | Time between interface tests | Time in seconds                      | This is the periodic interval between interface polls. Typically, an interface test runs more frequently than a global poll.                                                                           |
| 6 | Enabled                      | Enabled/Disabled                     | Enable or Disable the interface Health Monitor.                                                                                                                                                        |

Note: New interfaces will only appear in this section when an accompanying physical interface is created.

### Overrides for each WAN interface

These are used in scenarios where multiple interfaces are used. It allows for each interface to be configured independently from each other. Use the General settings sections above for reference.

## File Management

### Configuration backup

Allows the user to back up the current running configuration of the Hera 204 to their computer. Click the 'Backup' button, then the configuration file will be downloaded to the default Downloads folder in the browser or file explorer in tar.gz format.

### Configuration Upload

Allows the user to upload a configuration file onto the Hera 204. After clicking the 'Upload' button, then 'Choose File' and select a configuration file from a file browser or explorer window (tar.gz files should be used).

After selecting a configuration file, click 'OK' to apply the configuration to the Hera 204.

When the configuration file is loaded, a success prompt will appear. There are 2 options to 1) Reboot now, or 2) Reboot later to apply the configuration file when most convenient.

### Software upload

Allows the user to upload a software package to the Hera 204 router. After clicking the 'Upload', then 'Choose File' button, select a software file from a file browser or explorer window (tar.gz files should be used).

After selecting the file, the Hera 204 will install the software file. If successful, the Hera 204 will reboot and apply the software file.

## System Settings

### Network time protocol (NTP)

NTP configuration enables setup and synchronization of the router poll times.

| # | Field name                              | Description                                                                    |
| - | --------------------------------------- | ------------------------------------------------------------------------------ |
| 1 | Local NTP server                        | Enables / Disables the local NTP server. This does not disable the NTP client. |
| 2 | NTP servers                             | Lists configured NTP servers that the NTP client will synchronise with         |
| 3 | Use ipv4 for NTP server name resolution | Yes/No – selects whether ipv6 and ipv4 can be used, or just ipv4               |
| 4 | Minimum poll time                       | Minimum poll time                                                              |
| 5 | Maximum poll time                       | Maximum poll time                                                              |

Note: under NTP servers, if all servers are removed then the NTP client will be disabled.

## User Management

### Administrator password

Set a new administrator password. The new password should be at least 10 characters. Click the 'Save' button to save the settings to the router.

## Restart

### Reboot

Clicking the 'Reboot' button will bring up a confirmation dialog box. Click 'Yes' to confirm and reboot the Hera 204 router.

### Factory reset

Clicking the 'Reset' button will bring up a confirmation dialog box. Click 'Yes' to confirm and factory reset the Hera 204 router.

## Data Logging

Real-time graphs show how various statistical data changes over time.

### Settings

Data logging can be configured using the Data Logging -> Settings page.

| Field Name              | Sample Value     | Explanation                                                |
| ----------------------- | ---------------- | ---------------------------------------------------------- |
| 1. Logging              | Enabled/Disabled | Enable or disable data logging                             |
| 2. Log period (seconds) | 3600             | Sets the number of seconds between each data capture event |

### Performance

Displays mobile signal strength variation in time (measured in dBm). Hover over the points in the graph to get precise values and timestamps. Hover over the bar at the top of the graph to display the mobile network that the router was connected to.

Displays mobile connection signal strength and data sent/received for the selected date and time period. Hover over the horizontal network operator bar to view the operator's name(s). Hover over the points of a graph to view values.

{% hint style="info" %}
The signal-strength-over-time graph for the first paragraph above wasn't among the uploaded screenshots I could confidently match.
{% endhint %}
