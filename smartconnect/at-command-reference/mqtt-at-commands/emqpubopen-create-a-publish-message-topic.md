# EMQPUBOPEN – create a publish message topic

Create and view publish message topics, which will enable you to publish data to things in the cloud.

The topic name depends on the MQTT parameter, unless a token is used. For more information, see the \[MQTT] section, Using the AnyNet SMARTconnect™ configuration file.

You can use the following tokens to construct the topic name:

* $t – returns the cloud thingName
* $i – returns the device International Mobile Equipment Identity (IMEI) number

For example, status/$i publishes as status/

You can only include one token in a topic.

| Type  | Syntax                     | Response                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| ----- | -------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Test  | AT+EMQPUBOPEN=?            | +EMQPUBOPEN: (0-7), OK                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| Read  | AT+EMQPUBOPEN?             | List of publish topics. 0: /<\[mqtt] topicsuffix> 1: /<\[mqtt] topicsuffix> OK where: - 0, 1, and so on are the index numbers - \<publishtopi&#x63;_&#x6E;_> is the unique name for each publish index - <\[mqtt] topicsuffix> is the appended topic path. For more information, see topicsuffix. <\[mqtt] topicsuffix> may comprise of $i (IMEI) or $t (cloud thingName). $t has the following maximum lengths: - AWS – 128 characters - Google – 255 characters The sum of and <\[mqtt] topicsuffix> must not exceed the maximum size allowed by the MQTT broker, which is 256 characters for both AWS and Google. The Quectel module does not report empty topics. |
| Write | AT+EMQPUBOPEN=(0-7),"/\[$t | $i]" where: - (0-7) is a publish index number in the range from 0, up to and including 7. - is the publish topic title with a maximum length of 256 characters (including /cloudThingName or /IMEI). Topic titles cannot contain special characters. - $t or $i are optional values, described above.                                                                                                                                                                                                                                                                                                                                                                 |

#### Examples

AT+EMQPUBOPEN=0,"PublishToCloud0/$i"

OK

+EMQPUBOPEN: 0,0

AT+EMQPUBOPEN=1,"PublishToCloud1"

OK

+EMQPUBOPEN: 1,0

AT+EMQPUBOPEN?

0: PublishToCloud0/862061040777777

1: PublishToCloud1/AWSthingName

OK

AT+EMQPUBLISH=0,1,"{"imei":"$i","user":"1","sys":"128","dia":"112","pul":"075","ano":"0","time":"2023/11/30,20:10:12-20","ver":"BP01\_2.0","devdata":{"r":$r,"rat":"$a","mcc":$c,"mnc":$n,"imsi":$s,"batt":87\}}"

OK

:SEND OK

In the last example, the MQTT broker receives:

{

"imei": "867730056224474",

"user": "1",

"sys": "128",

"dia": "112",

"pul": "075",

"ano": "0",

"time": "2023/11/30,20:10:12-20",

"ver": "BP01\_2.0",

"devdata": {

"r": -68,

"rat": "eMTC",

"mcc": 310,

"mnc": 230,

"imsi": 302760007540320,

"batt": 87

}

}

For useful AWS information regarding maximum lengths, see: AWS IoT Core endpoints and quotas.

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
