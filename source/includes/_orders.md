# Orders

## Get Orders

```javascript
import {
  HttpClient
} from '@angular/common/http';

const path = 'https://node.chefsurf.io/api/orders';

constructor(private http: HttpClient) {
}

requestOrders(params) {
  return this.http.get(`${path}`, {
    params, 
    headers: {
      Authorization: `JWT ${jwt_token}`
    }
  });
}
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "_id": "5e2f9e6eb5b3c35900fb1399",
      "references": {
        ...
      },
      "shoppingCartItems": [
          "5e2f9e63b5b3c35900fb1385"
      ],
      "type": "client",
      "receivingMethod": "eat_here",
      "delivery": false,
      "pickup": false,
      "deliveryFee": 1,
      "subTotal": 24000,
      "discount": 0,
      "taxes": 1920,
      "total": 25920,
      "status": "draft",
      "foodStatus": "not_started",
      "paymentStatus": "pending",
      "deliveryStatus": "pending",
      "payUResponses": [],
      "origin": "web",
      "appVersion": "not_set",
      "orderItems": [
          "5e2f9e6eb5b3c35900fb139a"
      ],
      "deleted": false,
      "shoppingCart": "5e141f4b0936d17468f716c8",
      "customer": "5dfc657506b7c674c1fbf0de",
      "restaurant": "5dd9790212256f10e83bb934",
      "referenceOrder": null,
      "paymentMethod": "cash",
      "updatedAt": "2020-01-28T02:37:34.988Z",
      "createdAt": "2020-01-28T02:37:34.940Z",
      "__v": 1
    }, ...
  ]
```

This endpoint retrieves a list of orders that the staff / chef can see under the same ownership.

### HTTP Request

`GET https://node.chefsurf.io/api/orders`

### URL Parameters

Parameter | Description |
--------- | ----------- |
where_active | apply a 'active' condition to the query. i.e <strong>true</strong>
where_type | apply a 'type' condition to the query i.e <strong>client</strong>
where_origin | apply a 'origin' condition to the query i.e <strong>web</strong>
where_receivingMethod| apply a 'receivingMethod' condition to the query i.e <strong>eat_here</strong>
where_paymentMethod| apply a 'paymentMethod' condition to the query i.e <strong>cash</strong>

## Get a Order

> GET - https://node.chefsurf.io/orders/:order_id

```javascript
import {
  HttpClient
} from '@angular/common/http';

const path = 'https://node.chefsurf.io/api/orders';

constructor(private http: HttpClient) {
}

requestOrder(order_id, params) {
  return this.http.get(`${path}/${order_id}`, {
    params, 
    headers: {
      Authorization: `JWT ${jwt_token}`
    }
  });
}
```

> The above command returns JSON structured like this:

```json
{
  "data": {
    "_id": "5e2f9e6eb5b3c35900fb1399",
    "references": {
      ...
    },
    "shoppingCartItems": [
        "5e2f9e63b5b3c35900fb1385"
    ],
    "type": "client",
    "receivingMethod": "eat_here",
    "delivery": false,
    "pickup": false,
    "deliveryFee": 1,
    "subTotal": 24000,
    "discount": 0,
    "taxes": 1920,
    "total": 25920,
    "status": "draft",
    "foodStatus": "not_started",
    "paymentStatus": "pending",
    "deliveryStatus": "pending",
    "payUResponses": [],
    "origin": "web",
    "appVersion": "not_set",
    "orderItems": [
        "5e2f9e6eb5b3c35900fb139a"
    ],
    "deleted": false,
    "shoppingCart": "5e141f4b0936d17468f716c8",
    "customer": "5dfc657506b7c674c1fbf0de",
    "restaurant": "5dd9790212256f10e83bb934",
    "referenceOrder": null,
    "paymentMethod": "cash",
    "updatedAt": "2020-01-28T02:37:34.988Z",
    "createdAt": "2020-01-28T02:37:34.940Z",
    "__v": 1
  }
}
```

This endpoint retrieves one order by the ID.

### HTTP Request

`GET https://node.chefsurf.io/orders/:order_id`

<!-- ### URL Parameters -->
<!-- 
Parameter | Description
--------- | -----------
ID | The ID of the kitten to delete
 -->

## Create a Order

> POST = https://node.chefsurf.io/api/orders

```javascript
  import {
  HttpClient
} from '@angular/common/http';

const path = 'https://node.chefsurf.io/api/orders/process';

constructor(private http: HttpClient) {
}

placeOrder(data) {
  return this.http.post(`${path}`, data, {
    headers: {
      Authorization: `JWT ${jwt_token}`
    }
  });
}
```

> Sample data to create an order

```json
{
  "shoppingCart": "5e57c80d2368c1531f317108",
  "paymentMethod": "cash",
  "deliveryFee": 0,
}
```

> The above command returns JSON structured like this:

```json
{
  "data": {
      "references": {
          "shoppingCartItems": []
      },
      "shoppingCartItems": ["5e57c81f2368c1531f317109"],
      "type": "client",
      "receivingMethod": "eat_here",
      "deliveryFee": 0,
      "subTotal": 12000,
      "discount": 0,
      "taxes": 960,
      "total": 12960,
      "status": "draft",
      "foodStatus": "not_started",
      "paymentStatus": "pending",
      "deliveryStatus": "none",
      "payUResponses": [],
      "origin": "web",
      "appVersion": "not_set",
      "orderItems": [{
          "complete": false,
          "status": "placed",
          "priority": "normal",
          "deleted": false,
          "_id": "5e57c8252368c1531f31711c",
          "order": "5e57c8252368c1531f31711b",
          "restaurant": "5dd9790212256f10e83bb934",
          "customer": "5dfc657506b7c674c1fbf0de",
          "date": "2020-02-27",
          "dateTime": "2020-02-27 13:47:00",
          "shoppingCartItem": "5e57c81f2368c1531f317109",
          "product": "5dd9797f12256f10e83bb9c8",
          "total": 12000,
          "updatedAt": "2020-02-27T13:46:13.354Z",
          "createdAt": "2020-02-27T13:46:13.354Z",
          "__v": 0
      }],
      "deleted": false,
      "_id": "5e57c8252368c1531f31711b",
      "shoppingCart": "5e57c80d2368c1531f317108",
      "customer": "5dfc657506b7c674c1fbf0de",
      "restaurant": "5dd9790212256f10e83bb934",
      "referenceOrder": null,
      "paymentMethod": "cash",
      "updatedAt": "2020-02-27T13:46:13.358Z",
      "createdAt": "2020-02-27T13:46:13.358Z",
      "__v": 0
  }
}
```

This endpoint allows you to create a new order. if you create a new order you need to be aware that you need to make sure to add a identifier that is not taken already. otherwise it will throw an exception.


## Update a Order 

> PUT - https://node.chefsurf.io/api/orders/order_id

```javascript
import {
  HttpClient
} from '@angular/common/http';

const path = 'https://node.chefsurf.io/api/orders';

constructor(private http: HttpClient) {
}

updateOrder(order_id, params) {
  return this.http.put(`${path}/${order_id}`, params, {
    headers: {
      Authorization: `JWT ${jwt_token}`
    }
  });
}
```

> Sample Data ( you can send the params you want to be updated in your request )

```json
{
  "type": "chef",
  "receivingMethod": "to_go",
  "status": "complete",
  "foodStatus": "packed",
  "paymentStatus": "paid",
  "deliveryStatus": "delivered"
}
```

> The above command returns JSON structured like this:

```json
{
    "data": {
        "references": {
            "shoppingCartItems": []
        },
        "shoppingCartItems": ["5e57c81f2368c1531f317109"],
        "type": "chef",
        "receivingMethod": "to_go",
        "deliveryFee": 0,
        "subTotal": 12000,
        "discount": 0,
        "taxes": 960,
        "total": 12960,
        "status": "complete",
        "foodStatus": "packed",
        "paymentStatus": "paid",
        "deliveryStatus": "delivered",
        "payUResponses": [],
        "origin": "web",
        "appVersion": "not_set",
        "orderItems": [{
            "complete": false,
            "status": "placed",
            "priority": "normal",
            "deleted": false,
            "_id": "5e57c8252368c1531f31711c",
            "order": "5e57c8252368c1531f31711b",
            "restaurant": "5dd9790212256f10e83bb934",
            "customer": "5dfc657506b7c674c1fbf0de",
            "date": "2020-02-27",
            "dateTime": "2020-02-27 13:47:00",
            "shoppingCartItem": "5e57c81f2368c1531f317109",
            "product": "5dd9797f12256f10e83bb9c8",
            "total": 12000,
            "updatedAt": "2020-02-27T13:46:13.354Z",
            "createdAt": "2020-02-27T13:46:13.354Z",
            "__v": 0
        }],
        "deleted": false,
        "_id": "5e57c8252368c1531f31711b",
        "shoppingCart": "5e57c80d2368c1531f317108",
        "customer": "5dfc657506b7c674c1fbf0de",
        "restaurant": "5dd9790212256f10e83bb934",
        "referenceOrder": null,
        "paymentMethod": "cash",
        "updatedAt": "2020-02-27T13:46:13.358Z",
        "createdAt": "2020-02-27T13:46:13.358Z",
        "__v": 0
    }
}



{
  "data": {
      "references": {
          "shoppingCartItems": []
      },
      "shoppingCartItems": ["5e57c81f2368c1531f317109"],
      "type": "client",
      "receivingMethod": "eat_here",
      "deliveryFee": 0,
      "subTotal": 12000,
      "discount": 0,
      "taxes": 960,
      "total": 12960,
      "status": "draft",
      "foodStatus": "not_started",
      "paymentStatus": "pending",
      "deliveryStatus": "none",
      "payUResponses": [],
      "origin": "web",
      "appVersion": "not_set",
      "orderItems": [{
          "complete": false,
          "status": "placed",
          "priority": "normal",
          "deleted": false,
          "_id": "5e57c8252368c1531f31711c",
          "order": "5e57c8252368c1531f31711b",
          "restaurant": "5dd9790212256f10e83bb934",
          "customer": "5dfc657506b7c674c1fbf0de",
          "date": "2020-02-27",
          "dateTime": "2020-02-27 13:47:00",
          "shoppingCartItem": "5e57c81f2368c1531f317109",
          "product": "5dd9797f12256f10e83bb9c8",
          "total": 12000,
          "updatedAt": "2020-02-27T13:46:13.354Z",
          "createdAt": "2020-02-27T13:46:13.354Z",
          "__v": 0
      }],
      "deleted": false,
      "_id": "5e57c8252368c1531f31711b",
      "shoppingCart": "5e57c80d2368c1531f317108",
      "customer": "5dfc657506b7c674c1fbf0de",
      "restaurant": "5dd9790212256f10e83bb934",
      "referenceOrder": null,
      "paymentMethod": "cash",
      "updatedAt": "2020-02-27T13:46:13.358Z",
      "createdAt": "2020-02-27T13:46:13.358Z",
      "__v": 0
  }
}
```

This endpoint allows you to modify the order, not all of the properties can be modified and there are formats that must be followed otherwise it will throw an error.

### HTTP Request

`PUT - https://node.chefsurf.io/api/orders/order_id`

### Fillable properties

Parameter | Type   | Description |
--------- | ------ | ----------- |
type      | String | it indicates the order type `chef` or `client`.
receivingMethod | String | it indicates the receiving method. Options: `'delivery', 'eat_here', 'to_go']`
status    | String | it indicates the status of the order. Options: `['draft', 'placed', 'preparing_order', 'delivering', 'ready_for_pickup', 'at_address', 'complete', 'refunded', 'cancelled']`
foodStatus | String | it indicates the food status of the order. Options: `['not_started', 'preparing', 'cooked', 'packed']`
paymentStatus | String | it indicates the payment status of the order. Options: `['pending', 'validating', 'paid', 'rejected']`
deliveryStatus | String | if the receivingMethos is `delivery` then this property indicates the delivery status. Options: `['pending', 'delivering', 'at_address', 'delivered', 'returned', 'user_not_showed_up', 'at_front']`
cancellationReason | String | it indicates the cancellation reason for the order. This is helpful to keep track of cancelled orders and analyze them
### Non fillable

Parameter | Type | Description
--------- | ---- | ------------
_id       | ObjectID | Primary key
restaurant| ObjectID | Restaurant Object ID
customer  | ObjectID | Customer Object ID
shoppingCartItems | Array | Array of ShoppingCartItems
referenceOrder | ObjectID | reference order , clone-parent order
deliveryFee | Number | cost of the delivery
subTotal | Number | sum of order items total
discount | Number | discount amount applied
taxes    | Number | taxes amount applied
total    | Number | order total (subtotal - discount + taxes)
paymentMethod | String | it indicates the payment method selected for this order. Options: `['cash', 'credit_card', 'credits', 'cash_and_credits', 'credit_card_and_credits']`
appVersion | String | it indicates the version of the app where the order was placed
orderItems | Array | Array of order items
origin     | String | it indicates where the order came from. Options: ` enum: ['web', 'android', 'ios', 'bot']`
updatedAt | DateTime | Update timestamps - auto generated
createdAt | DateTime | Create timestamps - auto generated
