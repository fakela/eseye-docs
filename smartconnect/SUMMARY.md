# Table of contents

## Getting started

* [About AnyNet SMARTconnect™](README.md)
* [Using the AnyNet SMARTconnect™ configuration file](getting-started/using-the-anynet-smartconnect-tm-configuration-file.md)
* [System lifecycle management](getting-started/system-lifecycle-management.md)

## Data exchange

* [Sending and receiving data](data-exchange/sending-and-receiving-data.md)
* [Sending data from the cloud to your thing](data-exchange/sending-data-from-the-cloud-to-your-thing.md)
* [Interacting with the AWS IoT shadow](data-exchange/interacting-with-the-aws-iot-shadow.md)
* [Connecting the Quectel BGxx module to a LwM2M server](data-exchange/connecting-the-quectel-bgxx-module-to-a-lwm2m-server.md)

## Updates

* [Over-the-air (OTA) updates](updates/over-the-air-ota-updates.md)
* [Updating AnyNet SMARTconnect™ software and host module firmware](updates/updating-anynet-smartconnect-tm-software-and-host-module-firmware.md)

## AT command reference

* [AnyNet SMARTconnect™ AT Commands](at-command-reference/anynet-smartconnect-tm-at-commands.md)
* [General AT commands](at-command-reference/general-at-commands/README.md)
  * [CCID – request unique SIM number (ICCID)](at-command-reference/general-at-commands/ccid-request-unique-sim-number-iccid.md)
  * [CREG – request network registration status](at-command-reference/general-at-commands/creg-request-network-registration-status.md)
* [MQTT AT commands](at-command-reference/mqtt-at-commands/README.md)
  * [EMQ – publish a message to singletopic](at-command-reference/mqtt-at-commands/emq-publish-a-message-to-singletopic.md)
  * [EMQPUBOPEN – create a publish message topic](at-command-reference/mqtt-at-commands/emqpubopen-create-a-publish-message-topic.md)
  * [EMQPUBLISH – publish data to a message topic](at-command-reference/mqtt-at-commands/emqpublish-publish-data-to-a-message-topic.md)
  * [EMQPUBCLOSE – remove a publish message topic](at-command-reference/mqtt-at-commands/emqpubclose-remove-a-publish-message-topic.md)
  * [EMQSUBOPEN – create a subscribe message topic](at-command-reference/mqtt-at-commands/emqsubopen-create-a-subscribe-message-topic.md)
  * [EMQSUBCLOSE – cancel a subscription to a message topic](at-command-reference/mqtt-at-commands/emqsubclose-cancel-a-subscription-to-a-message-topic.md)
  * [EMQREAD – read message from MQTT RX queue](at-command-reference/mqtt-at-commands/emqread-read-message-from-mqtt-rx-queue.md)
  * [EMQPERSIST – report a set value to the device shadow](at-command-reference/mqtt-at-commands/emqpersist-report-a-set-value-to-the-device-shadow.md)
  * [+EMQ Unsolicited Response Codes (URCs)](at-command-reference/mqtt-at-commands/+emq-unsolicited-response-codes-urcs.md)
  * [MQTT Rx Queue](at-command-reference/mqtt-at-commands/mqtt-rx-queue.md)
* [Management AT commands](at-command-reference/management-at-commands/README.md)
  * [ETMINFO – displays AnyNet SMARTconnect™ and device information](at-command-reference/management-at-commands/etminfo-displays-anynet-smartconnect-tm-and-device-information.md)
  * [ETMSTATE – check current state](at-command-reference/management-at-commands/etmstate-check-current-state.md)
  * [ETMCFG – read and write configuration file values](at-command-reference/management-at-commands/etmcfg-read-and-write-configuration-file-values.md)
  * [ETMCFGCHECK – checks if a new AnyNet SMARTconnect™ configuration file is available](at-command-reference/management-at-commands/etmcfgcheck-checks-if-a-new-anynet-smartconnect-tm-configuration-file-is-available.md)
  * [ETMFWCHECK – checks for updates to the AnyNet SMARTconnect™ application](at-command-reference/management-at-commands/etmfwcheck-checks-for-updates-to-the-anynet-smartconnect-tm-application.md)
  * [ETMHFWGET – checks for new host firmware](at-command-reference/management-at-commands/etmhfwget-checks-for-new-host-firmware.md)
  * [ETMHFWREAD – reads a section of the new host firmware image](at-command-reference/management-at-commands/etmhfwread-reads-a-section-of-the-new-host-firmware-image.md)
  * [ETMHFWCONF – confirms the new host firmware is applied](at-command-reference/management-at-commands/etmhfwconf-confirms-the-new-host-firmware-is-applied.md)
  * [ETMLW – handles the LwM2M protocol](at-command-reference/management-at-commands/etmlw-handles-the-lwm2m-protocol.md)
  * [ETMRESET – reboot the modem](at-command-reference/management-at-commands/etmreset-reboot-the-modem.md)
  * [+ETM Unsolicited Response Codes (URCs)](at-command-reference/management-at-commands/+etm-unsolicited-response-codes-urcs.md)
