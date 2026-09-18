# EMQ – publish a message to singletopic

Publish a message to the system `singlepubtopic`. `singlepubtopic` is a predefined topic for single-subscription systems. The host does not need to register a publish topic with `+EMQPUBOPEN`.

The configuration file defines the publish topic and QoS. The topic index is not required. See [Using the AnyNet SMARTconnect™ configuration file](../../getting-started/using-the-anynet-smartconnect-tm-configuration-file.md).

| Type  | Syntax     | Returned result                             |
| ----- | ---------- | ------------------------------------------- |
| Test  | `AT+EMQ=?` | `+EMQ: OK`                                  |
| Read  | `AT+EMQ?`  | `OK` or `ERROR`                             |
| Write | `AT+EMQ=`  | `OK`, `:SEND OK`, `+ETM ERROR:`, or `ERROR` |

For the Write command:

* Send an unquoted message as unmodified text.
* Limit the payload to `1000` printable characters.
* Send quoted ASCII-hex data with an even number of characters from `0-9`, `a-f`, or `A-F`.
* Start quoted JSON data with `{` immediately after the opening quote. AnyNet SMARTconnect™ does not validate JSON.
* AnyNet SMARTconnect™ converts ASCII-hex to binary for transmission. It removes escape characters from JSON messages.

The module returns `:SEND OK` after it publishes the message. This may wait until AnyNet SMARTconnect™ reconnects. The module returns `+ETM ERROR:` for command-specific errors. Confirm that `singlepubtopic` is configured. The module returns `ERROR` when the command is invalid or a parameter is missing.

#### Example

Send the message:

```
AT+EMQ="{"BatteryPower": "Low"}"
```

The module returns:

```
OK
:SEND OK
```
