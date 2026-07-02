---
description: >-
  Eseye supplies different SIM card versions, which all support multi-IMSI functionality. This means that:
---
# Understanding multi-IMSI functionality

Eseye supplies different SIM card versions, which all support [multi-IMSI](https://docs.eseye.com/Content/Glossary/multiIMSI.htm) functionality. This means that:

- Standard SIMs (v5) are manufactured with up to ten International Mobile Subscriber Identities ([IMSIs](https://docs.eseye.com/Content/Glossary/Imsi.htm)) from different MNOs.
- eUICC SIMs (v6 and v7) can support one multi-IMSI bootstrap profile, containing up to ten IMSIs, and up to three single-IMSI operational profiles. For more information, see [About eUICC SIM profiles](e-sim/profiles.md).

  {% hint style="info" %}

  The v6 and v7 SIM cards comply with the eUICC standard.

  {% endhint %}

The [Connectivity Management Platform](https://docs.eseye.com/Content/Connectivity/ConnectivityManagementPlatform.htm) (CMP) manages adding and deleting the IMSIs on the SIM card, and a SIM application controls which IMSI is active.

When an IoT device first starts up, the device attempts to connect to a network using the currently active IMSI.

Selecting a different IMSI enables the modem to register on a different available network, using an alternative set of credentials, without having to physically swap the SIM.

{% hint style="info" %}

The mobile network that provides the active IMSI is known as the [home network](https://docs.eseye.com/Content/Glossary/HomeNetwork.htm).

{% endhint %}

{% hint style="info" %}

Registration can only occur on one mobile network at a time, either on the home network, or roaming.

{% endhint %}

{% hint style="info" %}

For eUICC-enabled devices, the active IMSI may exist within a multi-IMSI [bootstrap](e-sim/profiles.md#Bootstra) profile, or as one of the single-IMSI [operational (step 2)](e-sim/profiles.md#Operatio) profiles.

{% endhint %}

## About multi-IMSI accounts

A standard SIM or AnyNet eUICC SIM profile with multi-IMSI functionality supports up to 10 IMSI accounts, which each contain all the data needed for a modem to connect to a network. Each account is identified by its unique [IMSI](https://docs.eseye.com/Content/Glossary/Imsi.htm). The accounts enable the IoT device to use up to ten different operator networks and all their [roaming](roaming.md) partners without having to physically change the SIM.

Each IMSI account is provided by one of Eseye's [AnyNet Federation](any-net-federation.md) MNO partners.

Eseye preconfigures which IMSI accounts are available during SIM manufacture, before they are shipped to customers. During an IoT device lifetime, Eseye can load new IMSIs onto the SIM, delete IMSIs, and change how they are selected over-the-air (OTA). This is useful if you need to [localise](localisation.md) a device.

{% hint style="info" %}

For AnyNet [eUICC](e-sim/euicc.md) SIMs, Eseye can download and enable multiple [operational profiles](e-sim/profiles.md#Operatio) OTA. The [Connectivity Management Platform](https://docs.eseye.com/Content/Connectivity/ConnectivityManagementPlatform.htm) manages switching between these profiles, in a similar way to switching IMSIs within a multi-IMSI profile. For more information, see [Understanding IMSI rotation vs IMSI switching](imsirotation-switching.md).

{% endhint %}

## Benefits of access to multiple IMSIs

Having access to multiple IMSIs provides the following benefits for IoT devices:

- Greater network choice – with access to more operators, the device is more likely to connect to a network.
- Network redundancy – if the current network goes down, the device can [rotate](#ImsiRotation) through different IMSIs until a different network connection is established.
- [Localisation](localisation.md) – when the IoT device uses a local network operator, this can resolve manufacturing and deployment issues, such as avoiding roaming restrictions in the local country.
- Legislative compliance – comply with local legislative requirements, no matter where the device is deployed.
- Roaming partner access – access [roaming agreements](roaming.md) either through the active IMSI, or by [switching](imsirotation-switching.md#ImsiSwitching) IMSIs. This can enable IoT devices to connect to alternative networks.

## Where to next?

- Understand [roaming](roaming.md), [steering of roaming](roaming.md#Steering) and [localisation](localisation.md)
- [About eSIM technology](e-sim/esim.md)
- [About eUICC SIM profiles](e-sim/profiles.md)
- [AnyNet SIMs](https://docs.eseye.com/Content/HardwareProducts/SIMsIntro.htm)
- [Eseye connectivity overview](https://docs.eseye.com/Content/Connectivity/ConnectivityIntro.htm)
- [Mobile Network Operators by PoP](https://docs.eseye.com/Content/Connectivity/MNOsByPoP.htm)
- [About IP addresses](https://docs.eseye.com/Content/Connectivity/IPAddresses.htm)
- [About the AnyNet Federation](any-net-federation.md)
- [Understanding localisation](localisation.md)
