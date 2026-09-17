# Location Error Codes

When a request fails, `status.status` returns `ERR` and the `errorCode` and `errorMessage` fields are populated.

| Code | Message                                                   | Cause                                                                                                                                            |
| ---- | --------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------ |
| 0    | Decoding failed: Syntax error                             | The JSON is structured incorrectly. This can occur when text is pasted from Microsoft Word, because some Word characters differ from ASCII.      |
| 1    | The number of cells is 0                                  | The `mast`, `power`, or `ta` values are absent or incorrect.                                                                                     |
| 601  | Missing parameter ICCID/MSISDN                            | The ICCID or MSISDN is absent or incorrect, or the request URL uses `http` rather than `https`.                                                  |
| 602  | Unauthorised Access, Invalid Account, or Invalid Password | The username or password is incorrect, the account does not exist in Infinity Classic, or the account is not authorised to use the Location API. |
| 603  | Parameter `<parameter>` value missing                     | The named parameter is absent or incorrect. Where two parameters are interchangeable, the error refers to either one.                            |
| 605  | No msisdn found                                           | The ICCID or MSISDN is absent or incorrect, or the request URL uses `http` rather than `https`.                                                  |
| 606  | NoLookupFound                                             | The location service cannot find a latitude or longitude for the device.                                                                         |
| 611  | invalid                                                   | The ICCID or MSISDN is incorrect, or is not available from this account.                                                                         |

A response body beginning `<!DOCTYPE html>` indicates that the request URL path is incorrect.
