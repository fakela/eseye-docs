---
description: Interpret Hera 604 front-panel and Ethernet port LED states.
---

# Status indicators

The Hera reports its state through five front-panel LEDs. Each Ethernet port has two indicators.

### Front-panel LEDs

The LEDs appear in this order: Power, LAN, Wi-Fi, WAN, and Signal.

#### Power

| State                          | Meaning                                 |
| ------------------------------ | --------------------------------------- |
| Solid red                      | Powered, but software is not running    |
| Solid green                    | Powered and running normally            |
| Flashes green with another LED | Error on the port with the flashing LED |
| Flashes green after startup    | Internal error                          |
| Off                            | No mains power or product failure       |

#### LAN, Wi-Fi, and WAN

These LEDs report their own connection:

| State                          | Meaning                 |
| ------------------------------ | ----------------------- |
| Solid green                    | Connection available    |
| Regular green flash with Power | Error on that port      |
| Irregular green flash          | Data transfer           |
| Off                            | No connection available |

#### Signal

| State                              | Meaning            |
| ---------------------------------- | ------------------ |
| Brief red flash every five seconds | No signal detected |
| Solid red                          | Weak signal        |
| Solid orange                       | Medium signal      |
| Solid green                        | Strong signal      |
| Off                                | Modem is off       |

> **Tip:** Regular green flashes from two LEDs indicate a port fault. The Power LED flashes to draw attention to it.

### Ethernet port indicators

Each Ethernet port has yellow and green indicators. Judge their state by brightness because the coloured lenses remain visible when unlit.

#### Yellow connection indicator

| State    | Meaning                                        |
| -------- | ---------------------------------------------- |
| Off      | Nothing connected                              |
| Solid    | Cable attached, port available, and no traffic |
| Flashing | Data transfer                                  |

#### Green speed indicator

| State | Meaning               |
| ----- | --------------------- |
| On    | Speed up to 100 Mbps  |
| Off   | Speed up to 1000 Mbps |

> **Note:** When yellow is lit and green is off, the port runs at its fastest speed.
