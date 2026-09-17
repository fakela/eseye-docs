---
description: Headers used when sending Eseye API requests.
---

# Request headers

Use these headers when sending requests to Eseye APIs.

### Base URLs

Each API reference provides the production base URL for that API. Always send requests over HTTPS.

For example, the SIM API uses:

```
https://sim.api.anynetiot.com
```

The authentication service uses a separate regional URL. See [authentication](../authentication/ "mention") for details.

### Authorization

Every protected request requires a bearer token:

```http
Authorization: Bearer <access-token>
```

### Accept

Request a JSON response with:

```http
Accept: application/json
```

### Content-Type

Send JSON request bodies with:

```http
Content-Type: application/json
```

The token endpoint requires:

```http
Content-Type: application/x-www-form-urlencoded
```

{% hint style="warning" %}
Send client credentials only to the token endpoint. Do not send them to API endpoints.
{% endhint %}

