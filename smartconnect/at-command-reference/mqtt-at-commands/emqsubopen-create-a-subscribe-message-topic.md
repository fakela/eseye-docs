# EMQSUBOPEN – create a subscribe message topic

Create and view subscribe message topics, which will enable you to send data from the MQTT broker to your thing.

The topic name depends on the MQTT parameter, unless a token is used. For more information, see the \[MQTT] section, Using the AnyNet SMARTconnect™ configuration file.

You can use the following tokens to construct the topic name:

* $t – returns the cloud thingName
* $i – returns the device International Mobile Equipment Identity (IMEI) number

For example, status/$i publishes as status/

You can only include one token in a topic.

| Type  | Syntax                       | Returned Result                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| ----- | ---------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Test  | AT+EMQSUBOPEN=?              | +EMQSUBOPEN:(0-7),\[,qos] +EMQSUBOPEN: "topiclist" OK                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| Read  | AT+EMQSUBOPEN?               | List of subscribe topics. 0: /<\[mqtt]topicsuffix> 1: /<\[mqtt]topicsuffix> OK where: - 0, 1, and so on are the index numbers - \<subscribetopi&#x63;_&#x6E;_> is the unique name for each subscribe index - <\[mqtt] topicsuffix> is the appended topic path. For more information, see topicsuffix. <\[mqtt] topicsuffix> may comprise of $i (IMEI) or $t (cloud thingName). $t has the following maximum lengths: - AWS – 128 characters - Google – 255 characters The sum of and <\[mqtt] topicsuffix> must not exceed the maximum size allowed by the MQTT broker, which is 256 characters for both AWS and Google. - The Quectel module does not report empty topics. |
| Write | AT+EMQSUBOPEN=(0-7), " /\[$t | $i]"\[,qos] or AT+EMQSUBOPEN="topiclist" where: - (0-7) is a subscribe index number in the range from 0, up to and including 7. - is the subscribe topic title with a maximum length of 256 characters (including /cloudThingName or /IMEI). Topic titles cannot contain special characters. - topiclist requests a list of the subscribe topics and their current state - $t or $i are optional values, described above. - qos is the optional Quality of Service value, either: 0 (default) – at most once, no guarantee of message receipt 1 – the message is sent or delivered to the receiver one or more times                                                        |

#### Example

AT+EMQSUBOPEN=0,"SubscribeFromCloud0/$i,1"

OK

+EMQSUBOPEN: 0,0

AT+EMQSUBOPEN=1,"SubscribeFromCloud1"

OK

+EMQSUBOPEN: 1,0

AT+EMQSUBOPEN?

+EMQSUBOPEN:

0: SubscribeFromCloud0/862061040777777

1: SubscribeFromCloud1/cloudThingName

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
