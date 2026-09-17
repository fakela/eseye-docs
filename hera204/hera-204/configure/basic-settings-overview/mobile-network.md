# Mobile Network

## Connection

Configure cellular settings used to connect to a mobile network.

![Mobile Network Connection](https://733576849-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FY2LsJ6998Uo7AtYcmJWd%2Fuploads%2FpTH0uCDRRqweVdMx1WJW%2Fpage_image_figure_05.png?alt=media\&token=cd96a7cd-f246-41ef-a31c-2cab40665dd8)

| Field name           | Sample value                             | Explanation                                                                     |
| -------------------- | ---------------------------------------- | ------------------------------------------------------------------------------- |
| 1. Mobile Connection | Enabled/Disabled                         | Enables or disables the mobile data connection.                                 |
| 2. Metric            | Value between 1 and 10                   | Sets default-route priority. The lowest value is the primary link.              |
| 3. Cellular Profiles | —                                        | Create up to 10 profiles. Select them manually or use them with Health Monitor. |
| a. APN               | `eseye1`                                 | Access Point Name used to connect to a GSM carrier.                             |
| b. PIN number        | Up to 8 digits, such as `12345678`       | SIM authentication PIN. Use only when the SIM has PIN enabled.                  |
| c. Username          | `username`                               | Carrier username. Available when authentication is not `none`.                  |
| d. Password          | `password`                               | Carrier password. Available when authentication is not `none`.                  |
| e. SIM               | ChipSim/SIM1                             | Selects the SIM slot used by the profile.                                       |
| f. Promote           | —                                        | Changes profile order for Health Monitor profile cycling.                       |
| Advanced Settings    | Available only in the configuration file | Contact Eseye Support for advanced settings.                                    |
| Service mode         | 2G only, 3G only, 4G only, or automatic  | Network preference. Automatic selects the best available connection.            |
| Provider             | MCC and MNC of local cellular providers  | Locks the link to a provider. Avoid this on roaming networks.                   |

{% hint style="warning" %}
An invalid PIN can block the SIM card. Use a SIM without a PIN where possible. An incorrect PIN can block the SIM after several reboots or after saving the configuration.
{% endhint %}
