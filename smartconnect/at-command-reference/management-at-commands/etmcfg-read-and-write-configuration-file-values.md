# ETMCFG – read and write configuration file values

Read and write configuration file values. See [Using the AnyNet SMARTconnect™ configuration file](../../getting-started/using-the-anynet-smartconnect-tm-configuration-file.md) for parameter details.

| Type  | Syntax                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             | Response                                                                                                                                                              |
| ----- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Test  | AT+ETMCFG=?                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        | +ETMCFG: ("clearcreds","default","revert","save","show") +ETMCFG: "get",, +ETMCFG:,, OK                                                                               |
| Write | AT+ETMCFG=\["",]\["",""\[,]] where: is the command, either: - clearcreds – deletes the certificate from the device secure store, and all AnyNet SMARTconnect™ files from the datatx folder. - default – resets the configuration file values to the default firmware values in the factory settings. After resetting to default, send the save to keep the default settings, then reboot the modem. - get – returns the current configuration value for the requested parameters. - revert – undoes any changes to the values in the configuration file up until the last save. If you want to keep the reverted values, send the save , then reboot the modem. - save – saves the current configuration values as a new version. After saving, you must reboot the modem to apply the changes. Use AT+ETMRESET to reboot the modem. - show – returns the entire current configuration file content. The response is sent as multiple URCs, with each line beginning +ETMCFG. If you do not supply , the value is applied to the configuration file in the following format: AT+ETMCFG=,, where: section is the configuration file section, parameter is the parameter name, and value is the new parameter value. | +ETMCFG: OK or +ETM ERROR: – returned for an AT command-specific error or ERROR – returned when a command is invalid, for example a parameter is missing or incorrect |

#### Examples

```
AT+ETMCFG="get","mqtt","port"
+ETMCFG: 8883
OK
```

```
AT+ETMCFG="get","mqtt","urcautoformat"
+ETMCFG: 1
OK
```

```
AT+ETMCFG="mqtt","keepalive",1800
OK
```

```
AT+ETMCFG="operation","time_format","%Y/%m/%d %T%z"
OK
```

```
AT+ETMCFG="mqtt","enable_msg_tokens",1
OK
```

```
AT+ETMCFG="save"
OK
```
