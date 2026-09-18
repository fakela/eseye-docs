# EMQPUBCLOSE – remove a publish message topic

Remove a publish message topic.

| Type  | Syntax                 | Returned result                        |
| ----- | ---------------------- | -------------------------------------- |
| Test  | `AT+EMQPUBCLOSE=?`     | `+EMQPUBCLOSE:(0-7)` and `OK`          |
| Read  | `AT+EMQPUBCLOSE?`      | `OK`                                   |
| Write | `AT+EMQPUBCLOSE=(0-7)` | `OK`, `+EMQPUBCLOSE:(0-7)`, or `ERROR` |

For the Write command, set a publish index from `0` through `7`. Open a publish topic for the selected index first. The response status is `0` when it cancels the topic, or `-2` when no topic exists for the index. Start MQTT with `AT+ETMSTATE="startmqtt"` before running the command.

#### Example

```
AT+EMQPUBCLOSE=0
OK
+EMQPUBCLOSE: 0,0
```
