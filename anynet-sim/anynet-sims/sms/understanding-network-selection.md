# Understanding network selection

iuNetwork selection is how an IoT device chooses which available cellular network to connect to. Network availability depends on which SIM, modem, and Mobile Network Operators (MNO) the IoT device uses.

The AnyNet solution offers access to a wide choice of cellular networks for optimum connectivity, and enables your IoT devices to connect to the most appropriate available network.

This network selection process is performed using 3GPP standards (see [3GPP specifications for network selection methods](understanding-network-selection.md#id-3gpp)), and is configured within the device as either manual or automatic:

* Automatic mode – the modem uses a 3GPP procedure to select the highest priority available network, based on the network preference lists (PLMN lists) contained in the SIM. For more information, see [Understanding network selection](understanding-network-selection.md#automatic).
* Manual mode – the customer application chooses an available network for the device, and instructs the device modem to connect to that network. For more information, see [Understanding network selection](understanding-network-selection.md#manual).

{% hint style="warning" %}
We strongly advise you to use Automatic selection mode for network selection. If you choose Manual selection mode, your application is responsible for all network selection and must comply with GSMA network operation standards.
{% endhint %}

The following factors also influence which network is selected:

* Device and modem firmware and specifications
* SIM configuration
* Home and roaming network configuration
* Physical location – networks are available in some areas, but not in others, and their signal strength will vary depending on the available cellular masts in that region
* Device antenna – performance will vary by antenna quality

### How automatic network selection works <a href="#automatic" id="automatic"></a>

At switch on, or following recovery from lack of signal, the device attempts to connect to the last network that it was registered on.

If this fails, the modem initially performs a network scan to identify currently available networks in the given location. The modem compares what is available with the following preference lists contained in the SIM, in descending order:

| Order      | Network selection list name     | SIM filename           | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| ---------- | ------------------------------- | ---------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1          | Equivalent home network list    | EHPLMN                 | <p>Equivalent Home Public Land Mobile Network (HPLMN).</p><blockquote><p>If this does not exist, the HPLMN is scanned first.</p></blockquote><p>This list is defined by the MNO.</p><p>It contains a list of multiple PLMNs that the modem can use as alternative Home PLMNs. Networks are listed in decreasing priority order, with the first PLMN having the highest priority.</p>                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| 2          | Home network                    | HPLMN                  | A single Public Land Mobile Network (PLMN) containing the subscriber profile, which is derived from the SIM IMSI. The network is local to the country where the device is deployed.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| 3          | User-controlled preference list | EF<sub>PLMNwAcT</sub>  | <p>User-controlled PLMN selector with Access Technology.</p><p>This list is created and defined by the user and is only used if it exists in the SIM.</p><p>Updated using AT commands on the device. Networks listed in decreasing priority order, with the first PLMN having the highest priority.</p>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| 4          | Operator preference list        | EF<sub>OPLMNwAcT</sub> | <p>Operator-controlled PLMN selector with Access Technology.</p><p>This list is defined by the MNO.</p><p>Usually updated over-the-air (OTA). Networks listed in decreasing priority order, with the first PLMN having the highest priority.</p>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| Throughout | Forbidden network list          | EF<sub>FPLMN</sub>     | <p>Each available network is filtered against the forbidden network list. The modem will not register on networks that exist on this list.</p><p>This list is dynamically maintained by the device.</p><p>In automatic selection mode, when an attempt to connect is denied, then the network is usually added to the forbidden network list in order to prevent the device from connecting to that network again. Depending on the registration error, this addition is either permanent, or until the SIM is next power cycled. However, a network is not added to the forbidden network list if it exists on the home and equivalent home network lists.</p><blockquote><p>In manual selection mode, the modem disregards the forbidden list. For more information, see How manual network selection works.</p></blockquote> |

If the device modem cannot connect to a network that exists in the preference lists, then it will try to connect to the following:

* Networks with a high quality signal in random order, as follows:
* Remaining networks, in decreasing signal strength order

| Mobile Network Generation | Signal quality                                                                                                                                |
| ------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------- |
| 2G                        | Signal strength ([RSSI](https://app.gitbook.com/s/hPiB0Z0YdVhl1D9teuS7/#rssi)) greater than –85 dBm                                           |
| 3G                        | <p>FDD: Received Signal Code Power (RSCP) value greater than or equal to -95 dBm.</p><p>TDD: RSCP value greater than or equal to -84 dBm.</p> |
| 4G/LTE (including NB-IoT) | RSRP value greater than or equal to -110 dBm.                                                                                                 |
| 5G                        | RSRP value greater than or equal to -110 dBm.                                                                                                 |

#### About automatic network reselection

The modem will periodically search for higher priority networks, depending on the HPLMN Timer settings in the SIM, the Radio Access Technology (RAT) used and the mobile network generation.

The modem becomes unavailable when it scans for available networks and compares them to the preference lists.

> This means that the modem may drop registration during the scanning process, so the data session may also drop. This is more likely to occur on modems with single antennas.

#### About steered automatic network selection

Eseye actively manages the network connection using the Connectivity Management Platform (CMP) to ensure optimum connectivity, regardless of what happens to the network. Our AnyNet SIMs contain preconfigured preference lists, which allow the modem to fully implement GSMA standards.

Because Eseye is fully involved in designing and commissioning the SIMs, we have access to the security keys, algorithms and network interfaces required for updating the preference lists. We can manage the preference lists remotely OTA, after the SIM is fitted to your devices and deployed.

Eseye can use information that is not available to the modem to steer the connection around potential issues, such as networks that do not provide GPRS (if the device requires it), or to avoid connectivity issues on the mobile networks. For more information, see [About cloud network reporting](understanding-network-selection.md#about).

{% hint style="info" %}
We recommend steered automatic network selection for devices where the customer wants a "fit and forget" SIM to provide reliable connectivity.
{% endhint %}

#### About unmanaged automatic network selection

{% hint style="warning" %}
While Eseye can provide unmanaged automatic network selection, we do not recommend it.
{% endhint %}

Unmanaged automatic network selection is where the SIM has no preference lists. It is sometimes (inaccurately) referred to as best signal or strongest signal network selection. It is normally used in SIMs where the provider has limited ability to manage the connectivity.

The device modem will try to connect to the following:

* Networks with a high quality signal in random order, as follows:
* Remaining networks, in decreasing signal strength order

| Mobile Network Generation | Signal quality                                                                                                                                |
| ------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------- |
| 2G                        | Signal strength ([RSSI](https://app.gitbook.com/s/hPiB0Z0YdVhl1D9teuS7/#rssi)) greater than –85 dBm                                           |
| 3G                        | <p>FDD: Received Signal Code Power (RSCP) value greater than or equal to -95 dBm.</p><p>TDD: RSCP value greater than or equal to -84 dBm.</p> |
| 4G/LTE (including NB-IoT) | RSRP value greater than or equal to -110 dBm.                                                                                                 |
| 5G                        | RSRP value greater than or equal to -110 dBm.                                                                                                 |

Because the network selection is random, unmanaged automatic network selection works well in countries where all networks have good coverage and provide all services, as the devices are typically spread evenly across all networks.

However, each time the device loses connection to the network, if it cannot rejoin that network, it must rescan for a new network. Problems are typically seen where a network has variable quality service, since the device may pick this network regularly.

More seriously, in countries where networks offer differentiated levels of service, the device may connect to a network that cannot support the desired features of the application, and could potentially get stuck.

This configuration option suits some customers.

### How manual network selection works <a href="#manual" id="manual"></a>

While Eseye supports manual network selection for all AnyNet SIMs, we do not recommend using it unless you need to clear a network from the Forbidden network list.

Manual network selection enables the embedded customer application to attempt to register the device on the manually chosen network, overriding any network steering in the modem, SIM, or on the network.

The customer application issues network scan and selection commands to the modem (for example, AT+COPS). The network scan command returns a list of the available networks in the following order:

* Networks that exist in the SIM preference lists (detailed [above](understanding-network-selection.md#automatic)) as follows:
  * Equivalent home network list
  * Home network
  * User-controlled preference list
  * Operator preference list

{% hint style="warning" %}
Forbidden list – Unlike the automatic network selection process, during manual network selection, the modem disregards this list. As a result, the customer application can instruct the modem to attempt to register on a network that exists in this list. If the attempt to register succeeds, then that network is removed from the forbidden list.
{% endhint %}

\* Networks with a high quality signal in random order, as follows: \* Remaining networks, in decreasing signal strength order

| Mobile Network Generation | Signal quality                                                                                                                                |
| ------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------- |
| 2G                        | Signal strength ([RSSI](https://app.gitbook.com/s/hPiB0Z0YdVhl1D9teuS7/#rssi)) greater than –85 dBm                                           |
| 3G                        | <p>FDD: Received Signal Code Power (RSCP) value greater than or equal to -95 dBm.</p><p>TDD: RSCP value greater than or equal to -84 dBm.</p> |
| 4G/LTE (including NB-IoT) | RSRP value greater than or equal to -110 dBm.                                                                                                 |
| 5G                        | RSRP value greater than or equal to -110 dBm.                                                                                                 |

The customer application may use the AT+COPS= command to select the required network.

Consult your modem manufacturer manual to understand how AT+COPS= is implemented for your modem.

The application should anticipate that the chosen network may lose service or fail to provide service at any time. In such cases, the customer application should attempt to reconnect to the chosen network, or connect to an alternative network.

{% hint style="warning" %}
While manually selecting a network gives the device full control over network steering, the firmware may select an unsuitable network, which you cannot then resolve remotely.
{% endhint %}

### About cloud network reporting <a href="#about" id="about"></a>

Eseye receives live status feeds from our AnyNet Federation partner MNOs. We also have a large number of managed devices that continuously report real-time network information to our CMP. We use this crowd source model to understand the real performance of networks all over the world, and to manage device connectivity accordingly.

### 3GPP specifications for network selection methods <a href="#id-3gpp" id="id-3gpp"></a>

3GPP have rigorously defined network selection methods. These vary depending on the RAT type and network technology, such as 2G vs 4G.

For more information, see:

<table><thead><tr><th>Specification</th><th>Network selection method information</th></tr></thead><tbody><tr><td colspan="2">Select the most recently published document in the returned list.</td></tr><tr><td><a href="https://www.etsi.org/standards#page=1&#x26;search=TS%20123%20122&#x26;title=1&#x26;etsiNumber=1&#x26;content=0&#x26;version=0&#x26;onApproval=1&#x26;published=1&#x26;historical=0&#x26;startDate=2022-01-01&#x26;endDate=&#x26;harmonized=0&#x26;keyword=&#x26;TB=&#x26;stdType=&#x26;frequency=&#x26;mandate=&#x26;collection=&#x26;sort=3">ETSI TS 123 122</a></td><td>Non-Access-Stratum (NAS) functions related to Mobile Station in idle mode, including information about automatic and manual network selection.</td></tr><tr><td><a href="https://www.etsi.org/standards#page=1&#x26;search=TS%20125%20304&#x26;title=1&#x26;etsiNumber=1&#x26;content=0&#x26;version=0&#x26;onApproval=1&#x26;published=1&#x26;historical=0&#x26;startDate=2022-01-01&#x26;endDate=&#x26;harmonized=0&#x26;keyword=&#x26;TB=&#x26;stdType=&#x26;frequency=&#x26;mandate=&#x26;collection=&#x26;sort=3">ETSI TS 125 304</a></td><td>User Equipment (UE) procedures in idle mode and procedures for cell reselection in connected mode, including information about automatic and manual network selection.</td></tr><tr><td><a href="https://www.etsi.org/standards#page=1&#x26;search=TS%20131%20102&#x26;title=1&#x26;etsiNumber=1&#x26;content=0&#x26;version=0&#x26;onApproval=1&#x26;published=1&#x26;historical=0&#x26;startDate=2022-01-01&#x26;endDate=&#x26;harmonized=0&#x26;keyword=&#x26;TB=&#x26;stdType=&#x26;frequency=&#x26;mandate=&#x26;collection=&#x26;sort=3">ETSI TS 131 102</a></td><td>Characteristics of the Universal Subscriber Identity Module (USIM) application, including information about PLMN lists.</td></tr><tr><td><a href="https://www.etsi.org/standards#page=1&#x26;search=127%20007&#x26;title=1&#x26;etsiNumber=1&#x26;content=0&#x26;version=0&#x26;onApproval=1&#x26;published=1&#x26;historical=0&#x26;startDate=2022-01-01&#x26;endDate=&#x26;harmonized=0&#x26;keyword=&#x26;TB=&#x26;stdType=&#x26;frequency=&#x26;mandate=&#x26;collection=&#x26;sort=3">ETSI TS 127 007</a></td><td>AT command set, including information about AT+COPS.</td></tr></tbody></table>
