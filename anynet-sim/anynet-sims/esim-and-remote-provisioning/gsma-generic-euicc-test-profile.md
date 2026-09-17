# GSMA Generic eUICC Test Profile

{% hint style="warning" %}
The GSMA Test Profile is only supported on Eseye's v7 AnyNet+ SIMs. For more information, contact Eseye support.
{% endhint %}

The GSMA Generic eUICC Test Profile was developed by the GSMA to fulfil the requirements of industry standardised testing defined by the GCF and PTCRB certification bodies, as well as to support devices with non-removable UICCs. It contains the necessary authentication and security data required to perform testing using a test network (system simulator), during production line sampling or during sales demonstrations where there is no need for operator-specific profiles.

![](../../.gitbook/assets/eSIM_GenericTestProfiles.svg)

{% hint style="info" %}
The GSMA Generic eUICC Test Profile should be preloaded on SIMs, and is distinct from both the [bootstrap (provisioning) profiles](about-euicc-sim-profiles.md) and [operational (step 2) profiles](about-euicc-sim-profiles.md).
{% endhint %}

To request a SIM that supports the Generic eUICC Test Profile, contact your Eseye Account Manager.

## USIM authentication parameters

The following table lists the authentication parameter values for v4.0 of the GSMA Generic eUICC Test Profile.

| Authentication parameter | Value                        |
| ------------------------ | ---------------------------- |
| Algorithm                | XOR 3G                       |
| Ki                       | 0x00 0x01 0x02 … 0x0E 0x0F   |
| Opc                      | N/A                          |
| algorithmOptions         | 0x02 (128 bits)              |
| rotationConstants        | Default                      |
| xoringConstants          | Default                      |
| numberOfKeccak           | N/A                          |
| sqnOptions               | 0x02 (SQN wrap around)       |
| sqnDelta                 | 000010000000                 |
| sqnAgeLimit              | 000010000000                 |
| SQN initial values       | 0x000000000000 (all records) |

{% hint style="info" %}
For a full list of authentication parameters, download the [TS.48 eSIM GTP Profile Structure spreadsheets](https://www.gsma.com/newsroom/resources/ts-48-generic-euicc-test-profile-for-device-testing/).
{% endhint %}

## How to use the Generic eUICC Test Profile

### Before you begin

{% hint style="info" %}
Install a private LTE test network before you begin. You can use your own test network. Alternatively:

* Eseye can introduce you to third party suppliers who can provide a test network.
* Eseye can rent you a fully supported test network.

Before switching to the Generic eUICC Test Profile, set the modem to full functionality mode:

```
AT+CFUN=1
```
{% endhint %}

### To switch to and from the Generic eUICC Test Profile using AT commands

Use the following AT command (for generic SIM access) to trigger the device to switch to and from the GSMA Generic eUICC Test Profile:

```
AT+CSIM=<length>,"<command>"
```

Where:

* `<length>` is the decimal number of characters in the command string.
* `<command>` is a hexadecimal command string:
  * `80C2000003E40102` switches to the Generic eUICC Test Profile.
  * `80C2000003E40103` switches back to the previous SIM profile.

{% hint style="info" %}
For more information, see [GSMA\_TS48\_eSIM\_GTP\_Profile\_Structure v4.0.xlsx](https://eseyeltd.sharepoint.com/sites/SIMinformation/_layouts/15/AccessDenied.aspx?Source=https%3A%2F%2Feseyeltd.sharepoint.com%2F%3Ax%3A%2Fr%2Fsites%2FSIMinformation%2FShared+Documents%2FSIM+Batch+Information%2Fspecs%2FTS48+test+profile%2FGSMA_TS48_eSIM_GTP_Profile_Structure+v4.0.xlsx%3Fd%3Dw2ec221a39b94470c8217474e18125f2a%26csf%3D1%26web%3D1%26e%3D0CatSe\&correlation=699c3ba2-d0bb-3001-27cd-4fefd8fa9948\&Type=item\&name=3dfd9eee-36b4-4a65-bd42-51361d7a5199\&listItemId=27735\&listItemUniqueId=2ec221a3-9b94-470c-8217-474e18125f2a\&allowautoredirecttosource=true).
{% endhint %}

To use the Generic eUICC Test Profile:

1.  Use the following AT command to trigger the device to switch to the GSMA Generic eUICC Test Profile:

    ```
    AT+CSIM=<length>,"80C2000003E40102"
    ```

    For example:

    ```
    AT+CSIM=16,"80C2000003E40102"
    ```
2.  Run the test.

    <div data-gb-custom-block data-tag="hint" data-style="info" class="hint hint-info"><p>You do not have to activate the SIM. Eseye will not charge you for the test. There is no limitation on data usage.</p></div>
3.  After all tests are complete, use the following AT command to switch back to the previous SIM profile:

    ```
    AT+CSIM=<length>,"80C2000003E40103"
    ```

    For example:

    ```
    AT+CSIM=16,"80C2000003E40103"
    ```
