# +ETM Unsolicited Response Codes (URCs)

AnyNet SMARTconnect™ adds the following Eseye URCs to the module.

You will continue to observe other URCs from the module.

For information about all other URCs, see the relevant module documentation.

| URC                                                               | Description                                                                                                                                                                                                                                                                                                                                                            |
| ----------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| +ETM:EMQRDY                                                       | ETM has entered MQTT mode and is ready to accept any AT+EMQ... commands. Prior to this, only AT+ETM... commands are accepted.                                                                                                                                                                                                                                          |
| +ETM:IDLE                                                         | The modem has started up and is ready for commands.                                                                                                                                                                                                                                                                                                                    |
| +ETM:REBOOTING                                                    | The modem will shortly restart. Wait for +ETM:IDLE before sending commands. Configure automatic rebooting using update\_autoreboot in the configuration file. For more information, see Using the AnyNet SMARTconnect™ configuration file.                                                                                                                             |
| +ETM: REBOOT REQUIRED                                             | The modem has received an update and needs to restart. While operation can continue as normal, the host should issue AT+ETMRESET at a convenient time. This restarts the device and applies the update. Configure automatic rebooting using update\_autoreboot in the configuration file. For more information, see Using the AnyNet SMARTconnect™ configuration file. |
| +ETMSTATE: where is the current connectivity state of the module. | Enable this response using the AT+ETMSTATE write command. For more information, see ETMSTATE – check current state.                                                                                                                                                                                                                                                    |
| +ETM:SYSSTART                                                     | Indicates that AnyNet SMARTconnect™ application has started.                                                                                                                                                                                                                                                                                                           |

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
