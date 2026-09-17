---
description: >-
  Enable the hosted AWS IoT application and manage certificate files on the Hera
  604.
---

# Hosted applications

Hosted applications are specialised applications that run on the Hera 604. Each application must be configured with the connection details and security files required by the external service.

Only change these settings when you have the connection details supplied by the deployment engineer or service owner. Incorrect certificate, port, topic, or serial settings can prevent the application from connecting.

After changing a page, select **Save** to apply the new values. Select **Reset** to discard changes that have not been saved.

###

#### AWS IOT

Open **Hosted Applications > AWS IOT** to connect the Hera 604 to an AWS IoT deployment.

When the application is enabled, the router uses the configured endpoint and device identity files to establish the AWS IoT connection. Obtain the socket port, certificate formats, and file locations from the deployment configuration before enabling it.

\<!-- Insert Screenshot 2026-08-14 at 16.45.47.png here. -->

**Application settings**

| Field                                | Value shown             | Description                                                                                                                                             |
| ------------------------------------ | ----------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Application                          | `Enabled` or `Disabled` | Starts or stops the AWS IoT application. Keep it disabled until the endpoint and identity files have been configured.                                   |
| Use WiFi LED for AWS IOT file status | `Yes` or `No`           | Uses the Wi-Fi LED to indicate the status of the files required by the AWS IoT application. This changes the LED's purpose while the option is enabled. |
| Socket port                          | Blank                   | Network port used to connect to the AWS IoT service. Enter the port specified in the deployment configuration.                                          |

**AWS IoT files**

| File name  | Type        | Available format             | From SIM      | Purpose                                                                         |
| ---------- | ----------- | ---------------------------- | ------------- | ------------------------------------------------------------------------------- |
| privatekey | Key         | `Base64 PEM` or `Binary DER` | `Yes` or `No` | Private key used to authenticate the Hera 604. Treat this file as confidential. |
| clientcert | Certificate | `Base64 PEM` or `Binary DER` | `Yes` or `No` | Client certificate that identifies the router to AWS IoT.                       |
| rootca     | Certificate | `Base64 PEM` or `Binary DER` | `Yes` or `No` | Root certificate authority used to verify the AWS IoT service certificate.      |
| url        | ---         | Not applicable               | `Yes` or `No` | AWS IoT endpoint assigned to the device or deployment.                          |
| thingname  | ---         | Not applicable               | `Yes` or `No` | AWS IoT Thing name assigned to the router.                                      |

**From SIM** determines whether the router obtains that value or file from the SIM. Set it to **No** only when the deployment is designed to use a file or value stored elsewhere on the router.

**Configure AWS IOT**

1. Leave **Application** set to **Disabled** while entering the settings.
2. Enter the **Socket port** supplied for the AWS IoT deployment.
3. For **privatekey**, **clientcert**, and **rootca**, select the format that matches the supplied files.
4. For each row, set **From SIM** according to where the deployment stores that item.
5. Set **Use WiFi LED for AWS IOT file status** to **Yes** only when the LED is required as a file-status indicator.
6. Confirm that the endpoint, Thing name, certificate, and private key belong to the same AWS IoT device identity.
7. Set **Application** to **Enabled**.
8. Select **Save**.

> **Security:** Do not copy private keys into tickets, emails, screenshots, or operator notes. If a private key is exposed, follow the deployment's credential-replacement procedure.

### Integration

Use the Integration pages to exchange data between equipment connected to the Hera 604 and an IP or MQTT service.

Before enabling an integration, confirm the cable and port assignment, serial parameters, destination address, permitted firewall path, and credentials. The settings at both ends of the connection must match.

#### Serial to IP

Open **Integration > Serial to IP** to forward data between either physical serial port and an IP connection.

The page contains independent columns for **serial1** and **serial2**. Configure only the port used by the installation. The screenshot maps **serial1** to `/dev/eser1` and **serial2** to `/dev/eser0`; use the mapping displayed by the router rather than assuming the device numbers follow the port names.

\<!-- Insert Screenshot 2026-08-14 at 16.46.00.png here. -->

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

#### Modbus to MQTT

Open **Integration > Modbus to MQTT** to read data from a Modbus service and publish it to an MQTT broker.

This page combines three parts: application control, the Modbus source, and the MQTT destination. Obtain the server ID, register definition, broker details, topics, and certificates from the integration owner before enabling the application.

\<!-- Insert Screenshot 2026-08-14 at 16.46.06.png here. -->

Fields highlighted in pink in the interface have not been completed. Supply the required deployment values before enabling the application.

**Application settings**

| Field       | Value shown             | Description                                                                                                                                                    |
| ----------- | ----------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Application | `Enabled` or `Disabled` | Starts or stops the Modbus-to-MQTT application. Keep it disabled until both connections are configured.                                                        |
| Trace file  | Blank                   | File used for application trace output. Use the path defined for the deployment; trace files can contain operational data and should be protected accordingly. |

**Modbus settings**

| Field                | Value shown | Description                                                                                                          |
| -------------------- | ----------- | -------------------------------------------------------------------------------------------------------------------- |
| Modbus server ID     | Blank       | Unit or server identifier of the Modbus device to query.                                                             |
| Modbus register file | Blank       | Register-definition file used to identify the Modbus registers and values processed by the application.              |
| Modbus MSG code      | Blank       | Message or function code required by the Modbus integration. Use the value supplied with the register configuration. |
| Modbus mode          | `TCP`       | Modbus transport mode. The displayed configuration uses Modbus TCP.                                                  |
| Modbus TCP port      | Blank       | TCP port exposed by the Modbus service.                                                                              |
| Modbus TCP URL       | Blank       | Hostname or IP address of the Modbus TCP service.                                                                    |

**MQTT settings**

| Field                                  | Value shown        | Description                                                                                                            |
| -------------------------------------- | ------------------ | ---------------------------------------------------------------------------------------------------------------------- |
| Client ID                              | `modbus_mqtt`      | Client identifier presented to the MQTT broker. It must be unique where required by the broker.                        |
| MQTT URL                               | Blank              | Hostname or address of the MQTT broker.                                                                                |
| Publish topic                          | Blank              | Topic to which Modbus data is published.                                                                               |
| Directive topic                        | Blank              | Topic from which the application receives supported directives or control messages.                                    |
| Last Will and Testament topic          | Blank              | Topic on which the broker publishes the client's Last Will message after an unexpected disconnection.                  |
| Last Will and Testament message        | Blank              | Message published by the broker after an unexpected disconnection.                                                     |
| Retain Last Will and Testament message | `No`               | Determines whether the broker retains the Last Will message for new subscribers.                                       |
| Keep MQTT alive (seconds)              | `60`               | Maximum keepalive interval negotiated with the broker.                                                                 |
| MQTT port                              | Blank              | Network port used to reach the MQTT broker.                                                                            |
| Username                               | Blank              | MQTT account name, when username/password authentication is used.                                                      |
| Password                               | Blank              | Password for the MQTT account. Treat it as confidential.                                                               |
| Quality of Service                     | `0`                | MQTT delivery level. Use the level required by the broker and deployment.                                              |
| Use Transport Layer Security?          | `Yes`              | Enables TLS to protect and authenticate the broker connection.                                                         |
| Use certificates from SIM              | `No`               | Determines whether the TLS certificate material is obtained from the SIM.                                              |
| Private key                            | `/var/private_key` | Location of the private key used for certificate-based authentication when certificates are not obtained from the SIM. |

**Configure Modbus to MQTT**

1. Leave **Application** set to **Disabled**.
2. Enter the Modbus server ID and select the register file and message code supplied for the connected equipment.
3. Select the required Modbus mode. For TCP, enter the service URL and TCP port.
4. Enter a unique **Client ID** for the MQTT connection.
5. Enter the MQTT broker URL and port.
6. Enter the publish and directive topics exactly as supplied. MQTT topic names are case-sensitive.
7. Configure the Last Will topic, message, and retain setting if the deployment uses connection-state monitoring.
8. Set the keepalive interval and Quality of Service required by the broker.
9. Enter the username and password if the broker uses account credentials.
10. Keep **Use Transport Layer Security?** set to **Yes** unless the integration owner has explicitly approved an unencrypted connection.
11. Set **Use certificates from SIM** according to where the deployment stores its certificate material. If it is set to **No**, confirm the private-key path and any certificate paths shown by the interface.
12. Enter the trace-file path if tracing is required.
13. Set **Application** to **Enabled** and select **Save**.
14. Confirm that the router can reach both the Modbus service and MQTT broker, then verify that expected values appear on the publish topic.

> **Credentials and certificates:** Do not include MQTT passwords, private keys, or certificate contents in screenshots, tickets, or operator notes.

### Before enabling an application

Confirm all of the following:

* The external service hostname or IP address is correct and reachable.
* The required TCP ports are permitted by the network and firewall configuration.
* Serial settings match the connected equipment.
* Certificates, private keys, usernames, and passwords belong to the same deployment.
* The router clock is correct, because certificate validation can fail when the time is wrong.
* A test procedure and a safe way to disable the application are available.
