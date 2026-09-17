# How to connect a Nordic nRF9160 modem to a cellular network using an Eseye SIM

You can connect to a cellular network using a Nordic nRF9160 modem and Eseye eUICC or AnyNet SIM. The following steps will help you through three stages of the network connection process:

1. Configuring automatic network operator selection.
2. Checking the network registration status.
3. Ensuring you can send and receive data.

#### Before you begin

* Configure the Nordic nRF9160 modem according to the manufacturer instructions. For example, ensure you have installed the correct drivers and requisite firmware.
* Fully insert the Eseye SIM into your device.
* Ensure the Eseye SIM is activated on the Infinity Classic portal.
* Ensure the device is on and the Nordic nRF9160 modem is powered up.
* Configure a terminal emulator to send commands to the Nordic nRF9160 modem.

To connect a Nordic nRF9160 modem to a cellular network:

1.  Using the terminal emulator, configure the module for full functionality. Type:

    AT+CFUN=1\<CR>

    \<CR> is the end-of-line character marking the end of a command line (alias \r – carriage return).
2.  Verify the device is reading the SIM correctly by requesting the ICCID and IMSI. Type:

    AT+CRSM=176,12258,0,0,10\<CR>

    The response is similar to the following:

    +CRSM: 144,0,"\<ICCID>"

    where ICCID is in binary coded decimal format, with switched digits. So the returned response 2143658709 actually means 1234567890.

    To clarify:

    21 43 65 87 09

    Switch places:

    12 34 56 78 90

    Type:

    AT+CIMI\<CR>

    Make a note of the returned numbers in the event you need to ask for assistance later.
3.  Configure the Nordic nRF9160 modem for minimum functionality. To ensure the radio is off, type:

    AT+CFUN=0\<CR>
4.  Configure the supported system modes for both LTE-M (Cat M1) and NB-IoT, with a preference of LTE-M. Type:

    AT%XSYSTEMMODE=1,1,0,1\<CR>

    The Nordic nRF9160 modem does not support other RAT types.

    System modes are region and network specific, and may not exist where your device is connected. For example, in India you can only access NB-IoT.
5.  Configure the device to search all available frequency bands. Type:

    AT%XBANDLOCK=0\<CR>

    The advanced user may want to limit the number of bands searched, which is beyond the scope of this topic.
6.  Set the mobile network operator selection to automatic. Type:

    AT+COPS=0\<CR>
7.  Define the PDP context to route data through Eseye's APN. Type:

    AT+CGDCONT=\<cid>,"\<PDPtype>","\<APN>"\<CR>

    where \<cid> is the context ID, \<PDPtype> is the IP connection type, and \<APN> is the relevant Eseye Access Point Name.

    For example: AT+CGDCONT=0,"IP","eseye1"

    For information about which Eseye APN to use, speak to your Account Manager. Also see [Current AnyNet APN list](https://docs.eseye.com/Content/Connectivity/AnyNetAPNList.htm).
8.  Configure the module for full functionality. Type:

    AT+CFUN=1\<CR>
9.  Set the mode to enable +CEREG unsolicited result codes. Type:

    AT+CEREG=1\<CR>

    For more information, see the Nordic nRF9160 modem AT Commands documentation.
10. Check the network operator selection. Type:

    AT+COPS?\<CR>

    The response includes the operator and the access technology selected. The following example response is for Verizon in LTE Cat M1 mode:

    +cops: 0,0,"Verizon ",8

    The following example response is for T-Mobile in NB-IoT mode:

    +cops: 0,0,"T-Mobile USA",9
11. Determine the signal strength. Type:

    AT+CSQ\<CR>
12. Check the network registration state. Type:

    AT+CEREG?\<CR>

    The response includes the mode you set earlier and the registration status, which is either:

    * 0 – Not registered, the device is currently not searching for new operator.
    * 1 – Registered to home network.
    * 2 – Not registered, but the device is currently searching for a new operator.
    * 3 – Registration denied.
    * 4 – Unknown. For example, out of range.
    * 5 – Registered, roaming. The device is registered on a foreign (national or international) network.

    Example response:

    +CEREG: 1,5

    Factors contributing to SIM failure to register on the network may include:

    * Missing network coverage
    * Denied network access
    * No valid roaming agreement between the home network and currently available operators
13. Open a data context. Type:

    AT+CGATT=1\<CR>

    If the response is OK, the device can send and receive data. If ERROR or +CME ERROR is returned, the attempt to open a data context has failed. Refer to the Nordic nRF9160 modem AT Commands manual for more information.
14. Check the allocated IP address. If you registered to the correct APN, this matches the IP address on the RADIUS log in Infinity Classic. Type:

    AT+CGPADDR\<CR>
15. Log into Infinity Classic and check the SIM status is Active on the SIM list page to ensure the SIM is connected.
16. If you have integrated the Nordic nRF9160 modem into the IP stack of another device, such as a Raspberry Pi, you can check the connectivity by ensuring you can send and receive data packets via the modem. We recommend pinging the AnyNet Ping service:

    ping 192.168.109.2\<CR>

    A successful response is similar to the following:

    OK

    +PING: 0,"192.168.109.2",32,744,255

    +PING: 0,"192.168.109.2",32,257,255

    +PING: 0,"192.168.109.2",32,234,255

    +PING: 0,"192.168.109.2",32,238,255

    +PING: 0,4,4,0,234,744,368

    If the Nordic nRF9160 modem is not integrated into the IP stack of another device, you cannot use the ping function. For more information, see [Ping TCP/IP server with AT Command (external link)](https://devzone.nordicsemi.com/f/nordic-q-a/50537/ping-tcp-ip-server-with-at-command).
