# EMQPUBCLOSE – remove a publish message topic

Remove a publish message topic.

| Type  | Syntax                                                                                                                                                                                                                  | Returned Result                                                                                                                                                                                                                                                                                                      |
| ----- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Test  | AT+EMQPUBCLOSE=?                                                                                                                                                                                                        | +EMQPUBCLOSE:(0-7) OK                                                                                                                                                                                                                                                                                                |
| Read  | AT+EMQPUBCLOSE?                                                                                                                                                                                                         | OK                                                                                                                                                                                                                                                                                                                   |
| Write | AT+EMQPUBCLOSE=(0-7) where: (0-7) is a publish index number in the range from 0, up to and including 7. You must have already opened a publish topic to the selected index number, or the command will return an error. | OK +EMQPUBCLOSE:(0-7), where: - (0-7) is the publish index number you selected from the range - status is either: - 0 – subscription cancelled successfully - -2 – no topic was registered for the given index or ERROR – the command failed Check you have sent the AT+ETMSTATE="startmqtt" command to enable MQTT. |

#### Example

AT+EMQPUBCLOSE=0

OK

+EMQPUBCLOSE: 0,0

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
