# Understanding multi-IMSI functionality

Eseye supplies different SIM card versions, which all support multi-IMSI functionality. This means that:

* Standard SIMs (v5) are manufactured with up to ten International Mobile Subscriber Identities (IMSIs) from different MNOs.
*   eUICC SIMs (v6 and v7) can support one multi-IMSI bootstrap profile, containing up to ten IMSIs, and up to three single-IMSI operational profiles. For more information, see [About eUICC SIM profiles](../esim-and-remote-provisioning/about-euicc-sim-profiles.md).

    <div data-gb-custom-block data-tag="hint" data-style="info" class="hint hint-info"><p>The v6 and v7 SIM cards comply with the eUICC standard.</p></div>

The [Connectivity Management Platform](../../connectivity/about-the-connectivity-management-platform.md) manages adding and deleting the IMSIs on the SIM card, and a SIM application controls which IMSI is active.

When an IoT device first starts up, the device attempts to connect to a network using the currently active IMSI.

Selecting a different IMSI enables the modem to register on a different available network, using an alternative set of credentials, without having to physically swap the SIM.

> The mobile network that provides the active IMSI is known as the [home network](https://app.gitbook.com/s/hPiB0Z0YdVhl1D9teuS7/#home-network).

{% hint style="info" %}
Registration can only occur on one mobile network at a time, either on the home network, or [roaming](understanding-roaming.md). For eUICC-enabled devices, the active IMSI may exist within a multi-IMSI [bootstrap](../esim-and-remote-provisioning/about-euicc-sim-profiles.md) profile, or as one of the single-IMSI [operational (step 2)](../esim-and-remote-provisioning/about-euicc-sim-profiles.md) profiles
{% endhint %}

## About multi-IMSI accounts

A standard SIM or AnyNet eUICC SIM profile with multi-IMSI functionality supports up to 10 IMSI accounts, which each contain all the data needed for a modem to connect to a network. Each account is identified by its unique IMSI. The accounts enable the IoT device to use up to ten different operator networks and all their [roaming partners](understanding-roaming.md) without having to physically change the SIM.

Each IMSI account is provided by one of Eseye's [AnyNet Federation](about-the-anynet-federation.md) MNO partners.

Eseye preconfigures which IMSI accounts are available during SIM manufacture, before they are shipped to customers. During an IoT device lifetime, Eseye can load new IMSIs onto the SIM, delete IMSIs, and change how they are selected over-the-air (OTA). This is useful if you need to [localise](understanding-localisation.md) a device.

{% hint style="info" %}
For AnyNet [eUICC SIMs](../esim-and-remote-provisioning/euicc-overview.md), Eseye can download and enable multiple [operational profiles](../esim-and-remote-provisioning/about-euicc-sim-profiles.md) OTA. The [Connectivity Management Platform](../../connectivity/about-the-connectivity-management-platform.md) manages switching between these profiles, in a similar way to switching IMSIs within a multi-IMSI profile. For more information, see [Understanding IMSI rotation vs IMSI switching](understanding-imsi-rotation-vs-imsi-switching.md).
{% endhint %}

## Benefits of access to multiple IMSIs

Having access to multiple IMSIs provides the following benefits for IoT devices:

* **Greater network choice** – with access to more operators, the device is more likely to connect to a network.
* **Network redundancy** – if the current network goes down, the device can rotate through different IMSIs until a different network connection is established.
* **Localisation** – when the IoT device uses a local network operator, this can resolve manufacturing and deployment issues, such as avoiding [roaming restrictions](understanding-roaming.md) in the local country.
* **Legislative compliance** – comply with local legislative requirements, no matter where the device is deployed.
* **Roaming partner access** – access roaming agreements either through the active IMSI, or by [switching IMSIs](understanding-imsi-rotation-vs-imsi-switching.md). This can enable IoT devices to connect to alternative networks.
