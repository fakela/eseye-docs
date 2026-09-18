# ETMFWCHECK – checks for updates to the AnyNet SMARTconnect™ application

This command checks the `[application] updateurl` for an AnyNet SMARTconnect™ application update.

See [Using the AnyNet SMARTconnect™ configuration file](../../getting-started/using-the-anynet-smartconnect-tm-configuration-file.md).

| Type    | Syntax          | Returned Result                                               |
| ------- | --------------- | ------------------------------------------------------------- |
| Execute | `AT+ETMFWCHECK` | `OK`, `+ETMFWCHECK: checking...`, and `+ETMFWCHECK: complete` |

#### Example

```
AT+ETMFWCHECK
OK
+ETMFWCHECK: checking...
+ETMFWCHECK: complete
```

If an update needs installing, the module also returns `+ETM: REBOOT REQUIRED`. Restart the system. The module returns `+ETM ERROR:` if the command fails.
