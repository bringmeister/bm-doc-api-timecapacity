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

parku uses conventional HTTP response codes to indicate success or failure of an API request. In general, codes in the 2xx range indicate success, codes in the 4xx range indicate an error that resulted from the provided information (e.g. a required parameter was missing, etc.), and codes in the 5xx range indicate an error with parku's servers.

### HTTP Status Codes Summary

Code   | Description
---    |---
`200`  | OK - Everything worked as expected.
`201`  | Created - Item was created successfully. The URL to the item can be found in the "Location"-Header.
`204`  | No Content - The request was successful.
`401`  | Unauthorized - No valid API key provided.
`404`  | Not Found - The requested item doesn't exist.
`422`  |  Unprocessable Entity
`5xx`  | Server errors - something went wrong on parku's end.

All error objects have _field_ properties so that your client can tell what the problem is. There is also an error _message_ to let you know what is wrong with the field.

## Endpoints

```sh
$ curl {{ site.parku.api }}/ \
    -u 6f1ed002ab5595859014ebf0951522d9:parku
```

> Response

```nginx
Status: 200 OK
```
```json
{
  "urls_url": "{{ site.parku.api }}/",
  "version_url": "{{ site.parku.api }}/version",
  "locations_url": "{{ site.parku.api }}/locations",
  "terms_url": "{{ site.parku.api }}/terms",
  "faq_url": "{{ site.parku.api }}/faq",
  "privacy_policy_url": "{{ site.parku.api }}/privacy_policy",
  "login_url": "{{ site.parku.api }}/login",
  "user_url": "{{ site.parku.api }}/user",
  "password_url": "{{ site.parku.api }}/password",
  "credit_url": "{{ site.parku.api }}/credit",
  "phone_numbers_url": "{{ site.parku.api }}/phone_numbers",
  "cars_url": "{{ site.parku.api }}/cars",
  "bookings_url": "{{ site.parku.api }}/bookings",
  "violation_url": "{{ site.parku.api }}/bookings/{booking_id}/violation",
  "sesam_url": "{{ site.parku.api }}/sesam"
}
```

Keep in mind, that some of these urls are private. You need a _private key_ which you get when [logging in a user][login].
For the public urls you need a _public key_.

With a _private key_ you can access public urls.

  [REST]: http://en.wikipedia.org/wiki/Representational_State_Transfer
  [JSON]: http://www.json.org/
  [HTTP Basic Auth]: http://en.wikipedia.org/wiki/Basic_access_authentication
  [HTTPS]: http://en.wikipedia.org/wiki/HTTP_Secure
  [login]: /api/login/
  [createuser]: /api/user/#toc_1
