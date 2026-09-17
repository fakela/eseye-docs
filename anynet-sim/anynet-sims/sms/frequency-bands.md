# Frequency bands

The electromagnetic spectrum is divided into smaller radio frequency bands (also called operating bands) that governments allocate to MNOs or private network owners. The supported frequency bands depend on:

* Operators – restricted to bands they own or have licensed for use in a particular country
* IoT devices – designed to work on a subset of all of the available operating bands

{% hint style="info" %}
Eseye's solution can, in principle, work with any spectrum. However, to date, Eseye's solution has been focused on cellular connectivity.
{% endhint %}

### Identifying bands used by operators in specific countries <a href="#identify" id="identify"></a>

Frequency bands vary by country and region, and their allocation depends on the MNOs and other spectrum owners (such as CBRS for private networks). Eseye works closely with local MNOs to ensure the maximum number of connectivity options in each country.

The following table details the most common regions we support. Band usage can vary within countries owing to specific carrier deployments. Additionally, countries may introduce newer bands. Always check with your specific carrier or regulatory authority for the most up-to-date information about the region where you are deploying your IoT devices.

|           | 2G (GSM)                                        | 3G (UMTS/WCDMA)                                 | 4G (LTE)                                                                                                                                                        |
| --------- | ----------------------------------------------- | ----------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Australia | <p>Band 3 (1800 MHz)</p><p>Band 8 (900 MHz)</p> | Band 1 (2100 MHz)                               | <p>Band 3 (1800 MHz)</p><p>Band 5 (850 MHz)</p><p>Band 7 (2600 MHz)</p><p>Band 28 (700 MHz)</p>                                                                 |
| Asia      | <p>Band 3 (1800 MHz)</p><p>Band 8 (900 MHz)</p> | Band 1 (2100 MHz)                               | <p>Band 1 (2100 MHz)</p><p>Band 3 (1800 MHz)</p><p>Band 5 (850 MHz)</p><p>Band 8 (900 MHz)</p><p>Band 40 (2300 MHz)</p><p>Band 41 (2500/2600 MHz)</p>           |
| China     | <p>Band 3 (1800 MHz)</p><p>Band 8 (900 MHz)</p> | <p>Band 1 (2100 MHz)</p><p>Band 8 (900 MHz)</p> | <p>Band 38 (2600 MHz)</p><p>Band 39 (1900 MHz)</p><p>Band 40 (2300 MHz)</p><p>Band 41 (2500/2600 MHz)</p>                                                       |
| EU        | <p>Band 3 (1800 MHz)</p><p>Band 8 (900 MHz)</p> | Band 1 (2100 MHz)                               | <p>Band 1 (2100 MHz)</p><p>Band 3 (1800 MHz)</p><p>Band 7 (2600 MHz)</p><p>Band 8 (900 MHz)</p><p>Band 20 (800 MHz)</p>                                         |
| India     | <p>Band 3 (1800 MHz)</p><p>Band 8 (900 MHz)</p> | Band 1 (2100 MHz)                               | <p>Band 3 (1800 MHz)</p><p>Band 5 (850 MHz)</p><p>Band 40 (2300 MHz)</p><p>Band 41 (2500/2600 MHz)</p>                                                          |
| US        | <p>Band 2 (1900 MHz)</p><p>Band 5 (850 MHz)</p> | <p>Band 2 (1900 MHz)</p><p>Band 5 (850 MHz)</p> | <p>Band 2 (1900 MHz)</p><p>Band 4 (1700/2100 MHz)</p><p>Band 5 (850 MHz)</p><p>Band 12 (700 MHz)</p><p>Band 13 (700 MHz)</p><p>Band 14 (FirstNet – 700 MHz)</p> |

Alternatively, use the following resources to identify the frequency bands supported by an operator in a particular country:

*   GSMA records of members and the licensed bands available to each

    <div data-gb-custom-block data-tag="hint" data-style="info" class="hint hint-info"><p>This information is only available to GSMA members.</p></div>
*   [GSMA interactive map of NB-IoT and CAT-M deployments](https://www.gsma.com/iot/mobile-iot-map/) – a list of operators in each country and any band-specific restrictions for NB-IoT and CAT-M deployments.

    <div data-gb-custom-block data-tag="hint" data-style="info" class="hint hint-info"><p>The map does not contain the most up-to-date information.</p></div>
* Individual MNO reports – the most accurate source of information but time-consuming to obtain because you must retrieve them for every operator in every country. Also, because MNOs can use bands from the RAT they believe best serves their customers, the information may not list all the available bands and could display bands for older RAT types. For example, if an MNO reuses a 2G band for data even though a CAT-M1 band is available.
*   Cellular modem manufacturer specifications – modem manufacturers maintain accurate information around the used frequency bands to guarantee that modems sold for a particular region will work in those countries.

    <div data-gb-custom-block data-tag="hint" data-style="info" class="hint hint-info"><p>Modem manufacturers can be aware of networks operating on two bands but choose to support only one band to reduce the modem cost. We recommend that you ensure your modem supplier provides documentation to show that the modem has access to all the frequency bands in each country of operation.</p></div>
* Commercially harvested data – a number of commercial organisations collect and sell measurements of cell tower performance, including signal strength in multiple locations and the frequency bands detected.
* [Wikipedia (LTE bands available in each country)](https://en.wikipedia.org/wiki/List_of_LTE_networks) – compiled using crowd-sourced information from measurements taken from contributors’ handsets or from compiling lists of publicly available information.

### Identifying bands used by devices <a href="#identifyingbandsusedbydevices" id="identifyingbandsusedbydevices"></a>

The device and modem manufacturers develop IoT devices to work on specific bands. Eseye works with customers to prototype, test, certify and onboard devices, which ensures modems and the device antennae support the necessary operating bands.

Knowing which frequency bands are available also enables you to configure battery operated equipment to scan only a limited subset of the bands when attempting to connect, which helps speed up registration and reduce power consumption.

{% hint style="info" %}
Reducing the number of bands scanned can also limit the connectivity options. For example, reusing 2G frequencies in LTE/5G-NR means that devices that restrict the bands that they scan can limit future connectivity options.
{% endhint %}

Use the following resources to identify the frequency bands supported by an IoT device or modem:

* Cellular modem manufacturer specifications – modem manufacturers maintain accurate information around the frequency bands supported by their modem.
* [8823 Hera 600v5 series router datasheet (PDF)](https://docs.eseye.com/Content/Resources/Files/8823-Hera-600v5-Series-Router-Datasheet.pdf) and [8829 Hera 600v6 series router datasheet (PDF)](https://docs.eseye.com/Content/Resources/Files/8829-Hera-600v6-Series-Router-Datasheet.pdf) – the frequency bands supported on the Hera 600 series router are defined in the specification table.

#### CAT-M bands (M1/M2) <a href="#catmbands" id="catmbands"></a>

CAT-M is a subset of LTE and so, theoretically, CAT-M devices can support any LTE band. However, CAT-M devices are typically designed to operate in the frequency bands defined in section 5.5E in 3GPP TS 36.101 (v17.5.0), which include:

* FDD (half duplex and full-duplex) bands – 1, 2, 3, 4, 5, 7, 8, 11, 12, 13, 14, 18, 19, 20, 21, 24, 25, 26, 27, 28, 31, 66, 71, 72, 73, 74, 85, 87 and 88
* TDD bands – 39, 40, 41, 42 and 43

The full list of EUTRA bands are defined in Table 5.5-1 in [3GPP TS 36.101](https://www.3gpp.org/DynaReport/36101.htm).

#### NB-IoT bands (NB1/NB2) <a href="#nbiotbands" id="nbiotbands"></a>

NB-IoT devices support the operating bands defined in section 5.5F in 3GPP TS 36.101 (v17.5.0), which include:

* 4G/LTE bands – 1, 2, 3, 4, 5, 7, 8, 11, 12, 13, 14, 17, 18, 19, 20, 21, 24, 25, 26, 28, 31, 41, 42, 43, 65, 66, 70, 71, 72, 73, 74, 85, 87, 88, and 103
* 5G NR bands – n1, n2, n3, n5, n7, n8, n12, n14, n18, n20, n25, n28, n41, n65, n66, n70, n71, n74, n90

Category NB1 and NB2 systems operate in HD-FDD duplex mode or in TDD mode.
