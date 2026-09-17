# Understanding the IMSI rotation and switching process

For both IMSI rotation and IMSI switching, the process of how the IMSI changes within the SIM is the same. However, different factors will influence an IMSI rotation versus an IMSI switch.

For IMSI rotation, an application in the SIM triggers a rotation if it detects that there is no network connection for a period of time. For IMSI switching, the Connectivity Management Platform can instruct a SIM that is connected to a network to immediately change IMSI.

## How the SIM application detects network connection

At a regular interval, usually every three minutes, the SIM application reads these three `LOCI` files:

* EF<sub>LOCI</sub>
* EF<sub>PSLOCI</sub>
* EF<sub>EPSLOCI</sub>

These files indicate if the modem has successfully registered on a network, or if it is still attempting to connect.

{% hint style="info" %}
For devices that have never previously connected, the modem attempts to connect according to the IMSI order configured during SIM manufacture. For devices that have previously connected to a network, the modem attempts to connect to the last successfully connected network.
{% endhint %}

If the modem is not connected, the SIM application will rotate the IMSI according to the preconfigured order. This means that if the device is deployed where the current home network is not available and does not offer a roaming service, then the SIM application will rotate to an alternative IMSI to allow the device to connect.

{% hint style="info" %}
Different companies configure their devices to implement rotation timers in different ways. For example, some customer devices use a timer to count the IMSI rotation time, whereas others count the number of status commands.
{% endhint %}

Eseye can change the rotation order after deployment.

## How the SIM changes an IMSI

When the IMSI rotates or switches, the SIM application overwrites the active bootstrap account with files from the selected account:

| File                                                      | File                   |
| --------------------------------------------------------- | ---------------------- |
| `Account 0i`                                              | EF<sub>OPL</sub>       |
| `AD SIM`                                                  | EF<sub>OPLMNwAcT</sub> |
| `Auth Counter`                                            | EF<sub>PNN</sub>       |
| `BCCH`                                                    | EF<sub>PSLOCI</sub>    |
| EF<sub>ACC</sub>                                          | EF<sub>SPN</sub>       |
| EF<sub>ACL</sub>                                          | `IMSI USIM`            |
| EF<sub>EHPLMN</sub>                                       | `Kc`                   |
| EF<sub>EPSLOCI</sub>                                      | `KI`                   |
| EF<sub>EPSNSC</sub>                                       | `OPC`                  |
| EF<sub>HPLMNwAcT</sub>                                    | `PLMNsel`              |
| EF<sub>KcGPRS</sub>                                       | `SMSP`                 |
| EF<sub>LOCI</sub>                                         |                        |
| `ISD_P` connectivity parameters for connecting to `SM-SR` |                        |

The SIM application sends a `UICC Reset` command to refresh account values in the IoT device modem. The modem uses the new account details to connect to the new home network or a [roaming partner](understanding-roaming.md).

The modem must then clear the EF<sub>FPLMN</sub> file (`6F7B`). The mobile network updates it during registration.
