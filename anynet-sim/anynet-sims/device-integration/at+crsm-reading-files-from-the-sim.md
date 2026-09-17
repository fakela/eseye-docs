# AT+CRSM – reading files from the SIM

## AT+CRSM – reading files from the SIM

Read files from the AnyNet Secure SIM. For precise formats and response details, refer to the modem provider documentation.

We recommend that you use AT+CRSM over the generic SIM access AT+CSIM. AT+CRSM provides easier access to the SIM file system, as the modem facilitates the SIM interface locking and file selection routines.

{% hint style="info" %}
This command describes fields required for Eseye file extraction. Refer to 3GPP TS 27.007 for the complete definition.
{% endhint %}

### Command syntax

Use the following command:

```
AT+CRSM=<command>[,<fileid>[,<P1offset>,<P2offset>,<P3readlength>[,<data>[,"<pathid>"]]]]
```

The command includes these parameters:

* `command` is passed to the SIM. Use `176` (`READ BINARY`) to extract security and identity information.
* `fileid` is the integer file identifier on the SIM. See [Available files and sizes](https://eseye-v3.gitbook.io/eseye-docs/L25WdLp1CEZBZ0aOlPAR/anynet-sims/device-integration/about-anynet-secure-sim-files#available-files-and-sizes).
* `P1offset`, `P2offset`, and `P3readlength` define the read offset and length. `AT+CRSM` returns up to 255 bytes per read.
  * `P1offset` contains the upper 8 bits of the 16-bit file offset.
  * `P2offset` contains the lower 8 bits of the 16-bit file offset. It can include the modulus (`MOD`) operator.
  * `P3readlength` is the integer read length. Limit it to 255 bytes.
* `data` is unused for `READ BINARY`. Leave it empty.
* `pathid` is the elementary file path in hexadecimal. Use `"3F007FEE"` for AnyNet Secure SIM files.

You can use `+`, `-`, `/`, and `*` arithmetic operators in the offset parameters.

### Returned result

A successful command returns:

```
+CRSM: <sw1>,<sw2>[,"<RETURNEDDATA>"]
```

A failed command returns:

```
+CME ERROR: <err>
```

The response fields are:

* `sw1` and `sw2` describe command execution. They can indicate success or file-read errors.
* `RETURNEDDATA` contains successful response data as an ASCII hexadecimal string.
* `err` is the error result when the command cannot pass to the SIM.
