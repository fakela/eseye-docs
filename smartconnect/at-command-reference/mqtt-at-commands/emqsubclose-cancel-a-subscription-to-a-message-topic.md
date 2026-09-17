# EMQSUBCLOSE – cancel a subscription to a message topic

Cancel a subscription to a topic.

| Type  | Syntax                                                                                                                                                                                                        | Returned Result                                                                                                                                                                                                                                                                                        |
| ----- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Test  | AT+EMQSUBCLOSE=?                                                                                                                                                                                              | OK +EMQPUBOPEN:(0-7)                                                                                                                                                                                                                                                                                   |
| Read  | AT+EMQSUBCLOSE?                                                                                                                                                                                               | OK or ERROR                                                                                                                                                                                                                                                                                            |
| Write | AT+EMQSUBCLOSE=(0-7) where: (0-7) is a subscribe index number in the range from 0, up to and including 7. You must have already subscribed to the selected index number, or the command will return an error. | OK +EMQSUBCLOSE:(0-7), where: - (0-7) is the subscribe index number you selected from the range - status is either: - 0 – subscription cancelled successfully - -1 – broker returned an unsubnack - -2 – no topic was registered for the given index or ERROR – the command failed +EMQSUBCLOSE:(0-7), |

#### Example

AT+EMQSUBCLOSE=0

OK

+EMQSUBCLOSE: 0,0

AT+EMQSUBOPEN?

OK

+EMQSUBOPEN topics:

0 null

1 SubscribeFromCloud1/AWSthingName

2 null

3 null

4 null

5 null

6 null

7 null

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
