# Understanding LTE default APNs

{% hint style="info" %}
Eseye supply a list of APNs that offer different functionality for registering a device on a mobile network. Use the correct APN (specified in your contract) for your deployment. For more information, see [Current AnyNet APN list](current-anynet-apn-list.md).
{% endhint %}

On LTE networks, if a device does not specify an APN, or if the modem automatically registers with the network before the firmware has provided the APN configuration setting, then the Mobile Network Operator (MNO) connects the devices to a preconfigured default APN.

Default APNs on LTE networks are intended for management purposes only, and not data routing. Increasingly, MNOs with LTE-only networks are preventing devices that use the default APN setting from transmitting or receiving data.

{% hint style="info" %}
As LTE-only networks become more prevalent, devices that do not specify an APN when they connect could start to experience high failure rates as they become unable to transmit or receive data. This means that Eseye will become increasingly restricted in providing the optimum connectivity for these devices, and customers may be vulnerable to legislation changes, for example, if Eseye cannot [localize devices](../../anynet-sims/how-anynet-sims-work/understanding-localisation.md) to avoid roaming restrictions.
{% endhint %}

### Current workaround

If we know that devices might connect to the default APN, we can configure our systems to avoid localizing these devices to any networks that impose data routing restrictions on default APNs. However, this creates additional complexity and reduced flexibility when optimising connectivity for these devices.

### Devices using 2G or 3G

If your deployment uses 2G or 3G networks, your devices should already connect to a specified APN, as these networks do not provide a default APN.

Many network operators have begun the process of sunsetting their 2G and 3G networks. To find out how to futureproof your deployment and gain the benefits that LTE networks offer. For more information, see IoT Guide to 2G and 3G Network Shutdowns.

## Currently implementing AnyNet service

To ensure that we can provide optimum connectivity for all the devices and offer new LTE services to our customers, the AnyNet service is provided for LTE default APNs.

For many of our interconnects, the LTE carrier does not permit data routing for default APNs. All devices must specify a valid AnyNet APN when they register with a network in order to enable traffic flow between devices and endpoints.

### Checking that the AnyNet APN is valid

Ensure that the firmware in your device configures the APN setting in the modem before the modem registers with a network. If your modem automatically registers when it starts up, it must delay registering until the firmware has written the configuration settings to the modem.

#### Check that the device is not using the default APN

To check that your device is not using the default APN:

If you have more than one APN configured for your package, you can check your device behaviour by running the steps described below. This tests whether the device is connecting to the configured APN and isn’t relying on the network’s default APN.

1. Connect to the **eseye1** APN.
   1. Configure the APN setting in your device to **eseye1**, then reboot the device.
   2. Confirm that the device is connected to **eseye1** and can transmit and receive data.
2. Connect to a different AnyNet APN.
   1. Configure the APN setting in your device to another APN defined in your package, such as **eseye.com**, then reboot the device.
   2. Check that the device is connected to the APN you specified and can transmit and receive data. If the device is not connected, it shows that the modem is not reading the APN configuration setting before registering with the network. You will need to modify the firmware to correct this.
3. Re-connect to the **eseye1** APN.
   1. Configure the APN setting in your device to **eseye1**, then reboot the device.
   2. Confirm that the device is connected to **eseye1** and can transmit and receive data.

A successful result from this test does not guarantee that a device is operating correctly. Occasionally, we have observed race conditions between modems and firmware. This can result in devices connecting to the network’s default APN, even when the firmware is correctly configured with an APN.

#### Verify changes with the Eseye device onboarding service

The Eseye device onboarding service includes a rigorous process to test how your device connects and operates within the AnyNet ecosystem. This service includes a test to confirm that your device doesn’t connect to a default APN.

{% hint style="info" %}
For more information, contact your Account Manager or [email support@eseye.com](mailto:support@eseye.com).
{% endhint %}
