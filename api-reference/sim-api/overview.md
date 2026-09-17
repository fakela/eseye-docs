# Overview

The Eseye SIM API lets you manage the SIMs in your global IoT estate. You can:

* Activate or deactivate SIMs.
* Retrieve details for one or multiple SIMs.
* Update SIM statuses, packages, and portfolios.
* Create, update, and delete SIM attributes.
* View billing and network snapshots.

Each SIM has a unique 19- or 20-digit Integrated Circuit Card Identifier (`iccId`). Endpoints that act on a specific SIM include the `iccId` in the request path. The list endpoint can also accept one or more `iccId` values as query parameters.

### Base URL

Send production requests to:

```
https://sim.api.anynetiot.com
```

SIM API endpoints use `/api/v2`.

### Access and authentication

The SIM API is free to use. You need an Infinity account and a SIM API service account.

Eseye provisions the service account and provides its client ID, client secret, region, and permissions. Request access by emailing [orders@eseye.com](mailto:orders@eseye.com?subject=Request%20SIM%20API). Include your company name, role, phone number, and email address.

Every request requires an OAuth 2.0 bearer token:

```http
Authorization: Bearer <access-token>
```

Tokens expire after one hour. Follow [Broken link](/broken/spaces/0xQKujz8nVihyxgGvU7r/pages/bdk8wlJHszU6TNBJHJIf "mention") to request a token and make your first API call.

{% hint style="warning" %}
Test with test SIMs. API changes can affect live connectivity and billing.
{% endhint %}

### SIM behaviour and limitations

* A SIM has an `available` or `active` status.
* An `available` SIM cannot connect to a network and has no service charges.
* An `active` SIM can connect to a network. Standard service and usage charges apply.
* Set `status` to `available` to deactivate a SIM.
* Suspending a SIM disables its services but does not stop service charges.
* You cannot make changes to a suspended SIM.
* SIMs cannot be created through the API. Eseye supplies the SIMs and links them to your account.
* SIM API endpoints update one SIM at a time. For supported changes across multiple SIMs, see the [Bulk Operations API](https://app.gitbook.com/s/0xQKujz8nVihyxgGvU7r/bulk-operations-api "mention").
* Free-text search is not supported. Add attributes to categorise and find SIMs.

### Support

Contact [Eseye Support](mailto:support@eseye.com?subject=API%20support%20request) for API assistance.
