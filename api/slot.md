---
layout: page
categories: ["API"]
title: Slots
---

# Slots

All API requests to `{{ site.bringmeister.api }}/slot` require __HTTPS__.

_TODO_ Detailed description what a slot is!

## Reserve a Slot

_TODO_ Define

```sh
$ curl {{ site.bringmeister.api }}/slot/005c4826-4e28-11e3-a675-d43d7eece53d/12345
```

> Response

```json
{
  "id": "005c4826-4e28-11e3-a675-d43d7eece53d",
  "delivery_zone": "1",
  "store_no": "1234567",
  "price": "4.44",
  "from": "{{ site.time | date: '%Y-%m-%d' }}T16:00:00{{ site.time | date: '%z' }}",
  "to": "{{ site.time | date: '%Y-%m-%d' }}T18:00:00{{ site.time | date: '%z' }}"
}
```

### HTTP Request

`GET {{ site.bringmeister.api }}/slot`


### Parameters

Parameter      | Description
---            | ---
`slot_id    `  | The id of the selected slot __Required.__
`zip`          | The zip code of selected slot  __Required.__


## Book a Slot

_TODO_ Define

```sh
$ curl {{ site.bringmeister.api }}/slot \
    -d slot_id=005c4826-4e28-11e3-a675-d43d7eece53d \
    --data-urlencode zip="012345"
```

> Response

```json
{
  "id": "005c4826-4e28-11e3-a675-d43d7eece53d",
  "delivery_zone": "1",
  "store_no": "1234567",
  "price": "4.44",
  "from": "{{ site.time | date: '%Y-%m-%d' }}T16:00:00{{ site.time | date: '%z' }}",
  "to": "{{ site.time | date: '%Y-%m-%d' }}T18:00:00{{ site.time | date: '%z' }}"
}
```

### HTTP Request

`POST {{ site.bringmeister.api }}/slot`

### Parameters

Parameter      | Description
---            | ---
`slot_id    `  | The id of the selected slot __Required.__
`zip`          | The zip code of selected slot  __Required.__


## Cancel a Slot

_TODO_ Define

```sh
$ curl {{ site.bringmeister.api }}/slot/005c4826-4e28-11e3-a675-d43d7eece53d
```

> Response

```json
{
  "id": "005c4826-4e28-11e3-a675-d43d7eece53d",
  "delivery_zone": "1",
  "store_no": "1234567",
  "price": "4.44",
  "from": "{{ site.time | date: '%Y-%m-%d' }}T16:00:00{{ site.time | date: '%z' }}",
  "to": "{{ site.time | date: '%Y-%m-%d' }}T18:00:00{{ site.time | date: '%z' }}"
}
```

### HTTP Request

`DELETE {{ site.bringmeister.api }}/slot/{slot_id}`

### Parameters

Parameter      | Description
---            | ---
`slot_id    `  | The id of the selected slot __Required.__


## Release a Slot

_TODO_ Define

```sh
$ curl {{ site.bringmeister.api }}/slot/005c4826-4e28-11e3-a675-d43d7eece53d/12345
```

> Response

```json
{
  "id": "005c4826-4e28-11e3-a675-d43d7eece53d",
  "delivery_zone": "1",
  "store_no": "1234567",
  "price": "4.44",
  "from": "{{ site.time | date: '%Y-%m-%d' }}T16:00:00{{ site.time | date: '%z' }}",
  "to": "{{ site.time | date: '%Y-%m-%d' }}T18:00:00{{ site.time | date: '%z' }}"
}
```

### HTTP Request

`PUT {{ site.bringmeister.api }}/slot/{slot_id}/{zip}`

### Parameters

Parameter      | Description
---            | ---
`slot_id    `  | The id of the selected slot __Required.__
