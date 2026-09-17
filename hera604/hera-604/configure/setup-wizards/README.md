---
description: Configure WAN connections and health monitoring.
---

# Setup Wizards

**Setup Wizards** contains the Network Connection wizard, which configures how the Hera 604 router reaches the internet and how it monitors that connection.

Eseye configures the router's connection before it ships. Use this wizard to change that configuration, or to set up a connection type the router was not supplied with.

{% hint style="warning" %}
Changing the connection type can reassign the Ethernet port, disable a WAN interface, or interrupt connectivity. Confirm the required network design before configuring the wizard.
{% endhint %}

### Connection modes

Selecting **Network Connection** presents four modes.

| Mode                           | Description                                                                 |
| ------------------------------ | --------------------------------------------------------------------------- |
| Cellular only                  | The router connects over the mobile network.                                |
| Ethernet only                  | The router connects through one of its Ethernet ports.                      |
| Cellular protected by Ethernet | The mobile network is the main connection. Ethernet takes over if it fails. |
| Ethernet protected by Cellular | Ethernet is the main connection. The mobile network takes over if it fails. |

The two protected modes run the connection step once for each interface, then continue as the single-interface modes do.

The wizard runs in three stages: **Set up the connection**, **Set up health monitoring**, and **Finish**.

{% hint style="warning" %}
Settings entered in the wizard are not applied until you select **Save** on the **Finish** page. Leaving the wizard before this point discards them.
{% endhint %}

### In this section

| Page                                                    | Describes                                      |
| ------------------------------------------------------- | ---------------------------------------------- |
| [Set up the connection](set-up-the-connection.md)       | The cellular and Ethernet connection settings. |
| [Set up health monitoring](set-up-health-monitoring.md) | The three health monitoring stages.            |
