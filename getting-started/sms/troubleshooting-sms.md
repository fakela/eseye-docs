---
description: >-
  This topic describes how to identify and resolve SMS-related issues including:
---
# Troubleshooting SMS

This topic describes how to identify and resolve SMS-related issues including:

- [IoT device not receiving SMS messages](#NotReceivingSms)
- [SMS messages received in wrong order](#SmsReceivedWrongOrder)
- [No delivery receipts received](#NoDeliveryReceipts)

## IoT device not receiving SMS messages

If your IoT device with an AnyNet SIM is not receiving SMS messages:

1. Check the [SMS error code](#SmsErrorCodes).
2. Check that the IoT device is connected to the network, for example by ensuring that the SIM status on the [Infinity Classic Network Settings page](https://docs.eseye.com/Content/InfinityClassic/SimActions.htm#Network) is Active.
3. Ensure that the [SMS buffer is not full](#ClearingTheSmsBuffer).

### SMS error codes

When an SMS message is not delivered, the MNO network for the destination or SMS application returns an error code indicating the reason for the failed delivery.

For more information about the error codes, contact Eseye support and provide the following information:

- For MT messages, the MSISDN to which you sent the MSISDN.
- For MO messages, the MSISDN of the originating IoT device.

### Clearing the SMS buffer

The SMS buffer stores SMS messages sent to a device until the modem deletes them. When the buffer is full, the device will not receive any further user messages or OTA commands. AnyNet SIMs contain a buffer for storing up to ten SMS messages.

Typically, messages are deleted after the device reads them or as a regular housekeeping task. Some devices don’t delete messages from the SMS buffer because the device is not expecting to receive SMS user messages, and so the firmware doesn’t include steps to check the buffer and delete messages. When the buffer is full, any OTA commands that the Eseye connectivity management platform (CMP) sends to the SIM cannot be delivered. At this point, the CMP loses the ability to manage the connectivity for that device until the SMS buffer is cleared.

To temporarily clear the SMS buffer:

1. If the device contains a removable SIM, remove the SIM card and insert it into a phone.
2. Delete the SMS messages manually.
3. Insert the SIM into the device.

## SMS messages received in wrong order

If SMS messages are being delivered but in the wrong order, contact Eseye customer support.

## No delivery receipts received

If you are not receiving delivery receipts for SMS messages that have been delivered, contact Eseye customer support.
