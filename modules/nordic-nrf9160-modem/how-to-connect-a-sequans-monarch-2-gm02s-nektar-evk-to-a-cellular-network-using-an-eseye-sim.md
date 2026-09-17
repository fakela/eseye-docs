# How to connect a Sequans Monarch 2 GM02S-NEKTAR EVK to a cellular network using an Eseye SIM

You can connect to a Cat-M1 or NB-IOT cellular network using a Sequans Monarch 2 GM02S-NEKTAR EVK (Evaluation Kit) and Eseye eUICC or AnyNet SIM. The following steps will help you through three stages of the network connection process:

1. Configuring automatic network operator selection.
2. Checking the network registration status.
3. Ensuring you can send and receive data.

### Before you begin

* Configure the device and Sequans Monarch 2 GM02S-NEKTAR EVK according to the manufacturer instructions. For example, ensure you have installed the correct drivers.
* Fully insert the Eseye SIM into your device.
* Ensure the Eseye SIM is activated on the Infinity Classic portal.
* Ensure the device is on and the Sequans Monarch 2 GM02S-NEKTAR EVK is powered up.
* Configure a terminal emulator to send commands to the Sequans Monarch 2 GM02S-NEKTAR EVK.

To connect a Sequans Monarch 2 GM02S-NEKTAR EVK to a cellular network:

1.  Using the terminal emulator, verify the device is reading the SIM correctly by requesting the ICCID and IMSI. Type:

    AT+SQNCCID

    AT+CIMI

    is the end-of-line character marking the end of a command line (alias \r – carriage return).

    Make a note of the returned numbers in the event you need to ask for assistance later.
2.  Using the terminal emulator, configure the Sequans Monarch 2 GM02S-NEKTAR EVK for minimum functionality. Type:

    AT+CFUN=0
3.  Check which LTE IoT technology is allowed according to the installed modem firmware version, and if it is active. Type:

    AT+SQNSIRSW?

    +SQNSIRSW: ("NBIOT","",),("CatM","",)

    where is the firmware version, and is either:

    * 0 – not active
    * 1 – active

    For example: +SQNSIRSW: ("NBIOT","LR8.1.0.0-55629",1),("CatM","LR8.0.5.10-55042",0)
4.  To switch technologies, type the following in order, waiting for each command response before proceeding:

    If any of these commands returns ERROR, reboot the device and retry the command. You may have to do this several times. If you continue after the command returns ERROR, you may brick the board (render it useless) and it will require re-flashing with the modem firmware.

    AT^RESET

    OK

    AT+SQNSFACTORYRESET

    OK

    AT+SQNSIRSW=""

    where is either NBIOT or CatM

    For example: AT+SQNSIRSW="NBIOT"

    OK
5.  Determine which 4G LTE band the modem is allowed to use for different Radio Access Technologies (RATs). Type:

    AT+SQNBANDSEL?

    This will return either:

    * AT+SQNBANDSEL=0 for LTE-M1
    * AT+SQNBANDSEL=1 for LTE Cat NB1
6.  Configure the device to search the allowed 4G LTE band. Type:

    AT+SQNBANDSEL=<4GLTEband>,"standard","1,2,3,4,5,8,12,13,17,18,19,20,25,26,28,66,71"

    where <4GLTEband> is either 0 or 1, depending on the current RAT.

    The advanced user may want to limit the number of bands searched, which is beyond the scope of this topic.
7.  Define the PDP context to route data through Eseye's APN. Type:

    AT+CGDCONT=,"",""

    where is the context ID, is the IP connection type, and is the relevant Eseye Access Point Name.

    For example: AT+CGDCONT=1,"IP","eseye1"

    For information about which Eseye APN to use, speak to your Account Manager. Also see Current AnyNet APN list.
8.  Configure the module for full functionality. Type:

    AT+CFUN=1
9.  Set the mode to enable +CEREG unsolicited result codes. Type:

    AT+CEREG=1

    For more information, refer to the Sequans Monarch 2 AT Commands manual for your module.
10. Set the mobile network operator (MNO) selection to automatic, which will force the modem to start searching for networks. Type:

    AT+COPS=0

    If the device has registered on a network, the response will include the current MNO and access technology.
11. Check the MNO selection. Type:

    AT+COPS?

    The response includes the operator and the access technology selected. The following example response is for a private network in NB-IoT mode:

    +COPS: (2,"picoLTE Network","picoLTE","00101",9)(3,"vodafone UK","voda UK","234)

    where 2 is the current private network, and 3 is forbidden.

    In Cat-M1 mode, the final number is an 8. For example:

    +COPS: (2,"picoLTE Network","picoLTE","00101",8)
12. Determine the signal strength. Type:

    AT+CSQ

    The Sequans Monarch 2 GM02S-NEKTAR EVK may return any of the following values:

    | Value | Description                                                             |
    | ----- | ----------------------------------------------------------------------- |
    | 0     | -113 dBm or less                                                        |
    | 1     | -111 dBm                                                                |
    | 2-30  | -109 to -53 dBm (when the value decreases by 1, the dBm increases by 2) |
    | 31    | -51 dBm or greater                                                      |
    | 99    | Not known or not detectable                                             |

    For example:

    +CSQ: 14,99

    where 14 relates to the RSSI \~ -85dBm

    and 99 is the bit error rate

    For information about the response, see the Monarch 2 LR 8.1 AT Command Reference Manual.
13. Check the network registration state per network type. Type:

    AT+CEREG?

    The response includes the mode you set earlier and the registration status, which is either:

    * 0 – Not registered, the device is currently not searching for new operator.
    * 1 – Registered to home network.
    * 2 – Not registered, but the device is currently searching for a new operator.
    * 3 – Registration denied.
    * 4 – Unknown. For example, out of range.
    * 5 – Registered, roaming. The device is registered on a foreign (national or international) network.

    For example:

    +CEREG: 1,5

    Factors contributing to SIM failure to register on the network may include:

    * Missing network coverage
    * Denied network access
    * No valid roaming agreement between the home network and currently available operators
14. Open a data context. Type:

    AT+CGATT=1

    If the response is OK, the device can send and receive data. If ERROR or +CME ERROR is returned, the attempt to open a data context has failed. For more information, see the Sequans Monarch 2 AT Commands manual for your module.
15. Check the allocated IP address. If you registered to the correct APN, this matches the IP address on the RADIUS log in Infinity Classic. Type:

    AT+CGPADDR
16. Use the AnyNet Ping service to ensure you can send and receive data packets. Type:

    AT+PING="192.168.109.2"

    A successful response is similar to the following:

    +PING: ,,,

    where Latency is in milliseconds, and TTL is TTL (Time To Live).

    For example:

    +PING: 1,192.168.109.2,1590,252

    +PING: 2,192.168.109.2,840,252

    +PING: 3,192.168.109.2,1410,252

    +PING: 4,192.168.109.2,7460,252

    OK

## Where to next?

* eUICC overview
* Find out about bootstrap and operational profiles: About eUICC SIM profiles
* About the AnyNet Ping service
* Reducing network selection time on Quectel BGxx modules
* About Access Point Names (APNs)
* AnyNet security options
