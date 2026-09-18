# MQTT Rx Queue

When AnyNet SMARTconnect™ is subscribed to a topic and receives new MQTT messages, it can perform either of the following functions:

*   Immediately forward the messages on the AT port in URC format. See [+EMQ Unsolicited Response Codes (URCs)](+emq-unsolicited-response-codes-urcs.md).

    The response format is:

    ```
    +EMQ:
    ```

    It includes the message index, length in bits, and forwarded MQTT message.
*   If the MQTT Rx Queue is enabled, store up to three MQTT messages in a queue in the module’s volatile memory.

    If AnyNet SMARTconnect™ receives further messages, it overwrites the existing messages, starting with the oldest.

    Messages use the following [+EMQREAD](emqread-read-message-from-mqtt-rx-queue.md) format:

    ```
    +EMQREAD:
    ```

    Use the `[mqtt] mqttenablerxqueue` parameter in the [AnyNet SMARTconnect™ configuration file](../../getting-started/using-the-anynet-smartconnect-tm-configuration-file.md) to enable or disable the MQTT Rx Queue.

## Status flags

If the MQTT Rx Queue is enabled, you can use the following status flags to obtain information about the internal status of AnyNet SMARTconnect™:

* `MQTT RX` — Set when messages appear in the MQTT Rx Queue.
* `MQTT RXov` — Set when the oldest received message is overwritten.
* `MQTT TX Internal error` — Set when a message cannot be stored.
* `MQTT TXov` — Set when the oldest transmitted message is overwritten.
* `MQTT TX OK` — Set when a transmitted message is published.
* `MQTT TX Refused` — Set when the broker rejects a message or closes the SSL connection five times.
* `Reboot required` — Set when an update requires a reboot.
* `Update fail` — Set when a host firmware, configuration, or AnyNet SMARTconnect™ update fails.
* `Update success` — Set when a host firmware, configuration, or AnyNet SMARTconnect™ update completes.

The module clears the flags when their documented reset condition occurs.

Check the status flags with [ETMINFO – displays AnyNet SMARTconnect™ and device information](../management-at-commands/etminfo-displays-anynet-smartconnect-tm-and-device-information.md).
