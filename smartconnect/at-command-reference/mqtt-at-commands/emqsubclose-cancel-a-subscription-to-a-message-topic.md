# EMQSUBCLOSE – cancel a subscription to a message topic

Cancel a subscription to a topic.

| Type  | Syntax                 | Returned result                        |
| ----- | ---------------------- | -------------------------------------- |
| Test  | `AT+EMQSUBCLOSE=?`     | `OK` and `+EMQPUBOPEN:(0-7)`           |
| Read  | `AT+EMQSUBCLOSE?`      | `OK` or `ERROR`                        |
| Write | `AT+EMQSUBCLOSE=(0-7)` | `OK`, `+EMQSUBCLOSE:(0-7)`, or `ERROR` |

For the Write command, set a subscribe index from `0` through `7`. Subscribe to the selected index first. The response status is `0` when it cancels the subscription, `-1` when the broker returns an `unsubnack`, or `-2` when no topic exists.

#### Example

```
AT+EMQSUBCLOSE=0
OK
+EMQSUBCLOSE: 0,0
```

```
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
```
