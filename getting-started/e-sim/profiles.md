---
description: >-
  An eUICC SIM profile acts as a virtual SIM within the SIM container. Downloading and enabling a new profile means that an IoT device can switch to a differen...
---
# About eUICC SIM profiles

An eUICC SIM profile acts as a virtual SIM within the SIM container. Downloading and enabling a new profile means that an IoT device can switch to a different network operator without the need to physically change the SIM.

Eseye provides the [Connectivity Management Platform](https://docs.eseye.com/Content/Connectivity/ConnectivityManagementPlatform.htm) (CMP) to manage loading, [switching](../imsirotation-switching.md#ImsiSwitching), and deleting profiles.

Each profile contains:

- An [ICCID](https://docs.eseye.com/Content/Glossary/Iccid.htm) to uniquely identify the profile
- One or more [IMSIs](https://docs.eseye.com/Content/Glossary/Imsi.htm), depending on the profile type, to identify the network subscriber
- Operator subscription data, including authentication credentials
- Policy rules

The content and structure of profiles is standardised to ensure interoperability between all network. Each IMSI account is provided by the mobile network to which it connects.

The number of profiles that can be stored on an eUICC is limited only by the memory available and the size of each network operator’s profile. For information about memory capacity, see the relevant [Datasheets](https://docs.eseye.com/Content/General/Files.htm#Datasheets).

You can only enable one profile at any time. The profile currently in use (enabled) is called the active profile.

![](../../.gitbook/assets/profiles.svg)

{% hint style="success" %}

For information about how eUICC IMSIs are managed OTA, see [Understanding the GSMA RSP M2M general architecture](remote-sim-provisioning.md).

{% endhint %}

{% hint style="success" %}

For information about eUICC, see [eUICC overview](euicc.md).

{% endhint %}

eUICC SIMs support the following profile types:

<details>

<summary>Bootstrap profile (also known as the provisioning profile )</summary>

eUICC SIMs are pre-configured with a [multi-IMSI](https://docs.eseye.com/Content/Glossary/multiIMSI.htm) bootstrap profile that has full access to up to ten mobile networks and their corresponding roaming agreements. This enables the device to connect to a network as soon as it starts up. For more information, see [How long does an IMSI rotation or switch take?](../imsirotation-switching.md#How).

The bootstrap profile enables communication with the [Remote SIM Provisioning](remote-sim-provisioning.md) (RSP) system when the device first starts up. With an eUICC SIM, the device can use the RSP system to download an operational profile over-the-air (OTA) and activate it to connect to a more suitable network.

{% hint style="info" %}

MNOs typically charge for RSP, so Eseye will also charge for OTA functions. These charges are detailed in your contract.

{% endhint %}

For information about how a device uses different IMSIs to connect to a network, see [Understanding the IMSI rotation and switching process](../how-imsirotate-switch-works.md).

For a comparison of bootstrap and operational profiles, see [Bootstrap profile vs operational profile comparison](bootstrap-vsoperational-profiles.md)

</details>

<details>

<summary>Operational profile (also known as a step 2 profile)</summary>

Operational profiles are single-IMSI profiles with full access to one mobile network and its corresponding roaming agreements.

The CMP manages loading and deleting operational profiles over-the-air (OTA) in an Eseye-enabled eUICC SIM. An operational profile is usually downloaded and activated after a device is deployed, to ensure that each device can [localise](../localisation.md), rather than roaming on a network within the bootstrap profile.

This is useful for ensuring your IoT devices adhere to local legislation and network policies. It is also useful if you manufacture thousands of devices that are shipped globally, and you do not know where each batch will end up.

You can use operational profiles on battery operated devices and mobile devices. For advice, contact Support ([support@eseye.com](mailto:support@eseye.com?subject=Require advice about operational (step 2) profiles for an IoT device)).

</details>

{% hint style="info" %}

You can flag the bootstrap or an operational profile as the fall-back (see below).

{% endhint %}

<details>

<summary>Test profile</summary>

Test profiles are single-IMSI profiles used for device certification, production line sampling or product demonstrations.

For more information, see [Eseye test profile](../test-profiles/eseye-test-profile.md).

eUICC SIMs can include a [GSMA Generic eUICC test profile](../test-profiles/gsma-generic-euicc-test-profile.md).

Customers must use AT commands to enable or disable the test profile.

</details>

## About fall-back and roll-back

As a safe-guard against failed connections, eUICC SIMs use fall-back and roll-back.

<details>

<summary>About fall-back</summary>

One profile is designated as the fall-back. If the active (enabled) profile loses connectivity, or is rejected, disabled, or deleted, the device enables the fall-back profile in its place after up to 23 minutes has passed. The timing depends on how the module is manufactured.

Eseye configures the fall-back using the [Connectivity Management Platform](https://docs.eseye.com/Content/Connectivity/ConnectivityManagementPlatform.htm) (CMP).

{% hint style="info" %}

The fall-back timer is separate from the multi-IMSI rotation timer, and will override multi-IMSI rotation if no connection occurs for 23 minutes.

{% endhint %}

{% hint style="info" %}

You cannot delete the profile assigned as the fall-back.

{% endhint %}

To maximise connectivity when a device first starts, Eseye usually defines a [multi-IMSI](../imsirotation-switching.md) bootstrap profile as the fall-back on an AnyNet+ SIM. This gives the device access to up to ten networks, for greater connectivity.

If the fall-back occurs as a result of connectivity failure, the CMP uses its rules-based engine to determine whether and when to attempt to switch the device back to a preferred operational profile.

#### Disabling fall-back

If a device is localised using an operational profile and the connection is stable, the CMP can define an operational profile as the fall-back, which effectively disables fall-back to the bootstrap profile. This prevents the device switching between profiles if it temporarily loses connectivity. For example, a tracking device in a car may lose connectivity if the car is parked underground overnight, but will reconnect on the fall-back profile (in this case, a single-IMSI operational profile) the next day when the car leaves the car park.

</details>

<details>

<summary>About roll-back</summary>

{% hint style="info" %}

This feature is for newly-downloaded profiles only.

{% endhint %}

After connection is established using an eUICC profile, if you load and enable a new profile and the connection fails, then the SIM rolls back to the previously connected profile. This is managed by the Connectivity Management Platform.

</details>

## Where to next?

- [Bootstrap profile vs operational profile comparison](bootstrap-vsoperational-profiles.md)
- [AnyNet SIMs](https://docs.eseye.com/Content/HardwareProducts/SIMsIntro.htm) (includes form factors)
- Understand [eSIM](esim.md)
- [About the Connectivity Management Platform](https://docs.eseye.com/Content/Connectivity/ConnectivityManagementPlatform.htm)
