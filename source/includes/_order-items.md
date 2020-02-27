# Order Items

## Get Order Items

```javascript
import {
  HttpClient
} from '@angular/common/http';

const path = 'https://node.chefsurf.io/api/order-items';

constructor(private http: HttpClient) {
}

requestOrderItems(params) {
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
        }
    ]
}
```

This endpoint retrieves a list of order items that the staff / chef can see under the same ownership.

### HTTP Request

`GET https://node.chefsurf.io/api/order-items`

### URL Parameters

Parameter | Required    |  Description  |
--------- | ----------- | ------------- |
where_order | Yes | apply a 'order' condition to the query. i.e <strong>5e57c8252368c1531f31711b</strong>
where_status | No | apply a 'status' condition to the query. i.e <strong>placed</strong>. Options available `['placed', 'queue', 'cooking', 'delivering', 'ready_for_pickup', 'at_address', 'complete', 'returned', 'cancelled']`

## Get Order Item

> GET - https://node.chefsurf.io/order-items/:order_id

```javascript
import {
  HttpClient
} from '@angular/common/http';

const path = 'https://node.chefsurf.io/api/order-items';

constructor(private http: HttpClient) {
}

requestOrderItem(order_id, params) {
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
    }
}
```

This endpoint retrieves one order item by the ID.

### HTTP Request

`GET https://node.chefsurf.io/order-items/:order_id`
