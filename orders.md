# Orders API Open API 3.x Specification
{:.no_toc}

Our orders service provides visibility to our ordering system by customer. Use the order API to retrieve orders belonging to a specified customer, or to create a new order for a customer. Only users with a valid oauth token may retrieve and place orders.

* toc
{:toc}

## /orders/[customerId]

### GET

Retrieve all orders from a specific customer ID. The response will be a list of orders. Each order will have an order ID, an address ID, a credit card ID, a time, and a total quantity of items ordered. An order will also include a list of items ordered. 

#### Request Parameters

| Name | Type | In | Description | Required | Example |
| ---- | ---- | -- | ----------- | -------- | ------- |
| customerId | string(guid) | path | The customer ID to retrieve orders for | Yes | "67647c99-ddb8-46b0-91e9-41f2176001e6" |

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

**Example response**

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

Post an order for a specified customer ID. Order details in an order may include an address ID, a credit card ID, and a list of items.

#### Request Parameters

| Name | Type | In | Description | Required | Example |
| ---- | ---- | -- | ----------- | -------- | ------- |
| customerId | string(guid) | path | The customer ID of the orders to retrieve | Yes | "67647c99-ddb8-46b0-91e9-41f2176001e6" |
| addressId | string(guid) | body | The address ID of the address used for the order | No | "67647c99-ddb8-46b0-91e9-41f2176001e6" |
| cardId | string(guid) | body | The card ID of the card used for the order | No | "67647c99-ddb8-46b0-91e9-41f2176001e6" |
| items.id | string(guid) | body.items | The ID of an item in the order | No | "67647c99-ddb8-46b0-91e9-41f2176001e6" |
| items.quantity | int | body.items | The quantity of the item ordered }No | | 1 |
| items.time | int | body.items | The timecode of the order | No | 1634810191 |

#### Errors

| Code | Description |
| ---- | ---- | 
| 204 | No content | 
| 400 | Bad request | 
| 401 | Unauthorized | 
| 500 | Internal server error | 

## /orders/[customerId]/[orderId]

### GET

Retrieve a specific order for a specified customer ID. Each order will have an order ID, an address ID, a credit card ID, a time, and a total quantity of items ordered. An order will also include a list of items ordered.

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

**Example respons**

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


## Schemas

### OrderRequest

An order request consists of an addressId, cardId, and a list of items. Each item has an ID, a quantity, and a price.

| Name | Type | Min length | Max length | Description |
| ---- | ---- | ---------- | ---------- | ----------- |
| addressId | string(guid) | 36 | 36 | The ID for an order address |
| cardId | string(guid) | 36 | 36 | The ID for a credit card |
| items.id | string(guid) | 36 | 36  | Item ID |
| items.quantity | number | 1 |  | Quantity of an item |
| items.price | number | 1 |  | Price of an item |

### OrderResponse

An order response consists an order ID, an address ID, a card ID, a time ordered, and a total amount ordered. It also includes a list of items and a list of shipments. Each item has an ID, a quantity, and a price. Each shipment has an ID, a status, and a time. 

| Name | Type | Min length | Max length | Description |
| ---- | ---- | ---------- | ---------- | ----------- |
| addressId | string(guid) | 36 | 36 | The ID for an order address |
| cardId | string(guid) | 36 | 36 | The ID for a credit card |
| items.id | string(guid) | 36 | 36  | Item ID |
| items.quantity | number | 1 |  | Quantity of an item |
| items.price | number | 1 |  | Price of an item |
| time | string | 1 | 20 | A time code specifying when the order was placed |
| total | number | 1 | | Total quantity of items in the order |
| shipment.id | string(guid) | 36 | 36 | The ID for a shipment |
| shipment.status | string | 1 | | The status of the shipment |
| shipment.time | string | 1 | 20 | A time code specifying when the shipment was made |
