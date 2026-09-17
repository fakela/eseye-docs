# EMQREAD – read message from MQTT RX queue

AnyNet SMARTconnect™ can store up to three MQTT messages in a queue in the Quectel module’s volatile memory.

AT+EMQREAD reads the stored messages.

| Type  | Syntax       | Returned Result                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| ----- | ------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Test  | AT+EMQREAD=? | OK                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| Read  | AT+EMQREAD?  | OK                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| Write | AT+EMQREAD   | +EMQREAD: S,\r\n OK or +EMQREAD: ,\r\n OK or +EMQREAD: NO MESSAGE OK where: - S is for singletopic only. Indicates data received on a single topic. For information about singletopic, see EMQ – publish a message to singletopic. - is the subscribed topic index number, not for singletopic use - is the length of the incoming data - is the received data in either ASCII-hex format or as text, depending on both the urcautoformat setting in the configuration file, and if appears within quotes. For example, if the urcautoformat setting = 1, then: - ,\r\n"" reports data in ASCII-hex format - ,\r\n reports data in text format For more information, see Using the AnyNet SMARTconnect™ configuration file. |

#### Example

AT+EMQREAD

+EMQREAD: 0,20

Example data message

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
