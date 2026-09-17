# Serial to IP

Open **Integration > Serial to IP** to forward data between either physical serial port and an IP connection.

The page contains independent columns for **serial1** and **serial2**. Configure only the port used by the installation. The screenshot maps **serial1** to `/dev/eser1` and **serial2** to `/dev/eser0`; use the mapping displayed by the router rather than assuming the device numbers follow the port names.

<figure><img src="../../.gitbook/assets/Screenshot 2026-08-14 at 16.46.00.png" alt=""><figcaption></figcaption></figure>



**Forwarding settings**

| Field                                             | Value shown             | Description                                                                                                                     |
| ------------------------------------------------- | ----------------------- | ------------------------------------------------------------------------------------------------------------------------------- |
| Forwarding                                        | `Enabled` or `Disabled` | Enables or disables Serial-to-IP forwarding for the selected serial port.                                                       |
| Characters to indicate forwarding                 | Blank; example `a,b,c`  | Characters that cause the buffered serial data to be forwarded. Enter multiple trigger characters as a comma-separated list.    |
| String length to trigger forwarding               | `0`                     | Number of buffered characters that triggers forwarding. A value of `0` means that this trigger is not set.                      |
| String to trigger forwarding                      | Blank                   | Character sequence that causes the buffered data to be forwarded.                                                               |
| Max waiting time (milliseconds) before forwarding | `0`                     | Maximum time data may remain buffered before it is forwarded. Enter a value suitable for the connected device's message timing. |

The forwarding triggers control when buffered serial data is sent to the IP connection. Use the trigger method required by the connected equipment; do not enter arbitrary delimiter characters or message lengths.

**Serial connection**

| Field    | serial1 shown | serial2 shown | Description                                                                    |
| -------- | ------------- | ------------- | ------------------------------------------------------------------------------ |
| Device   | `/dev/eser1`  | `/dev/eser0`  | Router device assigned to the physical serial port. Use the displayed mapping. |
| Baud     | `9600`        | `9600`        | Serial transmission speed in bits per second.                                  |
| Databits | `8`           | `8`           | Number of data bits in each serial character.                                  |
| Stopbits | `1`           | `1`           | Number of stop bits used to mark the end of a serial character.                |
| Parity   | `None`        | `None`        | Serial error-checking mode.                                                    |

The **Baud**, **Databits**, **Stopbits**, and **Parity** values must exactly match the connected equipment. A common notation for the values shown is **9600 8N1**.

**IP connection**

| Field                                | Value shown | Description                                                                                                                                  |
| ------------------------------------ | ----------- | -------------------------------------------------------------------------------------------------------------------------------------------- |
| IP port for inbound data             | Blank       | Local IP port on which the router receives data to send to the serial device.                                                                |
| IP address for outbound data         | Blank       | Destination IP address to which serial data is sent.                                                                                         |
| IP port for outbound data            | Blank       | Destination port to which serial data is sent.                                                                                               |
| IP protocol                          | `TCP`       | Transport protocol used by the IP connection. Select the protocol required by the receiving service.                                         |
| Maximum TCP connection attempts      | `5`         | Maximum number of attempts to establish the TCP connection. Applies when **IP protocol** is set to TCP.                                      |
| Maximum TCP idle time (milliseconds) | `0`         | Maximum permitted TCP idle time. Confirm the required meaning of `0` for the deployed software before relying on it as an unlimited timeout. |
| Keep TCP alive                       | `Yes`       | Enables TCP keepalive so that inactive or failed connections can be detected.                                                                |

**Configure Serial to IP**

1. Identify whether the equipment is connected to **serial1** or **serial2**.
2. Keep **Forwarding** disabled while entering the settings.
3. Set **Baud**, **Databits**, **Stopbits**, and **Parity** to match the equipment.
4. Enter the inbound port if an IP client will send data to the serial device.
5. Enter the outbound IP address and port if serial data will be sent to a remote IP service.
6. Select the required **IP protocol**.
7. If TCP is used, set the connection-attempt, idle-time, and keepalive values required by the deployment.
8. Configure the forwarding trigger used by the equipment's message format.
9. Set **Forwarding** to **Enabled** for the configured port.
10. Select **Save**.
11. Send a known test message in both required directions and confirm that it arrives unchanged.

> **Network access:** The destination must be reachable through the router, and any required firewall rule must already exist. Do not expose an inbound serial service to an untrusted network.
