# Connecting to the cloud

[AnyNet SMARTconnect™](https://app.gitbook.com/s/TZG4LrCHVlGSXoDpMgo3/getting-started/about-anynet-smartconnect-tm)-enabled Quectel module, coupled with an AnyNet SIM, provides simple, easy integration and secure cellular connection between your thing and your chosen cloud provider, from anywhere in the world. This enables you to remotely extract data from your thing for a variety of industrial and commercial applications, such as metering, monitoring, transportation, security, and so on.

AnyNet SMARTconnect™ ensures that your thing has near constant connectivity to a cellular network. Connecting to cloud services provides a flexible and scalable solution for your Internet of Things enterprise.

## How connectivity is established with the cloud

AnyNet SMARTconnect™ uses the Message Queue Telemetry Transport (MQTT) protocol to connect one or more things (MQTT clients) with the cloud MQTT broker (for example, AWS IoT Core).

You use an AT command interface to send and receive telemetry data to and from the cloud service. For more information, see [AT commands](https://app.gitbook.com/s/TZG4LrCHVlGSXoDpMgo3/at-command-reference/at-commands).

AnyNet SMARTconnect™-enabled Quectel modules use the following:

*   MQTT URL – the endpoint used to establish a connection between a thing and a cloud service such as AWS IoT Core, for example:

    ```
    a2efgh321joea3-ats.iot.eu-west-1.amazonaws.com
    ```
* Transport Layer Security (TLS) – for the IP connection
* Publish and subscribe topics – preconfigured in the AnyNet SMARTconnect™ application using AT commands
* MQTT ClientID
* Cloudthingname – the MQTT client ID that uniquely identifies the client to the cloud provider and may be included in the topics

For information about how to configure these settings, see [Using the AnyNet SMARTconnect™ configuration file](https://app.gitbook.com/s/TZG4LrCHVlGSXoDpMgo3/getting-started/using-the-anynet-smartconnect-tm-configuration-file).

## Where to next?

* Creating the essential AnyNet files
* [MQTT AT commands](https://app.gitbook.com/s/TZG4LrCHVlGSXoDpMgo3/at-command-reference/mqtt-at-commands)
* [Management AT commands](https://app.gitbook.com/s/TZG4LrCHVlGSXoDpMgo3/at-command-reference/management-at-commands)
* [General AT commands](https://app.gitbook.com/s/TZG4LrCHVlGSXoDpMgo3/at-command-reference/general-at-commands)
* [Updating the modem firmware using AWS IoT jobs – Quectel module](updating-the-modem-firmware-using-aws-iot-jobs-quectel-module.md)
