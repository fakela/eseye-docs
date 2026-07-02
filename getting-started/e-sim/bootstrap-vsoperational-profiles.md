---
description: >-
  The following table compares loading profiles onto the bootstrap, or via Remote SIM Provisioning (RSP) as an operational profile:
---
# Bootstrap profile vs operational profile comparison

The following table compares loading profiles onto the bootstrap, or via Remote SIM Provisioning (RSP) as an operational profile:

| Title | Bootstrap profile | Operational profile |
| --- | --- | --- |
| Security | This is a secure option. Profiles are loaded in a controlled environment during the manufacturing process, while the SIM is physically accessible.  Eseye can also load profiles to the bootstrap over-the-air (OTA).   Eseye keeps the profiles in a secure store. In the unlikely event that unused profiles are stolen, they cannot function until they are provisioned. You cannot clone a profile for simultaneous use in a different device, owing to non-resettable counters used in each SIM. SIM keysets are exclusively held by a third party responsible for their encryption, who have the processes and accreditations to manage the keysets for their existing MNO customers. | Eseye adheres to GSMA standards regarding remote SIM provisioning (RSP), which ensures that the profile is secure at every point during download, installation, and activation. |
| Download mechanism | Eseye uses SMS when loading profiles OTA. The profile is partitioned, and each segment is encrypted. The encrypted SMS messages are sent sequentially to the device. If the modem goes offline, SMS messages remain queued, and delivery triggers when the device next connects to the network.  The bootstrap-destined profile may require several connect cycles to complete. | The SM-SR owner sends an SMS to trigger the SIM to request the new profile. The SIM uses the modem to open a new data context to a management APN, and then uses this connection to fetch the profile via HTTPS.  If the profile download is in progress, the firmware must ensure that the modem connection time is extended until it completes. If the fetch is interrupted, it must start from the beginning. |

## Where to next?

- [About eUICC SIM profiles](profiles.md)
- [About Remote SIM Provisioning (RSP)](remote-sim-provisioning-overview.md)
- [Modules supporting Remote SIM Provisioning (RSP)](modules-supporting-rsp.md)
- [Understanding the GSMA RSP M2M general architecture](remote-sim-provisioning.md)
- [About eSIM technology](esim.md)
- [Understanding IMSI rotation vs IMSI switching](../imsirotation-switching.md)
- [AnyNet SIMs](https://docs.eseye.com/Content/HardwareProducts/SIMsIntro.htm)
