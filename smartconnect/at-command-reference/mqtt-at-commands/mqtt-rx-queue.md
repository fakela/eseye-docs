# MQTT Rx Queue

When AnyNet SMARTconnect™ is subscribed to a topic and receives new MQTT messages, it can perform either of the following functions:

*   Immediately forward the messages on the AT port in URC format – +EMQ: ,,

    where:

    id – is the message index number

    len – is the message length in bits

    data – is the forwarded MQTT message
*   If the MQTT Rx Queue is enabled, store up to three MQTT messages in a queue in the module’s volatile memory.

    If AnyNet SMARTconnect™ receives further messages, it overwrites the existing messages, starting with the oldest.

    Messages are stored in the following format – +EMQREAD: \r\n

    Use the \[mqtt] mqttenablerxqueue parameter in the configuration file to enable or disable the MQTT Rx Queue. For more information, see mqttenablerxqueue.

## Status Flags

If the MQTT Rx Queue is enabled, you can use the following status flags to obtain information about the internal status of AnyNet SMARTconnect™:

* MQTT RX – set when messages appear in the MQTT Rx Queue, cleared when no messages exist.
* MQTT RXov – set when the oldest received message is overwritten because of overflow, cleared when the status flags are read.
* MQTT TX Internal error – set when AnyNet SMARTconnect™ is unable to save the MQTT message in the non-volatile memory, cleared when the status flags are read.
* MQTT TXov – set when the oldest transmitted message is overwritten because of overflow, cleared when the status flags are read.
* MQTT TX OK – set when the transmitted message is successfully published, cleared when the status flags are read.
* MQTT TX Refused – set when the MQTT broker rejects the transmitted MQTT message, or closes the SSL connection five consecutive times after each publication attempt. Cleared when the status flags are read.
* Reboot required – set when a reboot is required in order to apply an update, cleared when AnyNet SMARTconnect™ resets.
* Update fail – set when a host firmware, configuration, or AnyNet SMARTconnect™ update fails, cleared when the status flags are read.
* Update success – set when an update completes successfully for host firmware, configuration, AnyNet SMARTconnect™, or AnyNet SMARTconnect™ and modem firmware, cleared when the status flags are read.

Check the status flags using the AT+ETMINFO command. For more information, see ETMINFO – displays AnyNet SMARTconnect™ and device information.

## Where to next?

* AnyNet SMARTconnect™ AT Commands
* MQTT AT commands
* Sending data from your thing to the cloud
* Sending data from the cloud to your thing
* +EMQ Unsolicited Response Codes (URCs)
* Management AT commands
* +ETM Unsolicited Response Codes (URCs)
* MQTT Rx Queue
* General AT Commands
