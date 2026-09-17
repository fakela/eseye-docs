# How to connect a Fibocom GS510-Q50 module to a cellular network using an Eseye SIM

You can connect to a cellular network using a Fibocom GS510-Q50 module and Eseye eUICC or AnyNet SIM. The following steps will help you through three stages of the network connection process:

1. Configuring automatic network operator selection.
2. Checking the network registration status.
3. Ensuring you can send and receive data.

#### Before you begin

* Configure the device and Fibocom GS510-Q50 module according to the manufacturer instructions. For example, ensure you have installed the correct drivers.
* Fully insert the Eseye SIM into your device.
* Ensure the Eseye SIM is activated on the Infinity Classic portal.
* Ensure the device is on and the Fibocom GS510-Q50 module is powered up.
* Configure a terminal emulator to send commands to the Fibocom GS510-Q50 module.

To connect a Fibocom GS510-Q50 module to a cellular network:

1.  Using the terminal emulator, verify the device is reading the SIM correctly by requesting the ICCID and IMSI. Type:

    AT+CCID\<CR>

    AT+CIMI\<CR>

    \<CR> is the end-of-line character marking the end of a command line (alias \r – carriage return).

    Make a note of the returned numbers in the event you need to ask for assistance later.
2.  Define the PDP context to route data through Eseye's APN. Type:

    AT+CGDCONT=\<cid>,"\<PDPtype>","\<APN>"\<CR>

    where \<cid> is the context ID, \<PDPtype> is the IP connection type, and \<APN> is the relevant Eseye Access Point Name.

    For example: AT+CGDCONT=1,"IP","eseye1"

    For information about which Eseye APN to use, speak to your Account Manager. Also see [Current AnyNet APN list](https://docs.eseye.com/Content/Connectivity/AnyNetAPNList.htm).
3.  Set the mode to enable +CREG and +CGREG unsolicited result codes. Type:

    AT+CREG=1\<CR>

    AT+CGREG=1\<CR>
4.  Check the MNO selection. Type:

    AT+COPS?\<CR>

    The response includes the operator and the access technology selected.

    The following example response is for T-Mobile in GSM mode:

    +cops: 0,0,"T-Mobile USA"
5.  Check the network registration state per network type. Type:

    AT+CREG?\<CR>

    AT+CGREG?\<CR>

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

    Factors contributing to SIM failure to register on the network may include:

    * Missing network coverage
    * Denied network access
    * No valid roaming agreement between the home network and currently available operators
6.  Open a data context. Type:

    AT+CGACT=1,1\<CR>

    If the response is OK, the device can send and receive data. If ERROR or +CME ERROR is returned, the attempt to open a data context has failed. Refer to the Fibocom GS510-Q50 module AT Commands manual for more information.
7.  Check the allocated IP address. If you registered to the correct APN, this matches the IP address on the RADIUS log in Infinity Classic. Type:

    AT+CGPADDR\<CR>
8. If your device is configured for the ICMP protocol (ping), use the AnyNet Ping service (192.168.109.2) to ensure you can send and receive data packets.

<br>
