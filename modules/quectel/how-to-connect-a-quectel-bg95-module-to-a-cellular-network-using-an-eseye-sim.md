# How to connect a Quectel BG95 module to a cellular network using an Eseye SIM

You can connect to a cellular network using a Quectel BG95 module and Eseye eUICC or AnyNet SIM. The following steps will help you through three stages of the network connection process:

1. Configuring automatic network operator selection.
2. Checking the network registration status.
3. Ensuring you can send and receive data.

Eseye tested the following steps on the BG95-M3. Steps may vary on different BG95 module variants.

### Before you begin

* Configure the device and Quectel BG95 module according to the manufacturer instructions. For example, ensure you have installed the correct drivers.
* Fully insert the Eseye SIM into your device.
* Ensure the Eseye SIM is activated on the Infinity Classic portal.
* Ensure the device is on and the Quectel BG95 module is powered up.
* Configure a terminal emulator to send commands to the Quectel BG95 module.

To connect a Quectel BG95 module to a cellular network:

1.  Using the terminal emulator, verify the device is reading the SIM correctly by requesting the ICCID and IMSI. Type:

    ```
    AT+CCID
    AT+CIMI
    ```

    is the end-of-line character marking the end of a command line (alias \r – carriage return).

    Make a note of the returned numbers in the event you need to ask for assistance later.
2.  Using the terminal emulator, configure the Quectel BG95 module for minimum functionality. Type:

    ```
    AT+CFUN=0
    ```
3.  Configure automatic searching of all Radio Access Technology (RAT) types, to include GSM (2G) and LTE (Cat M1). Type:

    ```
    AT+QCFG="nwscanmode",0,1
    ```
4.  Configure the RAT search sequence in the following order: LTE Cat M1 -> GSM -> LTE Cat NB1. Type:

    ```
    AT+QCFG="nwscanseq",020103,1
    ```
5.  Configure the device to search all available frequency bands. Type:

    ```
    AT+QCFG="band",0,100002000000000F0E189F,10004200000000090E189F
    ```

    The advanced user may want to limit the number of bands searched, which is beyond the scope of this topic.
6.  Set the mobile network operator selection to automatic. Type:

    ```
    AT+COPS=0
    ```

    The response will include the current network operator and access technology.
7.  Define the PDP context to route data through Eseye's APN. Type:

    ```
    AT+CGDCONT=,"",""
    ```

    where is the context ID, is the IP connection type, and is the relevant Eseye Access Point Name.

    For example:

    ```
    AT+CGDCONT=1,"IP","eseye1"
    ```

    For information about which Eseye APN to use, speak to your Account Manager. Also see [Current AnyNet APN list](https://app.gitbook.com/s/zlTL8FVu6GaQkB5i1TRY/connectivity/access-point-names/current-anynet-apn-list).
8.  Configure the module for full functionality. Type:

    ```
    AT+CFUN=1
    ```
9.  Set the mode to enable +CREG, +CGREG, and +CEREG unsolicited result codes. Type:

    ```
    AT+CREG=1;+CGREG=1;+CEREG=1
    ```

    For detailed information about AT+CREG, see CREG – request network registration status. For details about AT+CGREG and AT+CEREG, refer to the Quectel AT Commands manual for your module.
10. Check the network operator selection. Type:

    ```
    AT+COPS?
    ```

    The response includes the operator and the access technology selected. The following example response is for Verizon in LTE Cat M1 mode:

    ```
    +cops: 0,0,"Verizon ",8
    ```

    The following example response is for T-Mobile in GSM mode:

    ```
    +cops: 0,0,"T-Mobile USA",0
    ```
11. Check the active RAT and determine the signal strength. Type:

    ```
    AT+QCSQ
    ```
12. Check the network registration state per network type. Type:

    ```
    AT+CREG?;+CEREG?;+CGREG?
    ```

    The response includes the mode you set earlier and the registration status, which is either:

    * 0 – Not registered, the device is currently not searching for new operator.
    * 1 – Registered to home network.
    * 2 – Not registered, but the device is currently searching for a new operator.
    * 3 – Registration denied.
    * 4 – Unknown. For example, out of range.
    * 5 – Registered, roaming. The device is registered on a foreign (national or international) network.

    | Example response | Network type                     |
    | ---------------- | -------------------------------- |
    | +CREG: 1,1       | 2G – GSM (circuit switched)      |
    | +CGREG: 1,1      | 2G data – GPRS (packet switched) |
    | +CEREG: 1,5      | Cat M1 or NB-IoT                 |

    Factors contributing to SIM failure to register on the network may include:

    * Missing network coverage
    * Denied network access
    * No valid roaming agreement between the home network and currently available operators
13. Open a data context. Type:

    ```
    AT+CGATT=1
    ```

    If the response is OK, the device can send and receive data. If ERROR or +CME ERROR is returned, the attempt to open a data context has failed. Refer to the Quectel AT Commands manual for more information.
14. Check the allocated IP address. If you registered to the correct APN, this matches the IP address on the RADIUS log in Infinity Classic. Type:

    ```
    AT+CGPADDR
    ```
15. Use the AnyNet Ping service to ensure you can send and receive data packets. Type:

    ```
    AT+QPING=1,"192.168.109.2"
    ```

    A successful response is similar to the following:

    ```
    OK

    +QPING: 0,"192.168.109.2",32,744,255

    +QPING: 0,"192.168.109.2",32,257,255

    +QPING: 0,"192.168.109.2",32,234,255

    +QPING: 0,"192.168.109.2",32,238,255

    +QPING: 0,4,4,0,234,744,368
    ```

## Where to next?

* eUICC overview
* Find out about bootstrap and operational profiles: About eUICC SIM profiles
* [About the AnyNet Ping service](https://app.gitbook.com/s/zlTL8FVu6GaQkB5i1TRY/connectivity/monitoring-and-diagnostics/about-the-anynet-ping-service)
* [Reducing network selection time on Quectel BGxx modules](reducing-network-selection-time-on-quectel-bgxx-modules.md)
* About Access Point Names (APNs)
* AnyNet security options
