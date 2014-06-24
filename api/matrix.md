---
layout: page
categories: ["API"]
title: Matrix
---

# Matrix

All API requests to `{{ site.bringmeister.api }}/matrix` require __HTTPS__.

_TODO_ Detailed description what the matrix is!

## Retrieve the Matrix

The matrix consists of

```sh
$ curl {{ site.bringmeister.api }}/matrix/12345
```

> Response

```json
[{
  "id": "005c4826-4e28-11e3-a675-d43d7eece53d",
  "store_no":"2250274",
  "timeslot_no":"1",
  "slot_date":"2014-06-10",
  "from": "{{ site.time | date: '%Y-%m-%d' }}T16:00:00{{ site.time | date: '%z' }}",
  "to": "{{ site.time | date: '%Y-%m-%d' }}T18:00:00{{ site.time | date: '%z' }}",
  "finish":"2014-06-07 09:45:00",
  "price":"5.55",
  "currency": "EUR",
  "capacity":"0",
  "working_shift":"1",
  "delivery_zone":"1"
},
....
]
```

### HTTP Request

`GET {{ site.bringmeister.api }}/matrix/{zip}`

### Parameters

Parameter      | Description
---            | ---
`zip`          | String(10) The zip code as target location for food delivery __Required.__

### Response

Parameter       | Description
---             | ---
`id`            | String UUID, The Slot Id
`store_no`      | Int The Store Id
`timeslot_no`   |
`slot_date`     |
`from`          | DateTime Time of Slot Start
`to`            | DateTime Time of Slot End
`finish`        | DateTime
`price`         | Decimal(6,4) The price of the slot
`currency`      | String(3) Currency by ISO
`capacity`      |
`working_shift` |
`delivery_zone` |


