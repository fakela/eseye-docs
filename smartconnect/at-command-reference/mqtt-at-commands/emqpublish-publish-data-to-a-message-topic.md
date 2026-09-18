# EMQPUBLISH – publish data to a message topic

Publish data to a created message topic. Data is sent to your thing in the cloud.

| Type  | Syntax                       | Returned result                               |
| ----- | ---------------------------- | --------------------------------------------- |
| Test  | `AT+EMQPUBLISH=?`            | Available topic indexes, QoS values, and `OK` |
| Read  | `AT+EMQPUBLISH?`             | `OK`                                          |
| Write | `AT+EMQPUBLISH=(0-7),(0-1),` | `OK`, `ERROR`, `:SEND OK`, or `:SEND FAIL`    |

For the Write command:

* Set the publish topic index from `0` through `7`.
* Set QoS to `0` for at-most-once delivery or `1` for at-least-once delivery.
* Send an unquoted message as unmodified text.
* Limit the payload to `1000` printable characters.
* Send quoted ASCII-hex data with an even number of characters from `0-9`, `a-f`, or `A-F`.
* Start quoted JSON data with `{` immediately after the opening quote. AnyNet SMARTconnect™ does not validate JSON.

The module returns `:SEND OK` when it publishes the message. For QoS `1`, the broker sends a `PUBACK` to confirm receipt. `:SEND FAIL` applies only to QoS `1`. If the module returns `ERROR`, check that [EMQPUBOPEN – create a publish message topic](emqpubopen-create-a-publish-message-topic.md) has configured the topic and [ETMSTATE – check current state](../management-at-commands/etmstate-check-current-state.md) has started MQTT.

#### Example

```
AT+EMQPUBLISH=1,1,"{"BatteryPower": "Low"}"
OK
:SEND OK
```
