# EMQPUBOPEN – create a publish message topic

Create and view publish message topics. Use these topics to publish data to things in the cloud.

The topic name depends on the MQTT parameter unless you use a token. See [Using the AnyNet SMARTconnect™ configuration file](../../getting-started/using-the-anynet-smartconnect-tm-configuration-file.md).

You can use the following tokens to construct the topic name:

* `$t` — Returns the cloud `thingName`.
* `$i` — Returns the device International Mobile Equipment Identity (IMEI).

For example, `status/$i` publishes as `status/`.

You can only include one token in a topic.

| Type  | Syntax                              | Response                           |
| ----- | ----------------------------------- | ---------------------------------- |
| Test  | `AT+EMQPUBOPEN=?`                   | `+EMQPUBOPEN: (0-7)` and `OK`      |
| Read  | `AT+EMQPUBOPEN?`                    | A list of publish topics and `OK`  |
| Write | `AT+EMQPUBOPEN=(0-7),"/[$t \| $i]"` | Creates or updates a publish topic |

The Read command returns topics in this format:

```
0: /<[mqtt] topicsuffix>
1: /<[mqtt] topicsuffix>
OK
```

The returned topic list includes:

* An index number, starting at `0`.
* The unique publish topic name for the index.
* The appended `topicsuffix` path.

`topicsuffix` can include `$i` for the IMEI or `$t` for the cloud `thingName`. The maximum `$t` length is `128` characters for AWS and `255` characters for Google. The complete topic must not exceed the MQTT broker limit of `256` characters. The Quectel module does not return empty topics.

For the Write command:

* Set the publish index from `0` through `7`.
* Set a publish topic title up to `256` characters, including `/cloudThingName` or `/IMEI`.
* Do not use special characters in a topic title.
* Optionally include `$t` or `$i`.

#### Examples

Create a topic with the IMEI token:

```
AT+EMQPUBOPEN=0,"PublishToCloud0/$i"
OK
+EMQPUBOPEN: 0,0
```

Create a topic without a token:

```
AT+EMQPUBOPEN=1,"PublishToCloud1"
OK
+EMQPUBOPEN: 1,0
```

List publish topics:

```
AT+EMQPUBOPEN?
0: PublishToCloud0/862061040777777
1: PublishToCloud1/AWSthingName
OK
```

Publish a JSON message:

```
AT+EMQPUBLISH=0,1,"{"imei":"$i","user":"1","sys":"128","dia":"112","pul":"075","ano":"0","time":"2023/11/30,20:10:12-20","ver":"BP01\_2.0","devdata":{"r":$r,"rat":"$a","mcc":$c,"mnc":$n,"imsi":$s,"batt":87\}}"
OK
:SEND OK
```

In the last example, the MQTT broker receives:

```json
{
  "imei": "867730056224474",
  "user": "1",
  "sys": "128",
  "dia": "112",
  "pul": "075",
  "ano": "0",
  "time": "2023/11/30,20:10:12-20",
  "ver": "BP01_2.0",
  "devdata": {
    "r": -68,
    "rat": "eMTC",
    "mcc": 310,
    "mnc": 230,
    "imsi": 302760007540320,
    "batt": 87
  }
}
```

For useful AWS information regarding maximum lengths, see: AWS IoT Core endpoints and quotas.
