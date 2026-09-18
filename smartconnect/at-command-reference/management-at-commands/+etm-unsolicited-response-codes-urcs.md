# +ETM Unsolicited Response Codes (URCs)

AnyNet SMARTconnect™ adds the following Eseye URCs to the module.

You will continue to observe other URCs from the module.

For information about all other URCs, see the relevant module documentation.

| URC                     | Description                                       |
| ----------------------- | ------------------------------------------------- |
| `+ETM:EMQRDY`           | MQTT mode is ready to accept `AT+EMQ` commands.   |
| `+ETM:IDLE`             | The modem is ready for commands.                  |
| `+ETM:REBOOTING`        | The modem is restarting.                          |
| `+ETM: REBOOT REQUIRED` | An update requires a restart.                     |
| `+ETMSTATE:`            | Reports the module connectivity state.            |
| `+ETM:SYSSTART`         | The AnyNet SMARTconnect™ application has started. |

Wait for `+ETM:IDLE` before sending commands after a reboot. Configure automatic rebooting with `update_autoreboot` in the [AnyNet SMARTconnect™ configuration file](../../getting-started/using-the-anynet-smartconnect-tm-configuration-file.md). Use [ETMRESET – reboot the modem](etmreset-reboot-the-modem.md) to restart manually.
