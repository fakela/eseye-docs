# +EMQ Unsolicited Response Codes (URCs)

When the MQTT broker publishes data to your thing, AnyNet SMARTconnect™ forwards the data through the AT command interface using an appropriate URC.

If the data buffer contains only printable characters, it is presented unmodified. This makes transfer of JSON and ASCII text transparent. If non-printable characters are contained in the buffer, the entire buffer is converted to ASCII-hex and sent within quotes.

| URC                            | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| ------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| +EMQ: ~~,\r\n or +EMQ: ,\r\n~~ | Indicates data received on a subscribed topic, where: - S is for singletopic only. Indicates data received on a single topic. For information about singletopic, see EMQ – publish a message to singletopic. - is the subscribed topic index number, not for singletopic use - is the length of the incoming data - is the received data in either ASCII-hex format or as text, depending on both the urcautoformat setting in the configuration file, and if appears within quotes. For example, if the urcautoformat setting = 1, then: - ,\r\n"" reports data in ASCII-hex format - ,\r\n reports data in text format For more information, see Using the AnyNet SMARTconnect™ configuration file.                               |
| +EMQPERSIST:                   | Reports a message from the cloud service indicating something in the persistence service has changed. For simple AWSSHADOW  mode, only the '{"state":{...' parameters that have changed in the AWS delta are listed. For example: +EMQPERSIST: {"key1":"value1","key2":"value2"} where value1 and value2 are any type of value, including strings, integers, decimals and negative numbers. For complete AWSSHADOW mode, the entire JSON is listed. For example: +EMQPERSIST:{"version":186201,"timestamp":1573232068,"state":{"key1":"value1","key2":"value2"},"metadata":{"key1":{"timestamp":1573232068},"key2":{"timestamp":1573232068\}}} where value1 and value2 are numeric values, including decimals and negative numbers. |

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
