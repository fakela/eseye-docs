---
description: Send and receive SMS messages with the SMS API.
tags:
  - tag: paid-add-on
    primary: true
---

# Overview

The Eseye SMS API lets you send Mobile Terminated (MT) SMS messages to AnyNet and third-party SIMs. You can:

* Send an SMS message to a destination MSISDN.
* Cancel a queued or undelivered message.
* Check the delivery status of a message.
* Send delivery receipts to an endpoint you control.

### Base URL

Send production requests to:

```
https://messaging.eseye.com
```

All requests must use HTTPS.

### Access and authentication

The SMS API is a paid service. Messages are charged according to the rates in your SMS API contract.

Request access and pricing by emailing [orders@eseye.com](mailto:orders@eseye.com?subject=Request%20SMS%20API%20pricing). Include your company name, role, phone number, and email address.

Eseye provides an SMS API username and password. Include these credentials as form fields in every request:

```
username=<username>
password=<password>
```

SMS API requests use the following content type:

```http
Content-Type: application/x-www-form-urlencoded
```

The SMS API does not use an OAuth 2.0 bearer token.

{% hint style="warning" %}
Keep your SMS API credentials secure. Do not commit them to source control, expose them in client-side applications, or include them in logs.
{% endhint %}

### SMS behaviour and limitations

* Mobile Terminated SMS messages are sent from the network to a device.
* The destination must be supplied as an MSISDN.
* A message can contain either `text` or `short_message`.
* When both fields are provided, `text` takes priority.
* The `text` field supports 7-bit or 8-bit transport.
* The `short_message` field contains hex-encoded message data.
* Assign a unique `message_id` when sending a message if you need to track, cancel, or check its status.
* A message can only be cancelled before it is delivered.
* An optional `expiry` value controls when an undelivered message expires. Enter the value in `YYYY-MM-DD hh:mm:ss` format.
* An optional `receipt_url` identifies the endpoint that receives the delivery receipt.
* When `source` is empty, the AnyNet Messaging Service sends the message.
* Successful requests return an XML response rather than JSON.
* SMS API usage is charged according to your contract.

### Support

Contact [Eseye Support](mailto:support@eseye.com?subject=SMS%20API%20support%20request) for SMS API assistance.
