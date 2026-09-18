# ETMRESET – reboot the modem

Reboots the modem.

| Type    | Syntax        | Response                                                |
| ------- | ------------- | ------------------------------------------------------- |
| Execute | `AT+ETMRESET` | The module reboots and returns status URCs, or `ERROR`. |

#### Example

```
AT+ETMRESET
OK
+ETM: REBOOTING
NORMAL POWER DOWN
RDY
APP RDY
+ETM: SYSSTART
+ETM: IDLE
```
