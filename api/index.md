---
layout: page
title: API
---

# API

This API is organized around [REST][REST]. Our API is designed to have predictable, resource-oriented URLs and to use HTTP response codes to indicate API errors. [JSON][JSON] will be returned in all responses from the API, including errors.

## Authentication

We only allow live server IPs to communicate with the API, furthermore authentication will not be implemented currently.

All API requests must be made over HTTPS. Calls made over plain HTTP will fail.


## Errors

```nginx
Status: 422 Unprocessable Entity
```

```json
{
  "errors": [
    {
      "field": "email",
      "message": "The email "xxx" is not a valid E-Mail."
    }
  ]
}
```

bringmeister uses conventional HTTP response codes to indicate success or failure of an API request. In general, codes in the 2xx range indicate success, codes in the 4xx range indicate an error that resulted from the provided information (e.g. a required parameter was missing, etc.), and codes in the 5xx range indicate an error with bringmeister's servers.

### HTTP Status Codes Summary

Code   | Description
---    |---
`200`  | OK - Everything worked as expected.
`201`  | Created - Item was created successfully. The URL to the item can be found in the "Location"-Header.
`204`  | No Content - The request was successful.
`401`  | Unauthorized - No valid API key provided.
`404`  | Not Found - The requested item doesn't exist.
`422`  |  Unprocessable Entity
`5xx`  | Server errors - something went wrong on bringmeister's end.

All error objects have _field_ properties so that your client can tell what the problem is. There is also an error _message_ to let you know what is wrong with the field.

## Endpoints

```sh
$ curl {{ site.bringmeister.api }}/
```

> Response

```nginx
Status: 200 OK
```
```json
{
  "matrix_url": "{{ site.bringmeister.api }}/matrix",
  "slot_url": "{{ site.bringmeister.api }}/slot",
}
```


  [REST]: http://en.wikipedia.org/wiki/Representational_State_Transfer
  [JSON]: http://www.json.org/
  [HTTP Basic Auth]: http://en.wikipedia.org/wiki/Basic_access_authentication
  [HTTPS]: http://en.wikipedia.org/wiki/HTTP_Secure
  [login]: /api/login/
  [createuser]: /api/user/#toc_1
