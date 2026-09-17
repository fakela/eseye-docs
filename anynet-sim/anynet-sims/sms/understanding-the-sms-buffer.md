# Understanding the SMS buffer

### SMS buffer storage <a href="#sms" id="sms"></a>

The SMS buffer functions as a storage space located on either:

* SIM: It can store up to 10 SMS messages in its storage capacity.
* Device/ Modem: It utilises different storage locations to accommodate the SMS messages. The storage capacity for these locations may have a varying capacity larger than the SMS store, and this capacity varies from device to device. After receiving an SMS, the device stores the SMS message in the default or programmed location.

Whenever the device receives SMS messages or OTA operational messages, it checks for the availability of storage space.

* If storage space is available in the buffer, the device accepts the SMS.
* If storage space is unavailable in the buffer, the device rejects the SMS.

{% hint style="warning" %}
If Eseye is unable to send the device an OTA, the device cannot access the benefits provided by Eseye through the Connectivity Management Platform services, such as enabling/ disabling IMSIs, rotation order, multi-IMSI features etc.
{% endhint %}

[![](https://docs.eseye.com/Content/Resources/Images/GetStarted/Device-SMS%20buffer_thumb_240_240.png)](https://docs.eseye.com/Content/Resources/Images/GetStarted/Device-SMS%20buffer.png)

#### Anticipated strategy

Once the device receives and reads an SMS, it should perform either of the 3 tasks:

1. Delete SMS messages to clear the SMS buffer.
2. Delete the SMS upon a restart or during routine checks.
3. Clear the buffer automatically, once it reaches a predefined message threshold.

**Deleting SMS messages from the buffer (AT+CMGD)**

To prevent the buffer from becoming full, you can routinely delete old SMS messages or set up automatic deletion options in their device settings.

To delete SMS messages from the buffer using AT+CMGD:

{% hint style="info" %}
The below procedure is generally applicable to majority of modems. However, it's advisable to consult your device manufacturer before proceeding.
{% endhint %}

Type the command in the syntax (Optional parameters are enclosed in square brackets):

```
AT+CMGD=<index>[,<flag>]
```

Where:

* \<index> represents an integer specifying the location of the SMS message to delete from the buffer.
* \[,\<flag>] represents an integer that specifies whether to delete one or more SMS messages based on their message status. The flag is either:
  * 0 – Delete only the SMS message stored at the location index from the buffer. This is the default value.
  * 1 – Ignore the value of index and delete all SMS messages whose status is received read from the buffer.
  * 2 – Ignore the value of index and delete all SMS messages whose status is received read or stored sent from the buffer.
  * 3 – Ignore the value of index and delete all SMS messages whose status is received read, stored unsent or stored sent from the message storage area
  * 4 – Ignore the value of index and delete all SMS messages from the buffer.

Example:

```
AT+CMGD=1,4
OK
```

### Performing SMS buffer test and recording observationsTo test the device’s response, Eseye sends 15 SMS messages in succession, leading to one of the following test outcomes. <a href="#performingsmsbuffertestandrecordingobservationstotestthedevicesresponseeseyesends15smsmessagesinsucc" id="performingsmsbuffertestandrecordingobservationstotestthedevicesresponseeseyesends15smsmessagesinsucc"></a>

The following scenarios outline the procedure for testing the SMS buffer and the recorded observations:

#### Test behaviour scenarios <a href="#test" id="test"></a>

**Test scenario – 1 : Using the SIM as the default storage**

| Expected behaviour                                                                                                  | Unexpected behaviour                                                                                                                                                                                                    |
| ------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Eseye services transmits 15 SMS messages at intervals of approximately 5-10 seconds.                                | Eseye transmits 15 SMS messages at intervals of approximately 5-10 seconds.                                                                                                                                             |
| Eseye looks for delivery receipts for all the 15 SMS messages.                                                      | Eseye looks for delivery receipts for all the 15 SMS messages.                                                                                                                                                          |
| Eseye receives delivery receipts confirming the successful delivery of all 15 SMS messages.                         | Eseye receives confirmation for only 10 successfully delivered SMS messages.                                                                                                                                            |
|                                                                                                                     | <ul><li>The remaining 5 SMS messages remain in the sent state but are not delivered successfully, with no delivery receipts received.</li></ul>                                                                         |
| **Conclusion** – The device deletes the received SMS messages after they are read, effectively clearing the buffer. | **Conclusion** – The device fails to delete the received SMS messages after they are read. Consequently, resulting in the buffer becoming full and unable to accept further SMS messages (until the buffer is cleared). |
| **Result outcome** – Positive                                                                                       | **Result outcome** – Negative                                                                                                                                                                                           |

**Test scenario – 2 : Using the Device as the default Storage (Considering that the device can store up to a maximum of 50 SMS messages)**

| Expected behaviour with a warning                                                                                                                                                                                                                                                                                                                                                                                     | Unexpected behaviour                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Eseye transmits 15 SMS messages at intervals of approximately 5-10 seconds.                                                                                                                                                                                                                                                                                                                                           | Eseye transmits 15 SMS messages at intervals of approximately 5-10 seconds.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| Eseye looks for delivery receipts for all the 15 SMS messages.                                                                                                                                                                                                                                                                                                                                                        | Eseye looks for delivery receipts for all the 15 SMS messages.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| Eseye receives delivery receipts confirming the successful delivery of all 15 SMS messages.                                                                                                                                                                                                                                                                                                                           | Eseye receives 15 successfully delivered SMS receipts.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
|                                                                                                                                                                                                                                                                                                                                                                                                                       | Eseye proceeds to transmit additional SMS messages to test the device.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
|                                                                                                                                                                                                                                                                                                                                                                                                                       | <ul><li>However, the device rejects these SMS messages, leaving them in the sent state but failing to deliver them successfully.</li></ul>                                                                                                                                                                                                                                                                                                                                                                                                                             |
| **Conclusion** – The device deletes received SMS messages after they are read. However, there is uncertainty regarding whether or not the buffer retains all of the 15 transmitted SMS messages.                                                                                                                                                                                                                      | **Conclusion** – The device fails to delete all the received SMS messages after they are read. This results in the buffer becoming full and unable to accept any more SMS messages (until it is cleared).                                                                                                                                                                                                                                                                                                                                                              |
| <p><strong>Subsequent events</strong> – These events might or might not occur:</p><ul><li>The outcome of this test may yield a false positive result.</li><li>Eventually, the buffer reaches its maximum threshold capacity without detection.</li><li>Consequently, the device ceases to accept further SMS messages, resulting in on-site device malfunction.</li></ul>                                             | <p><strong>Decision</strong> – Identifying faulty behaviour in a device utilizing device storage presents challenges due to:</p><ul><li>Inability to ascertain the storage location utilized by the device without receiving specific information.</li><li>Difficulty in determining the storage capacity of the device, which can vary significantly (ranging from 5 to 200 SMS messages or more).</li><li>Limited transmission of SMS messages during the testing phase, resulting in the full storage capacity of the device not being thoroughly tested.</li></ul> |
| <p><strong>Resolution</strong> – The device manufacturer clarifies about the storage architecture and the buffer utilisation.</p><p>Conduct an actual test on the device to:</p><ul><li>Determine the device's storage capacity.</li><li>Use AT commands to interrogate the device and ascertain the buffer's SMS storage capability.</li></ul><p>Access to the AT command line is not always available to Eseye.</p> |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
