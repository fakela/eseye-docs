# MQTT AT commands

AnyNet SMARTconnect™ Message Queuing Telemetry Transport (MQTT) AT commands support devices with built-in MQTT capabilities. They implement MQTT communication on IoT devices.

To enable AnyNet SMARTconnect™ MQTT, send the following command:

```
AT+ETMSTATE="startmqtt"
```

If the configuration file `[operation]` parameter is set to `mqtt`, AnyNet SMARTconnect™ starts MQTT after power up. If the parameter is not set, send the command after every reboot.

The MQTT client registers each topic with an index that is used to publish the messages. The response indicates acceptance or rejection of the topic. Optionally, you can configure a single fixed topic so the module need not keep track of topic indices for sending or receiving data.

The MQTT client supports QoS `0` and `1`. It connects to the broker as a clean session.

The client queues published messages in non-volatile flash memory until the broker receives them. For QoS `1` messages, it waits for a `puback` before discarding sent data and transmitting the next message. This preserves messages during network outages.

Queued messages remain after a power failure until the module reconnects. The `nvqueuemaxsize` setting in the [AnyNet SMARTconnect™ configuration file](../../getting-started/using-the-anynet-smartconnect-tm-configuration-file.md) defines retained message storage.

The client removes retained messages from flash memory after the broker receives them.
