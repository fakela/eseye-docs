---
description: Retrieve large collections in smaller responses.
---

# Pagination

List endpoints use pagination to divide large collections into smaller responses.

### Parameters

| Parameter   | Required | Description                                   |
| ----------- | -------- | --------------------------------------------- |
| `pageSize`  | No       | Maximum number of returned items.             |
| `pageToken` | No       | Identifies the requested page. Omit it first. |

The endpoint reference shows whether it supports these parameters.

### Request the next page

Copy `nextPageToken` from the response. Pass it as `pageToken` in the next request:

```http
GET /api/v2/sim?pageSize=50&pageToken=next-page-token
```

Continue until the response omits `nextPageToken`.

{% hint style="info" %}
Treat page tokens as opaque values. Do not edit or calculate them.
{% endhint %}
