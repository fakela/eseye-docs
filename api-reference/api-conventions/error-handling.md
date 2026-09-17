---
description: Interpret HTTP responses and resolve API errors.
---

# Error handling

Eseye APIs use HTTP status codes to report request outcomes.

### HTTP status codes

| Status             | Meaning                                    | What to do                             |
| ------------------ | ------------------------------------------ | -------------------------------------- |
| `200 OK`           | The request succeeded.                     | Process the response.                  |
| `400 Bad Request`  | The request is malformed.                  | Check parameters and request data.     |
| `401 Unauthorized` | The token is missing, invalid, or expired. | Check the header or request a token.   |
| `403 Forbidden`    | The service account lacks permission.      | Request the required access.           |
| `404 Not Found`    | A resource does not exist.                 | Check the supplied identifiers.        |
| `5xx`              | Eseye could not complete a valid request.  | Retry temporary failures with backoff. |

### Error responses

An error can include `errorCode`, `errorTag`, `message`, and `additionalDetails`.

### Handle errors safely

* Record the HTTP status and error details in application logs.
* Do not log client secrets or complete access tokens.
* Correct most `4xx` errors before retrying.
* Retry temporary network and `5xx` failures with exponential backoff.
