# ETMHFWREAD – reads a section of the new host firmware image

Reads consecutive sections of the new firmware image. You can set the size of each section.

If a host firmware image was previously downloaded using AT+ETMHFWGET, it is stored in flash memory on the module. For information about AT+ETMHFWGET, see ETMHFWGET – checks for new host firmware.

| Type  | Syntax                                                                                                                                                                                            | Response                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| ----- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Test  | AT+ETMHFWREAD=?                                                                                                                                                                                   | +ETMHFWREAD: (0-4294967295),(0-1024) OK                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| Read  | AT+ETMHFWREAD?                                                                                                                                                                                    | +ETMHFWREAD: , OK where: - imagesize is the size of the host firmware image in bytes - checksum is the 16-bit XOR checksum of the entire image in hexadecimal format If both imagesize and checksum are 0, no firmware image exists in the flash memory. After reading the whole image, the MCU application should run a checksum to compare its copy and the one supplied by AnyNet SMARTconnect™. This ensures the local copy was accurately copied from AnyNet SMARTconnect™. The checksum is always four characters long, with leading zeros where required. or ERROR |
| Write | AT+ETMHFWREAD=, where: - offset is the number of offset bytes (from 0 to 4294967295 bytes) - length is the number of bytes read (from 0 to 1024 bytes) offset and length are required parameters. | +ETMHFWREAD: OK where is the returned data in hexadecimal or +ETM ERROR: – returned for an AT command-specific error or ERROR – returned when a command is invalid, for example a parameter is missing or incorrect                                                                                                                                                                                                                                                                                                                                                       |

#### Example

To read 46 bytes in 16 byte chunks:

```
AT+ETMHFWREAD=0,16
+ETMHFWREAD:
OK
```

```
AT+ETMHFWREAD=16,16
+ETMHFWREAD:
OK
```

```
AT+ETMHFWREAD=32,14
+ETMHFWREAD:
OK
```
