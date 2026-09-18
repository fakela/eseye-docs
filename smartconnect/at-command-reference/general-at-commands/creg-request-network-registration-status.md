# CREG – request network registration status

Verifies the current network registration status of the module. Set the mode first to control the returned information and automatic status updates.

### Test command

Run the command:

```
AT+CREG=?
```

The module returns:

```
+CREG: (0-2)
OK
```

### Read command

Set the mode with the Write command before running:

```
AT+CREG?
```

The response depends on the selected mode. The first number is the mode:

```
+CREG: 0
OK
```

```
+CREG: 1
OK
```

```
+CREG: 2,[,,[,]]
```

For mode `2`, the response includes:

* The registration status:
  * `0` — Not registered. The device is not searching for an operator.
  * `1` — Registered on the home network.
  * `2` — Not registered, but searching for an operator.
  * `3` — Registration denied.
  * `4` — Unknown, for example, when the device is out of range.
  * `5` — Registered while roaming on a foreign network.
* A two-byte location area code in hexadecimal format.
* A cell ID in hexadecimal format:
  * `16` bit for 2G.
  * `28` bit for 3G or 4G.
* The radio access technology:
  * `0` — GSM.
  * `2` — UTRAN.
  * `3` — GSM with EGPRS.
  * `4` — UTRAN with HSDPA.
  * `5` — UTRAN with HSUPA.
  * `6` — UTRAN with HSDPA and HSUPA.
  * `7` — E-UTRAN.

The module returns `ERROR` if the command fails.

### Write command

Run the command:

```
AT+CREG=
```

Set the value to one of the following:

* `0` — Disable unsolicited network registration results. Check the registration status manually.
* `1` — Enable unsolicited network registration results. The modem returns a response when the status changes.
* `2` — Enable unsolicited network registration and location information results. The modem returns a response when the registration status or additional network information changes.

The module returns `OK` when it sets the mode. It returns `ERROR` if the command fails.

Factors contributing to SIM failure to register on the network may include:

* Missing network coverage
* Denied network access
* No valid roaming agreement between the home network and currently available operators

#### Example

Set the mode:

```
AT+CREG=2
OK
```

Read the registration status:

```
AT+CREG?
+CREG: 2,5,"54DB","0F6B0578",7
OK
```
