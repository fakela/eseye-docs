---
description: Return an OAuth 2.0 bearer token for an API service account.
layout:
  width: wide
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
  metadata:
    visible: true
  tags:
    visible: true
  actions:
    visible: true
  anchors:
    visible: true
---

# Request access token

Tokens are issued using the client credentials grant, which authenticates your service account rather than an individual user.

{% openapi-operation spec="authentication" path="/oauth2/token" method="post" %}
[OpenAPI authentication](https://4401d86825a13bf607936cc3a9f3897a.r2.cloudflarestorage.com/gitbook-x-prod-openapi/raw/bdab568f466663f90a560a0773f26da545dac664b491667c7d934fd6f95a2798.yaml?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=dce48141f43c0191a2ad043a6888781c%2F20260917%2Fauto%2Fs3%2Faws4_request&X-Amz-Date=20260917T001054Z&X-Amz-Expires=172800&X-Amz-Signature=34e798c4decaa4af0cb4d536b81c449112b4dcdadc799ce1067a4feb93b4cf7c&X-Amz-SignedHeaders=host&x-amz-checksum-mode=ENABLED&x-id=GetObject)
{% endopenapi-operation %}



Returns an OAuth 2.0 bearer token for an API service account.

```http
POST /oauth2/token
```

### Endpoint

```
https://eseye-idp-prod.auth.<region>.amazoncognito.com/oauth2/token
```

Replace `<region>` with the AWS region Eseye provided.

### Request headers

| Header          | Value                               | Required |
| --------------- | ----------------------------------- | -------- |
| `Authorization` | `Basic <credentials>`               | Yes      |
| `Content-Type`  | `application/x-www-form-urlencoded` | Yes      |

`<credentials>` is the Base64-encoded form of `<client-id>:<client-secret>`.

### Form parameters

| Parameter    | Value                | Required | Description                        |
| ------------ | -------------------- | -------- | ---------------------------------- |
| `grant_type` | `client_credentials` | Yes      | Authenticates the service account. |
| `scope`      | `api/api`            | Yes      | Requests Eseye API access.         |

### Example request

```bash
curl --request POST \
  --url "https://eseye-idp-prod.auth.eu-west-1.amazoncognito.com/oauth2/token" \
  --user "${ESEYE_CLIENT_ID}:${ESEYE_CLIENT_SECRET}" \
  --header "Content-Type: application/x-www-form-urlencoded" \
  --data-urlencode "grant_type=client_credentials" \
  --data-urlencode "scope=api/api"
```

### Successful response

An accepted request returns HTTP `200`:

```json
{
  "access_token": "eyJraWQiOiJhYmMxMjMiLCJhbGciOiJSUzI1NiJ9...",
  "token_type": "Bearer",
  "expires_in": 3600
}
```

Reuse the token until it expires, then request another token.

### Error response

The endpoint returns HTTP `400` when it rejects a request. An `invalid_client` error means the credentials were not accepted.
