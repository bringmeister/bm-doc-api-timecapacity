---
layout: page
categories: ["API"]
title: Matrix
---

# Matrix

All API requests to `{{ site.bringmeister.api }}/matrix` require __HTTPS__.

The matrix consists of a set of time slots that are in principle available
for the requested zip code that the customer selected. A slot is described
by a date, time slot begin, and time slot end.

## Retrieve the Matrix

Retrieving the matrix by ZIP Code.

```sh
$ curl {{ site.bringmeister.api }}/matrix/12345
```

> Response

```json
[{
  "id": "005c4826-4e28-11e3-a675-d43d7eece53d",
  "store_no":"2250274",
  "from": "{{ site.time | date: '%Y-%m-%d' }}T16:00:00{{ site.time | date: '%z' }}",
  "to": "{{ site.time | date: '%Y-%m-%d' }}T18:00:00{{ site.time | date: '%z' }}",
  "finish":"2014-06-07 09:45:00",
  "price":"5.55",
  "currency": "EUR",
  "capacity":"0",
  "working_shift":"1",
},
....
]
```

### HTTP Request

`GET {{ site.bringmeister.api }}/matrix/{zip}`

### Parameters

Parameter      | Description
---            | ---
`zip`          | VARCHAR(5) - The zip code as target location for food delivery __Required.__

### Response

Parameter       | Description
---             | ---
`id`            | VARCHAR(32) - UUID, The Slot Id
`store_no`      | INT - The Store Id
`from`          | DATETIME - Time of Slot Start
`to`            | DATETIME - Time of Slot End
`finish`        | DATETIME - Final datetime until this slot can be booked
`price`         | DECIMAL(6,4) - The price of the slot
`currency`      | VARCHAR(3) - Currency as defined by [ISO 4217][ISO 4217]
`capacity`      | INT
`working_shift` | TBD


[ISO 4217][http://de.wikipedia.org/wiki/ISO_4217]
