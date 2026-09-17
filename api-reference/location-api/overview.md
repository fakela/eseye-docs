---
description: Track devices with the Location API.
tags:
  - tag: paid-add-on
    primary: true
---

# Overview

The Eseye Location API provides location information for IoT SIMs and cellular network towers. You can:

* Retrieve the current or last recorded location of a SIM.
* Export the locations of multiple SIMs as a KMZ file.
* Retrieve the location and network details of a cell tower.

Location results are based on the last cell tower used by the SIM. They do not represent the precise GPS location of the device.

### Base URL

Send production requests to:

```
https://location.eseye.com
```

All requests must use HTTPS.

### Access and authentication

The Location API is a chargeable service and requires separate access.

Request access and pricing by emailing [orders@eseye.com](mailto:orders@eseye.com?subject=Request%20Location%20API%20pricing). Include your company name, role, phone number, and email address.

Eseye provides a Location API username and password. Each request includes:

* The username and password in the JSON request body.
* A `PHPSESSID` session cookie in the `Cookie` header.

```http
Cookie: PHPSESSID=<session-cookie>
Content-Type: application/json
```

{% hint style="warning" %}
Keep your Location API credentials and session cookie secure. Do not commit them to source control, expose them in client-side applications, or include them in logs.
{% endhint %}

### Location behaviour and limitations

* A SIM can be identified using either its ICCID or MSISDN.
* Location results contain the latitude and longitude of the last cell tower used by the SIM.
* When the device is offline or its current location is unavailable, the API returns the last recorded location.
* Eseye retains location data for two months. Store any historical data that you need to keep for longer.
* A KMZ export can contain a maximum of 10 ICCIDs per request.
* KMZ files can be imported into Google Earth or Google My Maps.
* A cell tower lookup requires its Mobile Country Code (`mcc`), Mobile Network Code (`mnc`), location area identifier, and cell identifier.
* A successful HTTP response does not always mean the location lookup succeeded. Check `status.status` in the response:
  * `OK` means the request completed successfully.
  * `ERR` means the request failed. Check `errorCode` and `errorMessage` for details.
* Location information depends on the network data available to Eseye. A location may not be returned for every lookup.

### Support

Contact [Eseye Support](mailto:support@eseye.com?subject=Location%20API%20support%20request) for Location API assistance.
