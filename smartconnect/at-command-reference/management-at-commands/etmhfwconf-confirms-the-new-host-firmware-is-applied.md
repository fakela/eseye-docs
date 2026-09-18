# ETMHFWCONF – confirms the new host firmware is applied

Confirms the new host firmware image is applied and then deletes the image from the modem flash memory.

| Type    | Syntax          | Response              |
| ------- | --------------- | --------------------- |
| Execute | `AT+ETMHFWCONF` | `OK` or `+ETM ERROR:` |

#### Example

```
AT+ETMHFWCONF
OK
```

`+ETM ERROR:` may indicate that the firmware download failed. Confirm that [ETMHFWGET – checks for new host firmware](etmhfwget-checks-for-new-host-firmware.md) returned `+ETMHFWGET: available`.
