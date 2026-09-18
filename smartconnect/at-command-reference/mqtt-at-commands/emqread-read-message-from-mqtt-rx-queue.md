# EMQREAD – read message from MQTT RX queue

AnyNet SMARTconnect™ can store up to three MQTT messages in a queue in the Quectel module’s volatile memory.

`AT+EMQREAD` reads the stored messages.

| Type  | Syntax         | Returned Result                                      |
| ----- | -------------- | ---------------------------------------------------- |
| Test  | `AT+EMQREAD=?` | `OK`                                                 |
| Read  | `AT+EMQREAD?`  | `OK`                                                 |
| Write | `AT+EMQREAD`   | A queued message, or `+EMQREAD: NO MESSAGE` and `OK` |

The response identifies either `S` for `singletopic`, or the subscribed topic index. It includes the message length and data. The `urcautoformat` configuration setting controls whether the data is ASCII-hex or text. See [EMQ – publish a message to singletopic](emq-publish-a-message-to-singletopic.md) and [Using the AnyNet SMARTconnect™ configuration file](../../getting-started/using-the-anynet-smartconnect-tm-configuration-file.md).

#### Example

```
AT+EMQREAD
+EMQREAD: 0,20
Example data message
OK
```
