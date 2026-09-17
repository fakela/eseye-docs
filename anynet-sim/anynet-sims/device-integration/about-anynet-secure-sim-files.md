# About AnyNet Secure SIM files

Read AnyNet Secure SIM files using AT+CRSM. For more information, see [AT+CRSM – reading files from the SIM](https://eseye-v3.gitbook.io/eseye-docs/L25WdLp1CEZBZ0aOlPAR/anynet-sims/device-integration/at+crsm-reading-files-from-the-sim).

{% hint style="info" %}
SIMs can only connect to one network at a time.

For information about supported modules, see [supported modules](../esim-and-remote-provisioning/modules-supporting-remote-sim-provisioning-rsp.md).
{% endhint %}

## File format

All files follow the same basic format:

`<length><checksum><package>`

| Variable | Parameter                                                             | Description                                                                                                                                                                                                                                                                                                                                   |
| -------- | --------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| length   | 2-byte unsigned 16-bit integer                                        | package byte length, part of the file header                                                                                                                                                                                                                                                                                                  |
| checksum | 4-byte unsigned 32-bit integer, stored by most significant byte first | package CRC-32 checksum, part of the file header                                                                                                                                                                                                                                                                                              |
| package  | Binary data                                                           | The data field. Encryption keys and certificates may require some post-processing. For information about file location and post-processing requirements, see [Available files and sizes](https://eseye-v3.gitbook.io/eseye-docs/L25WdLp1CEZBZ0aOlPAR/anynet-sims/device-integration/about-anynet-secure-sim-files#available-files-and-sizes). |

## Available files and sizes

Eseye delivers the following files to your AnyNet Secure SIM. File Max Size indicates the maximum amount of data available. The file header describes the length of the actual data.

Usable Bytes refers to the number of bytes available after the header is accounted for. For more information, see [Reading the file header](https://eseye-v3.gitbook.io/eseye-docs/L25WdLp1CEZBZ0aOlPAR/anynet-sims/device-integration/basic-data-read-process#reading-the-file-header).

| File Name                 | File ID (decimal) | File ID (hexadecimal) | File Max Size (bytes)                 | Usable bytes |
| ------------------------- | ----------------- | --------------------- | ------------------------------------- | ------------ |
| Thing Name                | 28640             | 6FE0                  | 256                                   | 250          |
| Root CA                   | 28641             | 6FE1                  | 2048                                  | 2042         |
| Public signed certificate | 28642             | 6FE2                  | 2048                                  | 2042         |
| Private key               | 28643             | 6FE3                  | 2048 (not encrypted) 4096 (encrypted) | 2042 4090    |
| MQTT Endpoint             | 28644             | 6FE4                  | 256                                   | 250          |

The default path ID for the available files is: "3F007FEE". For more information, see [AT+CRSM – reading files from the SIM](https://eseye-v3.gitbook.io/eseye-docs/L25WdLp1CEZBZ0aOlPAR/anynet-sims/device-integration/at+crsm-reading-files-from-the-sim).

{% hint style="info" %}
For information about the basic data read process for each listed file, see [Basic data read process](https://eseye-v3.gitbook.io/eseye-docs/L25WdLp1CEZBZ0aOlPAR/anynet-sims/device-integration/basic-data-read-process).
{% endhint %}
