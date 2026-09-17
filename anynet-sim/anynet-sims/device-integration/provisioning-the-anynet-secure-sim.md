# Provisioning the AnyNet Secure SIM

## Provisioning the AnyNet Secure SIM

Eseye automatically provisions the AnyNet Secure SIM. This process downloads and programs security and identity information to the SIM.

### Monitor provisioning

Monitor provisioning progress in the [AWS IoT Device Shadow](https://docs.aws.amazon.com/iot/latest/developerguide/iot-device-shadows.html). Access the shadow with Lambda functions, programmatically, or through the AWS IoT console.

### Provisioning duration

Provisioning usually completes within five to 10 minutes. It can take up to one hour. Some modules reset up to four times during provisioning.

If the device restarts the modem regularly, file delivery can slow down. Allow the modem to register and remain registered while downloading updates.

If your AnyNet Secure SIM does not connect within 24 hours, [contact Support](mailto:support@eseye.com).

For details about the provisioned data, see [About AnyNet Secure SIM files](about-anynet-secure-sim-files.md).

### Wait for provisioning to finish

Wait for the `+ETM: IDLE` URC before using the device to send or receive commands.
