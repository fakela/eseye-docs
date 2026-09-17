# Reducing network selection time on Quectel BGxx modules

Multi-network SIM profiles need time to connect to the best local available network for a device. While single MNO SIM profiles will take less time to connect to a network, this is only helpful if the provider is constantly available in the locale.

For Quectel modems, you can optimise the time an AnyNet SIM takes to register on a network by using the following coding best practices:

1.  Enable all URCs for `AT+CREG`, `AT+CGREG`, and `AT+CEREG`, unless you prefer to poll for this information.

    These URCs will enable you to see when the modem registers and deregisters in real time.

    If you prefer to poll for `AT+CREG`, `AT+CGREG`, and `AT+CEREG`, then the following responses are for registered modems:

    * `_n_,1`, where 1 is registered, home network
    * `_n_,5`, where 5 is registered, roaming

    Refer to the Quectel AT command documentation for more information.
2.  Using the `AT+QCFG` command with radio enabled will trigger a new radio frequency (RF) scan for different available frequencies, and will disregard if the modem is already camped on a cell, waiting for registration.

    As a result:

    1. Registration time, and therefore power consumption, will increase because of the rescan.
    2. In accordance with 3GPP, the modem will look for a different available service provider and ignore the LOCI and OPLMNwACT values stored in the SIM. This may cause an unwanted switch to a different service provider.

    The rescan triggers for the following commands:

    * band
    * iotopmode
    * nwscan
    * nwscanmode
    * nwscanseq
    * roamservice
    * servicedomain

    We recommend you read the existing values to ensure they are correct for your system.

    We recommend you disable NB-IoT if you're not using the technology, as scanning for NB-IoT bands can take a long time.

    If you must change any of these values:

    1. Use `AT+CFUN=0` to disable radio.
    2. Use `AT+QCFG` commands to make your changes, for example `AT+QCFG=“iotopmode”,0,1` to disable NB-IoT.
    3. Use `AT+CFUN=1` to enable radio.
3.  If you want to scan for LTE Cat M1 networks before scanning for 2G networks, use any of the following settings:

    * `AT+QCFG=”nwscanseq”,02,1`
    * `AT+QCFG=”nwscanseq”,020103,1`
    * `AT+QCFG=”nwscanseq”,0201,1`

    Ensure you disable radio when setting the `AT+QCFG=”nwscanseq”` values (see point 2 above).
4.  For 2G and LTE Cat M1 networks, ensure you scan for available networks for 20-30 seconds before causing changes in state, such as restarting the modem.

    The time delay must take into account the potential scan times of the LTE Cat M1 bands and the AnyNet SIM. If the time delay is too short, it is very likely that time out will occur before the device transitions to a registered status. The modem may then take additional time to restart.
5.  If you are using `AT+QENG` for additional information, do not use it to poll for registration status.

    `AT+QENG` is designed to provide information about serving cells, and the information only becomes valid after the `AT+COPS?` and `AT+CREG` commands indicate successful registration.

    If you require `QENG="servingcell"` information, request it after the registration status has changed.

## Where to next?

* [Connecting to the cloud](connecting-to-the-cloud.md)
* [General AT commands](https://app.gitbook.com/s/TZG4LrCHVlGSXoDpMgo3/at-command-reference/general-at-commands)
* 8618 Eseye-enabled Quectel BG96 module Developer Guide (PDF)
