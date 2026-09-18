# +EMQ Unsolicited Response Codes (URCs)

When the MQTT broker publishes data to your thing, AnyNet SMARTconnect™ forwards the data through the AT command interface using an appropriate URC.

If the data buffer contains only printable characters, it is presented unmodified. This makes transfer of JSON and ASCII text transparent. If non-printable characters are contained in the buffer, the entire buffer is converted to ASCII-hex and sent within quotes.

| URC            | Description                                  |
| -------------- | -------------------------------------------- |
| `+EMQ:`        | Reports data received on a subscribed topic. |
| `+EMQPERSIST:` | Reports a cloud persistence-service change.  |

`+EMQ:` identifies a `singletopic` message with `S`, or a subscribed topic with its index. The response includes the data length and content. The `urcautoformat` setting controls whether the content uses ASCII-hex or text. See [EMQ – publish a message to singletopic](emq-publish-a-message-to-singletopic.md) and [Using the AnyNet SMARTconnect™ configuration file](../../getting-started/using-the-anynet-smartconnect-tm-configuration-file.md).

In simple `AWSSHADOW` mode, `+EMQPERSIST:` returns changed values. In complete mode, it returns the complete JSON message:

```json
+EMQPERSIST: {"key1":"value1","key2":"value2"}
```
