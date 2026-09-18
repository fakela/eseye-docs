# ETMHFWGET – checks for new host firmware

Requests a check for new host firmware. Use the Read function to check if new firmware is already downloaded and available.

| Type  | Syntax                                                            | Response                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| ----- | ----------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Test  | AT+ETMHFWGET=?                                                    | +ETMHFWGET: OK                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| Read  | Not currently available.                                          |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| Write | AT+ETMHFWGET= where is the unique identity of the current device. | OK +ETMHFWGET: checking... – AnyNet SMARTconnect™ is searching the configuration file \[host] updateurl for new firmware. If new firmware is available, the file is downloaded. For more information, see updateurl. The host can read the downloaded file using AT+ETMHFWREAD. For more information, see ETMHFWREAD – reads a section of the new host firmware image. +ETMHFWGET: none – no host firmware is available. Ensure that the URL is configured and accessible or +ETMHFWGET: available – the latest host firmware is downloaded and available or +ETM ERROR: |

#### Example

```
AT+ETMHFWGET=862061234567890
OK
+ETMHFWGET: checking...
+ETMHFWGET: none
```
