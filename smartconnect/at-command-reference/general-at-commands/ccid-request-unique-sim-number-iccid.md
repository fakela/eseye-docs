# CCID – request unique SIM number (ICCID)

This command returns the unique Integrated Circuit Card Identifier (ICCID) of the installed SIM card.

| Type    | Syntax      | Returned Result                                                                              |
| ------- | ----------- | -------------------------------------------------------------------------------------------- |
| Test    | `AT+CCID=?` | `OK`                                                                                         |
| Execute | `AT+CCID`   | `+CCID: OK` where is the unique ICCID for the attached SIM. or `ERROR` – the command failed. |

#### Example

Run the command:

```
AT+CCID
```

The module returns:

```
+CCID: 8944531233020460000
OK
```
