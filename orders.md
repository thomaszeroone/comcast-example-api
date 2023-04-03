# Orders API Open API 3.x Specification

This document describes the specification for the orders API

## /orders/[customerId]

### GET

Returns all orders from a specific customer ID.

#### Request Parameters

| Name | Type | In | Description | Required | Example |
| ---- | ---- | -- | ----------- | -------- | ------- |
| customerId | string(guid) | path | The customer ID of the orders to retrieve | Yes | "67647c99-ddb8-46b0-91e9-41f2176001e6" |

#### Response Parameters

| Name | Type | In | Description | Example |
| ---- | ---- | -- | ----------- | ------- |
| id | string(guid) | body | The ID of the order | "67647c99-ddb8-46b0-91e9-41f2176001e6" |
| addressId | string(guid) | body | The address ID of the address used for the order | "67647c99-ddb8-46b0-91e9-41f2176001e6" |
| cardId | string(guid) | body | The card ID of the card used for the order | "67647c99-ddb8-46b0-91e9-41f2176001e6" |
| items.id | string(guid) | body.items | The ID of an item in the order | "67647c99-ddb8-46b0-91e9-41f2176001e6" |
| items.quantity | int | body.items | The quantity of the item ordered | 1 |
| items.time | int | body.items | The timecode of the order | 1634810191 |
| time | int | body | The timecode of the order | 1634810191 |
| total | int | body | The total number of items in the order | 1 |

#### Code 200

OK. Normal response.

**Example response **

```
[
  {
    "id": "67647c99-ddb8-46b0-91e9-41f2176001e6",
    "addressId": "67647c99-ddb8-46b0-91e9-41f2176001e6",
    "cardId": "67647c99-ddb8-46b0-91e9-41f2176001e6",
    "items": [
      {
        "id": "67647c99-ddb8-46b0-91e9-41f2176001e6",
        "quantity": 1,
        "price": 1
      }
    ],
    "shipment": {
      "id": "67647c99-ddb8-46b0-91e9-41f2176001e6",
      "status": "shipped",
      "time": "1634810191"
    },
    "time": "1634810191",
    "total": 1
  }
]
```

#### Errors

| Code | Description |
| ---- | ---- | 
| 204 | No content | 
| 400 | Bad request | 
| 401 | Unauthorized | 
| 500 | Internal server error | 

### POST

Post an order by customer ID.

#### Request Parameters

| Name | Type | In | Description | Required | Example |
| ---- | ---- | -- | ----------- | -------- | ------- |
| customerId | string(guid) | path | The customer ID of the orders to retrieve | Yes | "67647c99-ddb8-46b0-91e9-41f2176001e6" |
| addressId | string(guid) | body | The address ID of the address used for the order | "67647c99-ddb8-46b0-91e9-41f2176001e6" |
| cardId | string(guid) | body | The card ID of the card used for the order | "67647c99-ddb8-46b0-91e9-41f2176001e6" |
| items.id | string(guid) | body.items | The ID of an item in the order | "67647c99-ddb8-46b0-91e9-41f2176001e6" |
| items.quantity | int | body.items | The quantity of the item ordered | 1 |
| items.time | int | body.items | The timecode of the order | 1634810191 |

#### Errors

| Code | Description |
| ---- | ---- | 
| 204 | No content | 
| 400 | Bad request | 
| 401 | Unauthorized | 
| 500 | Internal server error | 

## /orders/[customerId]/[orderId]

### GET

Returns a specific order from a customer ID and order ID.

#### Request Parameters

| Name | Type | In | Description | Required | Example |
| ---- | ---- | -- | ----------- | -------- | ------- |
| customerId | string(guid) | path | The customer ID of the order to retrieve | Yes | "67647c99-ddb8-46b0-91e9-41f2176001e6" |
| orderId | string(guid) | path | The order ID of the order to retrieve | Yes | "67647c99-ddb8-46b0-91e9-41f2176001e6" |

#### Response Parameters

| Name | Type | In | Description | Example |
| ---- | ---- | -- | ----------- | ------- |
| id | string(guid) | body | The ID of the order | "67647c99-ddb8-46b0-91e9-41f2176001e6" |
| addressId | string(guid) | body | The address ID of the address used for the order | "67647c99-ddb8-46b0-91e9-41f2176001e6" |
| cardId | string(guid) | body | The card ID of the card used for the order | "67647c99-ddb8-46b0-91e9-41f2176001e6" |
| items.id | string(guid) | body.items | The ID of an item in the order | "67647c99-ddb8-46b0-91e9-41f2176001e6" |
| items.quantity | int | body.items | The quantity of the item ordered | 1 |
| items.time | int | body.items | The timecode of the order | 1634810191 |
| time | int | body | The timecode of the order | 1634810191 |
| total | int | body | The total number of items in the order | 1 |

#### Code 200

OK. Normal response.

**Example response **

```
{
  "id": "67647c99-ddb8-46b0-91e9-41f2176001e6",
  "addressId": "67647c99-ddb8-46b0-91e9-41f2176001e6",
  "cardId": "67647c99-ddb8-46b0-91e9-41f2176001e6",
  "items": [
    {
      "id": "67647c99-ddb8-46b0-91e9-41f2176001e6",
      "quantity": 1,
      "price": 1
    }
  ],
  "shipment": {
    "id": "67647c99-ddb8-46b0-91e9-41f2176001e6",
    "status": "shipped",
    "time": "1634810191"
  },
  "time": "1634810191",
  "total": 1
}
```

#### Errors

| Code | Description |
| ---- | ---- | 
| 204 | No content | 
| 400 | Bad request | 
| 401 | Unauthorized | 
| 500 | Internal server error | 

## /health

### GET

Returns the health of the service.

#### Request Parameters

No parameters.

#### Response Parameters

| Name | Type | In | Description | Example |
| ---- | ---- | -- | ----------- | ------- |
| code | string | body | The ID code of the health status. | 1234 |
| message | string | body | Message returned by status query. | "error" |

#### Errors

| Code | Description |
| ---- | ---- | 
| 204 | No content | 
| 400 | Bad request | 
| 401 | Unauthorized | 
| 500 | Internal server error | 
