# EMQPERSIST – report a set value to the device shadow

Report a set value to the device shadow/twin. The operation depends on which AWSSHADOW mode you set, either simple or complete.

You set AWSSHADOW in the Configuration File. For more information, see Using the AnyNet SMARTconnect™ configuration file. Alternatively, send: AT+ETMCFG="mqtt","awsshadow","\<off/simple/complete>", for example: AT+ETMCFG="mqtt","awsshadow","simple"

## AWSSHADOW simple mode

The shadow AnyNet SMARTconnect™ performs the following automatically:

* Generates the JSON state and reported or desired objects
* Subscribes to the shadow/update/delta topic, and filters out the containing objects
* Presents the host with the state object JSON content only, sent via URC

The host only sends the content of the reported object.

## AWSSHADOW complete mode

The host sends the complete JSON for the shadow to AnyNet SMARTconnect™.

AnyNet SMARTconnect™ sends the complete shadow message as a URC, without filtering.

## EMQPERSIST commands

| Type  | Syntax                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                | Returned Result            |
| ----- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------- |
| Test  | AT+EMQPERSIST=?                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       | +EMQPERSIST: OK            |
| Read  | AT+EMQPERSIST?                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        | OK or ERROR                |
| Write | AT+EMQPERSIST= where JSON is the JSON code, which depends on the AWSSHADOW mode you configured. For simple mode: Either the content of the state reported object or desired object is required, in this format: AT+EMQPERSIST="{"key":value}" where value is a numeric value, including decimals and negative numbers. If the passed-in text does not include reported or desired, then reported is assumed. The state reported encapsulation is appended. If the passed-in text includes reported and/or desired, only the state encapsulation is appended. For example, for the reported text: "{"key":"value"}" and "{"reported":{"key":"value"\}}" are both sent as {"state":{"reported":{"key":"value"\}}} For example, for reported and desired text: "{"reported":{"key":"value"},"desired":{"key":"value"\}}" is sent as {"state":{"reported":{"key":"value"},"desired":{"key":"value"\}}}. For complete mode: The complete JSON data for the shadow/update topic is required, in this format: AT+EMQPERSIST="{"state":{"reported":{"key":value\}}}" where value is a numeric value, including decimals and negative numbers. | OK :SEND OK or +ETM ERROR: |

#### Examples

For Simple mode:

AT+EMQPERSIST="{"Temperature":-3.5}"

AT+EMQPERSIST="{"Colour":"Blue"}"

For Complete mode, including setting AWSSHADOW to complete:

AT+ETMCFG="mqtt","awsshadow","complete"

AT+EMQPERSIST="{"state":{"reported":{"Temperature":28.0\}}}"

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
