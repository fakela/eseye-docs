# Routing

Open **Basic Settings > Routing > Active and static routes**. The **Active routes** table shows the routes currently installed on the router.

<figure><img src="../../.gitbook/assets/Screenshot 2026-08-14 at 15.35.44.png" alt=""><figcaption></figcaption></figure>

| Field       | Description                                                                                      |
| ----------- | ------------------------------------------------------------------------------------------------ |
| Destination | Network or host reached by the route.                                                            |
| Netmask     | Defines the range of destination addresses covered by the route.                                 |
| Interface   | Router interface used to send matching traffic.                                                  |
| Gateway     | Next router to which matching traffic is sent. `0.0.0.0` indicates a directly connected network. |
| Cost        | Route weight. A lower cost is preferred when otherwise equivalent routes exist.                  |

#### Configure static routes

Use the **Static routes** table to send traffic for a specific host or network through a chosen interface or gateway.

> **Important:** An incorrect static route can send traffic to the wrong interface or make a network unreachable. Confirm the destination, netmask, gateway, and interface before saving.

| Field       | Example                                   | Description                                                                                                        |
| ----------- | ----------------------------------------- | ------------------------------------------------------------------------------------------------------------------ |
| Name        | monitoring                                | Descriptive name for the route.                                                                                    |
| Destination | 192.168.55.0                              | Network or host to which the route applies.                                                                        |
| Netmask     | 255.255.255.0                             | Defines the destination range. Use `255.255.255.255` for one host.                                                 |
| Interface   | `loopback`, `lan`, `cellpri`, or `ethwan` | Interface used to send matching traffic.                                                                           |
| Gateway     | IP address                                | Next router for the destination. Leave blank only when the deployment design specifies a directly connected route. |
| Cost        | Number                                    | Route weight used when more than one route can reach the same destination. Lower values are preferred.             |

Use **Create** to add a route, **Remove** to delete one, and **Promote** to move a route higher in the displayed list. Select **Save** after making changes.
