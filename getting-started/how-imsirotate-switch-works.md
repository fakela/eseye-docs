---
description: >-
  For both IMSI rotation and IMSI switching, the process of how the IMSI changes within the SIM is the same. However, different factors will influence an IMSI ...
---
# Understanding the IMSI rotation and switching process

For both IMSI rotation and IMSI switching, the process of how the IMSI changes within the SIM is the same. However, different factors will influence an IMSI rotation versus an IMSI switch.

For IMSI rotation, an application in the SIM triggers a rotation if it detects that there is no network connection for a period of time. For IMSI switching, the Connectivity Management Platform can instruct a SIM that is connected to a network to immediately change IMSI.

For more information, see:

- [Understanding IMSI rotation vs IMSI switching](imsirotation-switching.md)
- [How the SIM application detects network connection](#How2)
- [About the Connectivity Management Platform](https://docs.eseye.com/Content/Connectivity/ConnectivityManagementPlatform.htm)

## How the SIM application detects network connection

At a regular interval (usually three minutes), the SIM application reads three LOCI files within the SIM:

- EFLOCI
- EFPSLOCI
- EFEPSLOCI

These files indicate if the modem has successfully registered on a network, or if it is still attempting to connect.

{% hint style="info" %}

For devices that have never previously connected, the modem will attempt to connect according to the IMSI order that was configured during SIM manufacture. For devices that have previously connected to a network, the modem will attempt to connect to the last successfully connected network.

{% endhint %}

If the modem is not connected, the SIM application will rotate the IMSI according to the preconfigured order. This means that if the device is deployed where the current home network is not available and does not offer a roaming service, then the SIM application will rotate to an alternative IMSI to allow the device to connect.

{% hint style="info" %}

Different companies configure their devices to implement the rotation timers in different ways. For example, some customer devices use a timer to count the IMSI rotation time, whereas other customer devices count the number of status commands.

{% endhint %}

Eseye can change the rotation order after the device is deployed.

## How the SIM changes IMSI

When the IMSI either rotates or switches, the SIM application overwrites the active bootstrap account with the following files from the newly selected account:

|  |  |
| --- | --- |
| - Account   0i | - EFOPL |
| - AD   SIM | - EFOPLMNwAcT |
| - Auth Counter | - EFPNN |
| - BCCH | - EFPSLOCI |
| - EFACC | - EFSPN |
| - EFACL | - IMSI   USIM |
| - EFEHPLMN | - Kc |
| - EFEPSLOCI | - KI |
| - EFEPSNSC | - OPC |
| - EFHPLMNwAcT | - PLMNsel |
| - EFKcGPRS | - SMSP |
| - EFLOCI |  |
| - ISD\_P connectivity parameters, for connecting to SM-SR | |

The SIM application then uses a UICC Reset command to instruct the IoT device modem to refresh the account values. The modem uses the new account details to try and connect to the new home network, or a roaming network.

At this point, the modem must clear the EFFPLMN file (6F7B), which is then updated by the mobile network during the registration process.
