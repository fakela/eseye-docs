# ETMHFWCONF – confirms the new host firmware is applied

Confirms the new host firmware image is applied and then deletes the image from the modem flash memory.

| Type    | Syntax        | Response                                                                                                                                                                                                                                                                          |
| ------- | ------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Execute | AT+ETMHFWCONF | OK or +ETM ERROR: – may indicate that the host firmware has not successfully downloaded onto the Quectel module. Ensure AT+ETMHFWGET completed successfully, and you have seen the +ETMHFWGET: available URC. For more information, see ETMHFWGET – checks for new host firmware. |

#### Example

AT+ETMHFWCONF

OK

## Where to next?

* AnyNet SMARTconnect™ AT Commands
* MQTT AT commands
* Sending data from your thing to the cloud
* Sending data from the cloud to your thing
* +EMQ Unsolicited Response Codes (URCs)
* Management AT commands
* +ETM Unsolicited Response Codes (URCs)
* MQTT Rx Queue
* General AT Commands
