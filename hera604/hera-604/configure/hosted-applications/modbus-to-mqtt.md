# Modbus to MQTT

Open **Integration > Modbus to MQTT** to read data from a Modbus service and publish it to an MQTT broker.

This page combines three parts: application control, the Modbus source, and the MQTT destination. Obtain the server ID, register definition, broker details, topics, and certificates from the integration owner before enabling the application.

<figure><img src="../../.gitbook/assets/Screenshot 2026-08-14 at 16.46.06.png" alt=""><figcaption></figcaption></figure>

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
