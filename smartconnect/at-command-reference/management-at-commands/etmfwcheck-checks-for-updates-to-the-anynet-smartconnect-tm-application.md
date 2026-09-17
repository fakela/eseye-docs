# ETMFWCHECK – checks for updates to the AnyNet SMARTconnect™ application

This command checks the \[application] updateurl for a new AnyNet SMARTconnect™ application.

For more information, see Using the AnyNet SMARTconnect™ configuration file.

| Type    | Syntax        | Returned Result                                                                                                                                                                                                                              |
| ------- | ------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Execute | AT+ETMFWCHECK | OK +ETMFWCHECK: checking... +ETMFWCHECK: complete If a new application needs to be installed, the following URC will also appear: +ETM: REBOOT REQUIRED You must reboot the system as soon as possible. or +ETM ERROR: – the command failed. |

#### Example

AT+ETMFWCHECK

OK

+ETMFWCHECK: checking...

+ETMFWCHECK: complete

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
