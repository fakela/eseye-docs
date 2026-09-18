# EMQPERSIST – report a set value to the device shadow

Report a set value to the device shadow/twin. The operation depends on which AWSSHADOW mode you set, either simple or complete.

You set `AWSSHADOW` in the configuration file. See [Using the AnyNet SMARTconnect™ configuration file](../../getting-started/using-the-anynet-smartconnect-tm-configuration-file.md). Alternatively, send:

```
AT+ETMCFG="mqtt","awsshadow","<off/simple/complete>"
```

## AWSSHADOW simple mode

The shadow AnyNet SMARTconnect™ performs the following automatically:

* Generates the JSON state and reported or desired objects
* Subscribes to the shadow/update/delta topic, and filters out the containing objects
* Presents the host with the state object JSON content only, sent via URC

The host only sends the content of the reported object.

## AWSSHADOW complete mode

The host sends the complete JSON for the shadow to AnyNet SMARTconnect™.

AnyNet SMARTconnect™ sends the complete shadow message as a URC, without filtering.

## EMQPERSIST commands

| Type  | Syntax            | Returned result                    |
| ----- | ----------------- | ---------------------------------- |
| Test  | `AT+EMQPERSIST=?` | `+EMQPERSIST: OK`                  |
| Read  | `AT+EMQPERSIST?`  | `OK` or `ERROR`                    |
| Write | `AT+EMQPERSIST=`  | `OK`, `:SEND OK`, or `+ETM ERROR:` |

For the Write command, send JSON that matches the configured `AWSSHADOW` mode.

In simple mode, send the reported or desired object content:

```json
{"key": value}
```

If the content omits `reported` and `desired`, AnyNet SMARTconnect™ treats it as `reported`. It adds the required `state` and `reported` containers. If the content includes `reported` or `desired`, it adds only the `state` container.

In complete mode, send the complete shadow update:

```json
{"state":{"reported":{"key":value}}}
```

#### Examples

For Simple mode:

```
AT+EMQPERSIST="{"Temperature":-3.5}"
AT+EMQPERSIST="{"Colour":"Blue"}"
```

For Complete mode, including setting AWSSHADOW to complete:

```
AT+ETMCFG="mqtt","awsshadow","complete"
AT+EMQPERSIST="{"state":{"reported":{"Temperature":28.0\}}}"
```

##
