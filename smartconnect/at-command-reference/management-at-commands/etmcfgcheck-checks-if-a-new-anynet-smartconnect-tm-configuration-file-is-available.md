# ETMCFGCHECK – checks if a new AnyNet SMARTconnect™ configuration file is available

This command checks the \[config] updateurl for a new configuration file.

For more information, see Using the AnyNet SMARTconnect™ configuration file.

| Type    | Syntax         | Returned Result                                                                                                                                                                                                                                     |
| ------- | -------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Execute | AT+ETMCFGCHECK | OK +ETMCFGCHECK: checking... +ETMCFGCHECK: complete If a new configuration file needs to be applied, the following URC will also appear: +ETM: REBOOT REQUIRED You must reboot the system as soon as possible. or +ETM ERROR: – the command failed. |

#### Example

AT+ETMCFGCHECK

OK

+ETMCFGCHECK: checking...

+ETMCFGCHECK: complete

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
