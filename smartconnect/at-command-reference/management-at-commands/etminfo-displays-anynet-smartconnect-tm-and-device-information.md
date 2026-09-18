# ETMINFO – displays AnyNet SMARTconnect™ and device information

Displays information about the current AnyNet SMARTconnect™ application and device.

| Type  | Syntax               | Response                                       |
| ----- | -------------------- | ---------------------------------------------- |
| Test  | `AT+ETMINFO=?`       | Available information keys and `OK`            |
| Read  | `AT+ETMINFO?`        | `OK` or `ERROR`                                |
| Write | `AT+ETMINFO="<key>"` | The requested value, `+ETM ERROR:`, or `ERROR` |

Use these information keys:

* `busy` checks for background operations.
* `ci` returns the cell identity.
* `iccid`, `imei`, and `imsi` return SIM, device, and cellular subscriber identifiers.
* `location` returns device latitude and longitude.
* `mcc` and `mnc` return the mobile country and network codes.
* `mqttpubmsg` returns the number of stored MQTT messages.
* `rssi` returns the received signal strength.
* `service` returns the network registration status.
* `statusflags` returns the status flags.
* `version` returns the Eseye software version on the selected modem.
* `gettime` returns UTC time, and `getlocaltime` returns local time.

The modem obtains time from NITZ and NTP when available. The `[operation] time_format` configuration setting controls the returned time format.

For `busy`, `0000` means it is safe to power down. Any other hexadecimal value means background work is in progress. Do not power down with `pwrkey`.

For `mqttpubmsg`, the response lists messages in the non-volatile and volatile queues. For `service`, `0` means not registered and `1` means registered.

`statusflags` returns hexadecimal status flags:

* `0000` — No flag set.
* `0001` — MQTT RX.
* `0002` — MQTT RXov.
* `0004` — MQTT TXov.
* `0008` — Update success.
* `0010` — MQTT TX Refused.
* `0020` — MQTT TX Internal error.
* `0040` — MQTT TX OK.
* `0080` — Update fail.
* `0100` — Reboot required.

When multiple flags are set, the modem adds their values. For example, `000A` indicates MQTT RXov (`0002`) and Update success (`0008`). See [MQTT Rx Queue](../mqtt-at-commands/mqtt-rx-queue.md) for flag meanings.

The module returns `+ETM ERROR:` for command-specific errors. It returns `ERROR` for an invalid command or missing parameter.

If location returns unknown, enable location in [ETMCFG – read and write configuration file values](etmcfg-read-and-write-configuration-file-values.md). Also confirm that the modem can acquire a satellite lock.

#### Example

```
AT+ETMINFO="iccid"
+ETMINFO: 8944538523020412345
OK
```

```
AT+ETMINFO="gettime"
+ETMINFO: 2023/12/15 13:40:02-0430
OK
```

```
AT+ETMINFO="getlocaltime"
+ETMINFO: 2023/12/15 09:10:04-0430
OK
```

### Related resources

* 8618 Eseye-enabled Quectel BG96 module Developer Guide (PDF)
