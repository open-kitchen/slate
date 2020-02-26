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
where_inventoryItem | apply a 'inventoryItem' condition to the query i.e <strong>5dd9790312256f10e83bb93f</strong>
where<_currentLoad | apply a 'currentLoad' condition to the query i.e <strong>10</strong>
where_identifier| apply a 'identifier' condition to the query i.e <strong>disp001</strong>

## Get a Order

> GET - https://node.chefsurf.io/open-kitchen/orders/:order_id

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
        "capacity": 0,
        "currentLoad": null,
        "active": false,
        "notes": "",
        "deleted": false,
        "_id": "5e118e9c11a8820b7ea66efa",
        "inventoryItem": "5dd9790312256f10e83bb93f",
        "label": "Order A",
        "identifier": "disp1",
        "restaurant": "5dd9790212256f10e83bb934",
        "owner": "5dd9790112256f10e83bb932",
        "updatedAt": "2020-01-05T07:28:11.412Z",
        "createdAt": "2020-01-05T07:22:04.868Z",
        "__v": 0
    }
}
```

This endpoint retrieves one order by the ID.

### HTTP Request

`GET https://node.chefsurf.io/open-kitchen/orders/:order_id`

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

const path = 'https://node.chefsurf.io/api/orders';

constructor(private http: HttpClient) {
}

createOrder(data) {
  return this.http.post(`${path}`, data, {
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
        "capacity": null,
        "currentLoad": null,
        "active": false,
        "notes": "",
        "_id": "5e118e9c11a8820b7ea66efa",
        "deleted": false,
        "inventoryItem": "5dd9790312256f10e83bb93f",
        "label": "Lettuce",
        "identifier": "lettuce_refid.",
        "restaurant": "5dd9790212256f10e83bb934",
        "owner": "5dd9790112256f10e83bb932",
        "updatedAt": "2020-01-05T07:22:04.868Z",
        "createdAt": "2020-01-05T07:22:04.868Z",
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
  
  "active": true,
  "capacity": 50
}
```

> The above command returns JSON structured like this:

```json
{
    "data": {
        "capacity": 50,
        "currentLoad": null,
        "active": true,
        "notes": "",
        "deleted": false,
        "_id": "5e118e9c11a8820b7ea66efa",
        "inventoryItem": "5dd9790312256f10e83bb93f",
        "label": "Lettuce",
        "identifier": "lettuce_refid.",
        "restaurant": "5dd9790212256f10e83bb934",
        "owner": "5dd9790112256f10e83bb932",
        "updatedAt": "2020-01-05T07:28:11.412Z",
        "createdAt": "2020-01-05T07:22:04.868Z",
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
label     | String | You can modify the label (human friendly identifier)
identifier | String | You can modify the identifier ( it has to be unique )
inventoryItem | ObjectID | You can assign an InventoryItem to the order to track statistics.
capacity | Number | You can set the capacity the order has (maximum load)
currentLoad | Number | You can set the current load (so we can notify the staff about low quantities).
active | Boolean | You can Enable/Disable the order.
notes | String | You can add some notes to the order in case there are some special instructions.

### Non fillable

Parameter | Type | Description
--------- | ---- | ------------
_id       | ObjectID | Primary key
restaurant| ObjectID | Restaurant Object ID
owner     | ObjectID | Ower Object ID
updatedAt | DateTime | Update timestamps - auto generated.
createdAt | DateTime | Create timestamps - auto generated.

## Delete Order 


> DELETE - https://node.chefsurf.io/api/orders/order_id

```javascript
import {
  HttpClient
} from '@angular/common/http';

const path = 'https://node.chefsurf.io/api/orders';

constructor(private http: HttpClient) {
}

/**
 * @param {String} order_id
*/
deleteOrder(order_id) {
  return this.http.delete(`${path}/${order_id}`, {
    {}, 
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
        "capacity": 50,
        "currentLoad": null,
        "active": true,
        "notes": "",
        "deleted": true,
        "_id": "5e118e9c11a8820b7ea66efa",
        "inventoryItem": "5dd9790312256f10e83bb93f",
        "label": "Lettuce",
        "identifier": "lettuce_refid.",
        "restaurant": "5dd9790212256f10e83bb934",
        "owner": "5dd9790112256f10e83bb932",
        "updatedAt": "2020-01-05T07:30:56.098Z",
        "createdAt": "2020-01-05T07:22:04.868Z",
        "__v": 0,
        "deletedAt": "2020-01-05T07:30:56.096Z"
    }
}
```

> If you are trying to delete a order that it has been deleted, you will get an exception: 404.

```json
{
    "code": "NotFound",
    "message": "Record not found."
}
```

This endpoint deletes a specific order.

### HTTP Request

`DELETE - https://node.chefsurf.io/api/orders/order_id`


