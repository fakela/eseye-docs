# MQTT AT commands

AnyNet SMARTconnect™ Message Queuing Telemetry Transport (MQTT) AT commands are specific to devices that have built-in MQTT capabilities. They provide a simple and lightweight way to implement MQTT communication on a wide range of IoT devices.

Send the following AT command to enable AnyNet SMARTconnect™ MQTT on your device: AT+ETMSTATE="startmqtt" If the configuration file \[operation] parameter is set to mqtt, then AnyNet SMARTconnect™ automatically starts MQTT after power up. If the is not set, after each reboot you must send AT+ETMSTATE="startmqtt" again.

The MQTT client registers each topic with an index that is used to publish the messages. The response indicates acceptance or rejection of the topic. Optionally, you can configure a single fixed topic so the module need not keep track of topic indices for sending or receiving data.

The MQTT client supports QoS 0 and 1, and always connects to the broker as a clean session. All publish messages are queued in a non-volatile flash memory until they are sent to the broker. For QoS 1 messages, AnyNet SMARTconnect™ waits for a puback from the broker before discarding the sent data and transmitting the next message. This mechanism queues messages while a network connection is not available, and forwards messages when the connection establishes.

In the event of a power failure, queued messages are retained until reconnection occurs. Retained message storage is defined by nvqueuemaxsize in the Configuration File. For more information, see Using the AnyNet SMARTconnect™ configuration file.

Retained messages are expunged from the flash memory when the broker successfully receives them.

## Where to next?

* EMQ – publish a message to singletopic
* EMQPERSIST – report a set value to the device shadow
* EMQPUBOPEN – create a publish message topic
* EMQPUBCLOSE – remove a publish message topic
* EMQPUBLISH – publish data to a message topic
* EMQREAD – read message from MQTT RX queue
* EMQSUBOPEN – create a subscribe message topic
* EMQSUBCLOSE – cancel a subscription to a message topic
* +EMQ Unsolicited Response Codes (URCs)
* MQTT Rx Queue
* Sending data from your thing to the cloud
* Sending data from the cloud to your thing
