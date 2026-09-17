# SMS

The Short Message Service (SMS) is a text messaging service supported on circuit-switched radio access networks (2G and 3G). It also works with packet-switched networks (4G and 5G) through circuit-switched fallback or SMS over IMS.

{% hint style="warning" %}
Eseye does not support SMS over IMS. For more information, contact your Account Manager.
{% endhint %}

IoT devices use [SMS](https://app.gitbook.com/s/hPiB0Z0YdVhl1D9teuS7/#sms) messages to send data to devices or applications. They can also receive SMS messages and over-the-air (OTA) network commands.

## AnyNet Messaging Service

The Eseye AnyNet Messaging Service controls the SMS messages sent to and from IoT devices with Eseye SIMs using interconnects with partner MNO core networks.

![](../../.gitbook/assets/GetStarted_AnyNetMessagingService.svg)

The AnyNet Messaging Service treats incoming messages and outgoing messages separately. The delivery paths are logically separated into:

* Mobile-originated (MO) – path originating from an IoT device with an AnyNet SIM.
* Mobile-terminated (MT) – path terminating on messages delivered to an IoT device with an AnyNet SIM.

{% hint style="info" %}
Incoming and outgoing SMS messages are queued at each Eseye PoP and not distributed across them
{% endhint %}

Eseye also provide an [SMS API](https://app.gitbook.com/s/aiPE40QazSAHFwL3em9A/sms/sms-api) that customers can use to create applications to send and receive SMS messages via the AnyNet Messaging Service. These SMS API generated messages are charged according to the charges outlines on your SMS API contract.

To add or remove IP addresses that can call the SMS API:

1. In Infinity Classic, open [**Settings** → **Messaging API**](https://app.gitbook.com/s/2pbiEZepRfUhnzoMb7nU/manage-your-sim-estate/configure-your-sim-estate/configure-the-messaging-api).
2.  For the API username, select **Edit** under **Action**.

    ![](../../.gitbook/assets/InfinityClassic_MessagingApiEdit.png)
3. Select **API Whitelist Enable**.
4. In **API Whitelist of IP Addresses**, enter a comma-separated list of IP addresses.

### SMS billing records

For more information about SMS billing records, see Understanding SMS charges on the CSV invoice.

### Allowlists and Blocklists

Eseye provides a database of allowed and blocked MSISDNs it checks when sending SMS messages. To add or remove MSISDNs from the database, contact Support.

## Mobile originated (MO) SMS messages

IoT devices with an AnyNet SIM can send MO SMS messages to:

* A user device as a text message.
* A customer application that integrates with the [SMS API](https://app.gitbook.com/s/aiPE40QazSAHFwL3em9A/sms/sms-api).

SMS messages are sent through the radio access network and are intercepted by the Eseye AnyNet Messaging Service, which controls the routing and [billing of SMS messages](https://app.gitbook.com/s/2pbiEZepRfUhnzoMb7nU/reports/finance-reports#sms-billing-activity-pdf-csv).

IoT devices can send MO messages to the MSISDN(s) configured in Infinity Classic on the [**Settings** → **Messaging API**](https://app.gitbook.com/s/2pbiEZepRfUhnzoMb7nU/manage-your-sim-estate/configure-your-sim-estate/configure-the-messaging-api) page. For each account, Infinity Classic supports creating multiple MSISDNs to which to send MO SMS messages, with each MSISDN being configured to forward the message to a different URL.

## Mobile terminated (MT) SMS messages

Customers with IoT devices using AnyNet SIMs can send SMS messages to their device (MT) using any of the following methods:

* By sending a text message to the primary MSISDN for the device.
* Using an application that is integrated with Eseye's [SMS API](https://app.gitbook.com/s/aiPE40QazSAHFwL3em9A/sms/sms-api).

When sending SMS messages to devices with [multi-IMSI](../how-anynet-sims-work/understanding-multi-imsi-functionality.md) AnyNet SIMs, the AnyNet Messaging Service sends SMS messages to the primary MSISDN associated with every IMSI on the SIM. This ensures that the SMS is delivered irrespective of the currently active IMSI. All SMS messages sent to non-active IMSIs will not be delivered and so only the SMS sent to the currently active IMSI will be successful and charged.
