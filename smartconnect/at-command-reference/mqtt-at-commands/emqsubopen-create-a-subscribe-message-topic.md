# EMQSUBOPEN – create a subscribe message topic

Create and view subscribe message topics. Use these topics to send data from the MQTT broker to your thing.

The topic name depends on the MQTT parameter unless you use a token. See [Using the AnyNet SMARTconnect™ configuration file](../../getting-started/using-the-anynet-smartconnect-tm-configuration-file.md).

You can use the following tokens to construct the topic name:

* `$t` — Returns the cloud `thingName`.
* `$i` — Returns the device International Mobile Equipment Identity (IMEI).

For example, `status/$i` publishes as `status/`.

You can only include one token in a topic.

| Type  | Syntax                                    | Returned result                         |
| ----- | ----------------------------------------- | --------------------------------------- |
| Test  | `AT+EMQSUBOPEN=?`                         | Available indexes, QoS values, and `OK` |
| Read  | `AT+EMQSUBOPEN?`                          | A list of subscribe topics and `OK`     |
| Write | `AT+EMQSUBOPEN=(0-7),"/[$t \| $i]"[,qos]` | Creates or updates a subscribe topic    |

The Read command returns the index, unique topic name, and appended `topicsuffix` path. `topicsuffix` can include `$i` for the IMEI or `$t` for the cloud `thingName`. The complete topic must not exceed `256` characters. The Quectel module does not return empty topics.

For the Write command:

* Set the subscribe index from `0` through `7`.
* Set a topic title up to `256` characters, including `/cloudThingName` or `/IMEI`.
* Do not use special characters in a topic title.
* Use `topiclist` to request the current topic list.
* Optionally set QoS to `0` for at-most-once delivery or `1` for at-least-once delivery.

#### Example

```
AT+EMQSUBOPEN=0,"SubscribeFromCloud0/$i,1"
OK
+EMQSUBOPEN: 0,0
```

```
AT+EMQSUBOPEN=1,"SubscribeFromCloud1"
OK
+EMQSUBOPEN: 1,0
```

```
AT+EMQSUBOPEN?
+EMQSUBOPEN:
0: SubscribeFromCloud0/862061040777777
1: SubscribeFromCloud1/cloudThingName
OK
```
