# ETMCFGCHECK – checks if a new AnyNet SMARTconnect™ configuration file is available

This command checks the `[config] updateurl` for a configuration file update.

See [Using the AnyNet SMARTconnect™ configuration file](../../getting-started/using-the-anynet-smartconnect-tm-configuration-file.md).

| Type    | Syntax           | Returned Result                                                 |
| ------- | ---------------- | --------------------------------------------------------------- |
| Execute | `AT+ETMCFGCHECK` | `OK`, `+ETMCFGCHECK: checking...`, and `+ETMCFGCHECK: complete` |

#### Example

```
AT+ETMCFGCHECK
OK
+ETMCFGCHECK: checking...
+ETMCFGCHECK: complete
```

If an update needs applying, the module also returns `+ETM: REBOOT REQUIRED`. Restart the system. The module returns `+ETM ERROR:` if the command fails.
