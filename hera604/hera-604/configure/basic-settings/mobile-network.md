# Mobile Network

#### Status (read only)

Open **Basic Settings > Mobile Network > Status (read only)** to view the current modem, SIM, provider, address, signal, and APN information.

<figure><img src="../../.gitbook/assets/Screenshot 2026-08-14 at 15.35.18 (1).png" alt=""><figcaption></figcaption></figure>

| Field                     | Example             | Description                                                                                                              |
| ------------------------- | ------------------- | ------------------------------------------------------------------------------------------------------------------------ |
| Mobile connection         | Disabled            | Shows whether cellular connectivity is currently enabled.                                                                |
| IMEI                      | 357999720028739     | Identity number of the modem installed in the Hera 604.                                                                  |
| Active SIM                | CHIP                | SIM currently selected by the active cellular profile.                                                                   |
| IMSI of active SIM        | 204046996492953     | Subscription identity associated with the active SIM.                                                                    |
| ICCID of active SIM       | 8999922112090029540 | Serial number of the active SIM.                                                                                         |
| Mobile network provider   | Unknown             | Mobile operator currently serving the connection. `Unknown` is expected when the connection is disabled or not attached. |
| Mobile network IP address | Unknown             | Address assigned to the cellular interface. `Unknown` indicates that no mobile IP address is currently available.        |
| Mobile network signal     | Signal indicator    | Current cellular signal strength. Hover over the indicator to view the measured value in dBm.                            |
| APN                       | eseye1              | APN used by the active cellular profile.                                                                                 |

The values on this page cannot be edited. Select the **refresh** icon to retrieve the latest information.

#### Connection

Open **Basic Settings > Mobile Network > Connection** to enable cellular connectivity and manage the connection profiles stored on the Hera 604.

<figure><img src="../../.gitbook/assets/Screenshot 2026-08-14 at 15.35.35 (1).png" alt=""><figcaption></figcaption></figure>

**Connection settings**

| Field             | Example                 | Description                                                                                                                          |
| ----------------- | ----------------------- | ------------------------------------------------------------------------------------------------------------------------------------ |
| Mobile connection | `Enabled` or `Disabled` | Enables or disables the cellular data connection.                                                                                    |
| Metric            | 2                       | Route metric assigned to the mobile interface. When multiple WAN routes are available, the route with the lower metric is preferred. |

Set **Mobile connection** to:

* **Enabled** to allow the Hera 604 to establish a cellular data session using the active profile.
* **Disabled** to stop the cellular data connection while retaining the stored profiles.

**Cellular profiles**

| Field        | Example                     | Description                                                                                       |
| ------------ | --------------------------- | ------------------------------------------------------------------------------------------------- |
| Profile name | EseyeChip                   | Name used to identify the cellular profile.                                                       |
| APN          | eseye1                      | Access Point Name used to establish the mobile data connection.                                   |
| User name    | Blank                       | APN authentication user name, if required.                                                        |
| Password     | Masked                      | APN authentication password, if required.                                                         |
| PIN          | Blank                       | PIN for the selected physical SIM, if SIM PIN protection is enabled.                              |
| SIM          | `CHIP`, `SIM 1`, or `SIM 2` | SIM used by the profile. `CHIP` is the embedded SIM.                                              |
| Active       | `Yes` or blank              | Indicates which profile is currently selected. Select the radio control to make a profile active. |

**Select a SIM and active profile**

Each profile can use one of the three available SIM sources:

| SIM option | Description                                 |
| ---------- | ------------------------------------------- |
| `CHIP`     | Embedded SIM installed inside the Hera 604. |
| `SIM 1`    | Physical SIM inserted in slot 1.            |
| `SIM 2`    | Physical SIM inserted in slot 2.            |

To change the active profile, select the radio control in the **Active** column for the required row. The selected profile shows **Yes** after the configuration is applied.

> **Warning:** An incorrect SIM PIN can eventually block the SIM after the configuration is saved or the router restarts. Enter a PIN only when the SIM is protected and the correct PIN has been confirmed.

Use the profile controls as follows:

| Control        | Description                                                                     |
| -------------- | ------------------------------------------------------------------------------- |
| **Create**     | Add a cellular profile.                                                         |
| **Promote**    | Move a profile higher in the list used by profile-selection and recovery logic. |
| **Remove**     | Delete one profile.                                                             |
| **Remove all** | Delete all cellular profiles.                                                   |

> **Important:** Do not remove the active profile or all profiles unless replacement connection details are available. Without a valid profile, the router cannot establish a mobile data session.

Select **Save** after enabling the connection, selecting a profile, or changing profile details.
