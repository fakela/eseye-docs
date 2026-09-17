# eSIM and remote provisioning

An eSIM (embedded SIM) is an embedded chip that is manufactured onto a board in your device to replace the removable SIM. The information within it is rewritable, which means you can change mobile networks and enable SIM provisioning over-the-air (OTA) without needing to physically swap SIM cards.

eSIM technology is especially important for IoT devices, which may exist in remote locations and may contain embedded SIMs (without eSIM technology) that an engineer cannot swap without replacing an entire board. It also avoids the need to design a physical enclosure for multiple SIMs, saving space and simplifying device design, manufacturing, and provisioning.

{% hint style="info" %}
The GSMA defines different eSIM architectures for machine to machine (M2M) and consumer device use cases. The Eseye eSIM solution uses the M2M eSIM architecture.
{% endhint %}

eSIM technology requires devices with [eUICC SIMs](euicc-overview.md) that support the use of [operator profiles](about-euicc-sim-profiles.md), and [remote SIM provisioning systems](about-remote-sim-provisioning-rsp.md) in the network to perform the updates. Both the eUICC SIMs and remote provisioning systems must achieve GSMA certification and operator-specific certification before you can use them on a live network. This ensures security and interoperability between operators.

![](../../.gitbook/assets/eSIM_eSIM.svg)

## Eseye's eSIM solution

Eseye has agreements in place with multiple operators that enables Eseye to download profiles from operators with the best connectivity or services for the connected IoT device. The [Connectivity Management Platform](../../connectivity/about-the-connectivity-management-platform.md) can use predetermined rules to trigger the remote SIM provisioning systems to download and enable different profiles depending on the regional requirements. The available operators and services for an IoT device depend on the [package](https://app.gitbook.com/s/hPiB0Z0YdVhl1D9teuS7/#package) assigned to the device.

For IoT devices that include an [Eseye Hera router](https://app.gitbook.com/s/Y2LsJ6998Uo7AtYcmJWd/hera-200/about-the-hera-204) (EU/USA/RoW model only), there is an embedded eUICC SIM as well as a physical SIM card within the Hera hardware.
