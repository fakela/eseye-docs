# Device integration

The AnyNet SIM provides simple, easy integration and secure cellular connection between your thing and your chosen cloud provider, from anywhere in the world. This enables you to remotely extract data from your thing for a variety of industrial and commercial applications, such as metering, monitoring, transportation, security, and so on.

### Before you begin

Complete the following setup:

1.  [Create an AWS account](https://aws.amazon.com), or log in to an existing account.

    For setup instructions, see the [AWS account activation guide](https://aws.amazon.com/premiumsupport/knowledge-center/create-and-activate-aws-account/).
2. In **AWS IoT Core**, [create a thing with AnyNetThingType](creating-a-thing-with-anynetthingtype.md). Use the AnyNet Secure SIM number as its identifier.
3. Install the matching AnyNet Secure SIM in your IoT device.
4. Power on the modem.
5. Connect a GPS antenna.
6. Confirm the modem can acquire a network signal.

## Connecting securely to AWS

AWS provisions the AnyNet Secure SIM over a cellular network. During provisioning, the AnyNet Secure service transfers the following identity and security information to your AnyNet Secure SIM:

* The unique AWS thing name
* The Amazon Resource Name (ARN) that defines which AWS endpoint supports the thing
* A set of X.509 certificates
* An encrypted private key – AWS and the modem use key pairs for signing data

You must extract this information into the modem to enable the secure data connection from your device to the AWS IoT Core platform.

For information about monitoring provisioning progress, see [Provisioning the AnyNet Secure SIM](provisioning-the-anynet-secure-sim.md).

For information about which files to extract from the AnyNet Secure SIM, see [About AnyNet Secure SIM files](about-anynet-secure-sim-files.md).

For information about how to extract the files, see [AT+CRSM – reading files from the SIM](at+crsm-reading-files-from-the-sim.md).
