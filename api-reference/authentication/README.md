---
description: Authenticate an API service account with OAuth 2.0 client credentials.
---

# Authentication

Eseye APIs use the OAuth 2.0 client credentials grant. This flow authenticates an API service account rather than an individual Infinity user.

It is designed for server-to-server integrations that can store credentials securely.

### How authentication works

1. Your application sends its client ID and client secret to the [request-access-token.md](request-access-token.md "mention").
2. Eseye verifies the service account and returns an access token.
3. Your application sends the access token with each API request.
4. When the token expires, your application requests a new one.

### Service accounts

An API service account identifies an integration and controls what that integration can do.

Eseye provisions the service account and provides:

* A client ID
* A client secret
* The AWS region used for authentication
* Access to the agreed APIs and operations

The client ID identifies the service account. The client secret proves that your application is authorised to use it.

{% hint style="info" %}
The token request always uses the `api/api` scope. Changing this value does not grant additional access. The permissions assigned to the service account determine which API operations the token can authorise.
{% endhint %}

### Access tokens

A successful authentication request returns an OAuth 2.0 bearer token. Include it in the [request-headers.md](../api-conventions/request-headers.md "mention") of every protected API request:

```
Authorization: Bearer <access-token>
```

Access tokens expire after one hour. The client credentials flow does not require a user to sign in again. Request another token using the same service account credentials when the current token expires.

Your application should reuse a valid token instead of requesting a new token before every API call.

### Token endpoint

Request tokens from the production endpoint for your AWS region:

```
https://eseye-idp-prod.auth.<region>.amazoncognito.com/oauth2/token
```

For example:

```
https://eseye-idp-prod.auth.eu-west-1.amazoncognito.com/oauth2/token
```

See [request-access-token.md](request-access-token.md "mention") for the complete request.

### Request an access token

The token service uses a regional endpoint. For example:

```
https://eseye-idp-prod.auth.eu-west-1.amazoncognito.com/oauth2/token
```

The [request-access-token.md](request-access-token.md "mention") includes the headers, form parameters, response, and request example.

### Protect your credentials and tokens

* Store the client secret in an environment variable or secrets manager.
* Request tokens only from a trusted server-side application.
* Do not expose credentials in browser or mobile application code.
* Do not commit credentials or tokens to source control.
* Do not write credentials or complete access tokens to application logs.
* Always send credentials and tokens over HTTPS.

{% hint style="warning" %}
Base64 encoding does not encrypt the client ID and client secret. HTTPS protects the credentials while they are being transmitted.
{% endhint %}

### Permissions

An access token can only authorise operations allowed by its service account.

{% hint style="warning" %}
If an API returns [error-handling.md](../api-conventions/error-handling.md "mention"), the token may be valid but the service account does not have permission to perform that operation. Contact Eseye to request the required access.
{% endhint %}
