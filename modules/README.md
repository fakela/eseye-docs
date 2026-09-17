# Connect a Quectel module to a cellular network

You can connect to a cellular network using a Quectel module and Eseye eUICC or AnyNet SIM. This procedure covers automatic operator selection, network registration, and data connectivity.

### Before you begin

* Configure the device and Quectel module according to the manufacturer instructions. Ensure you have installed the correct drivers.
* Fully insert the Eseye SIM into your device.
* Ensure the Eseye SIM is activated on the Infinity Classic portal.
* Ensure the device is on and the Quectel module is powered up. If you use an LTE IoT 2 click, see [powering-up-the-quectel-module.md](quectel/powering-up-the-quectel-module.md "mention").
* Configure a terminal emulator to send commands to the Quectel module. If you use an LTE IoT 2 click, see [connecting-to-the-quectel-module-using-a-terminal-emulator.md](quectel/connecting-to-the-quectel-module-using-a-terminal-emulator.md "mention").

To connect a Quectel module to a cellular network:

1.  Using the terminal emulator, request the ICCID and IMSI to verify the device reads the SIM:

    ```
    AT+CCID
    AT+CIMI
    ```

    `\r` is the end-of-line character that ends a command line.

    Record the returned numbers for any later support request.
2.  Configure the Quectel module for minimum functionality:

    ```
    AT+CFUN=0
    ```
3.  Configure automatic searching of all Radio Access Technology (RAT) types, including GSM (2G) and LTE (Cat M1):

    ```
    AT+QCFG="nwscanmode",0,1
    ```
4.  Enable roaming so the SIM can connect while roaming:

    ```
    AT+QCFG="roamservice",2,1
    ```
5.  Configure the RAT search sequence as LTE Cat M1, GSM, then LTE Cat NB1:

    ```
    AT+QCFG="nwscanseq",020103,1
    ```
6.  Configure the device to search all available frequency bands:

    ```
    AT+QCFG="band",0000000F,400A0E189F,A0E189F
    ```

    The advanced user may want to limit the number of bands searched, which is beyond the scope of this topic.
7.  Define the PDP context to route data through Eseye's APN:

    ```
    AT+CGDCONT=,"",""
    ```

    Replace the values with the context ID, IP connection type, and Eseye Access Point Name.

    For example:

    ```
    AT+CGDCONT=1,"IP","eseye1"
    ```

    For information about which Eseye APN to use, speak to your Account Manager. Also see Current AnyNet APN list.
8.  Configure the module for full functionality:

    ```
    AT+CFUN=1
    ```
9.  Set the mode to enable `+CREG`, `+CGREG`, and `+CEREG` unsolicited result codes:

    ```
    AT+CREG=1;+CGREG=1;+CEREG=1
    ```

    For detailed information about AT+CREG, see CREG – request network registration status. For details about AT+CGREG and AT+CEREG, refer to the Quectel AT Commands manual for your module.
10. Set the mobile network operator (MNO) selection to automatic:

    ```
    AT+COPS=0
    ```

    The response includes the current MNO and access technology.
11. Check the MNO selection:

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
12. Check the active RAT and signal strength:

    ```
    AT+QCSQ
    ```
13. Check the network registration state for each network type:

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
14. Open a data context:

    ```
    AT+CGATT=1
    ```

    If the response is OK, the device can send and receive data. If ERROR or +CME ERROR is returned, the attempt to open a data context has failed. Refer to the Quectel AT Commands manual for more information.
15. Check the allocated IP address. When you register to the correct APN, this matches the IP address in the Infinity Classic RADIUS log:

    ```
    AT+CGPADDR
    ```
16. Use the AnyNet Ping service to verify you can send and receive data packets:

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
* About the AnyNet Ping service
* [reducing-network-selection-time-on-quectel-bgxx-modules.md](quectel/reducing-network-selection-time-on-quectel-bgxx-modules.md "mention")
* About Access Point Names (APNs)
* AnyNet security options
