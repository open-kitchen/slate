# Shopping Carts

## Get Shopping Carts

```javascript
import {
  HttpClient
} from '@angular/common/http';

const path = 'https://node.chefsurf.io/api/shopping-carts';

constructor(private http: HttpClient) {
}

requestShoppingCarts(params) {
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
  
    "data": {
        "completed": false,
        "order": null,
        "dates": [],
        "shoppingCartItems": [
            "5e52fb397896c40fb0833efc",
            ...
        ],
        "creditsUsed": 0,
        "subTotal": 12000,
        "discount": 2000,
        "taxes": 960,
        "total": 10960,
        "_id": "5e40da7bdd54ce1b2f57d7ec",
        "restaurant": "5dd9790212256f10e83bb934",
        "owner": "5dfc657506b7c674c1fbf0dd",
        "user": "5dfc657506b7c674c1fbf0de",
        "updatedAt": "2020-02-23T22:22:49.495Z",
        "createdAt": "2020-02-10T04:22:19.400Z",
        "__v": 1
    }

}
```

This endpoint retrieves the latest active shopping cart the user has. this endpoint is useful if you don't know the shopping cart id that is active at the moment.

### HTTP Request

`GET https://node.chefsurf.io/api/shopping-carts`

### URL Parameters

Parameter | Description |
--------- | ----------- |
where_completed | apply a 'completed' condition to the query. i.e <strong>true</strong>
where_active | apply a 'active' condition to the query i.e <strong>true</strong>
where_total | apply a 'total' condition to the query i.e <strong>25000</strong>

## Get Shopping Cart

> GET - https://node.chefsurf.io/open-kitchen/shopping-carts/:shopping_cart_id

```javascript
import {
  HttpClient
} from '@angular/common/http';

const path = 'https://node.chefsurf.io/api/shopping-carts';

constructor(private http: HttpClient) {
}

requestShoppingCart(shopping_cart_id, params) {
  return this.http.get(`${path}/${shopping_cart_id}`, {
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
        "completed": false,
        "order": null,
        "dates": [],
        "shoppingCartItems": [
            "5e52fb397896c40fb0833efc",
            ...
        ],
        "creditsUsed": 0,
        "subTotal": 12000,
        "discount": 2000,
        "taxes": 960,
        "total": 10960,
        "_id": "5e40da7bdd54ce1b2f57d7ec",
        "restaurant": "5dd9790212256f10e83bb934",
        "owner": "5dfc657506b7c674c1fbf0dd",
        "user": "5dfc657506b7c674c1fbf0de",
        "updatedAt": "2020-02-23T22:22:49.495Z",
        "createdAt": "2020-02-10T04:22:19.400Z",
        "__v": 1
    }
}
```

This endpoint retrieves one shopping cart by the ID.

### HTTP Request

`GET https://node.chefsurf.io/open-kitchen/shopping-carts/:shopping_cart_id`

<!-- ### URL Parameters -->
<!-- 
Parameter | Description
--------- | -----------
ID | The ID of the kitten to delete
 -->

## Create Shopping Cart

> POST = https://node.chefsurf.io/api/shopping-carts

```javascript
  import {
  HttpClient
} from '@angular/common/http';

const path = 'https://node.chefsurf.io/api/shopping-carts';

constructor(private http: HttpClient) {
}

createShoppingCart(data) {
    return this.http.post(`${path}`, data, {
        headers: {
        Authorization: `JWT ${jwt_token}`
        }
    });
}
```

> Sample Data when creating a new shopping cart

```json
{
  "newItem": {
      //...shoppingCartItemData
  },
  "restaurant": "5dd9790212256f10e83bb934",
  "coupon": "3de5970157956f10d23bc628",
  "creditsUsed": 2000
}
```

> The above command returns JSON structured like this:

```json
{
    "data": {
        "completed": false,
        "order": null,
        "dates": [],
        "shoppingCartItems": [
            "5e52fb397896c40fb0833efc",
            ...
        ],
        "creditsUsed": 2000,
        "subTotal": 12000,
        "discount": 0,
        "taxes": 960,
        "total": 10960,
        "_id": "5e40da7bdd54ce1b2f57d7ec",
        "restaurant": "5dd9790212256f10e83bb934",
        "owner": "5dfc657506b7c674c1fbf0dd",
        "user": "5dfc657506b7c674c1fbf0de",
        "updatedAt": "2020-02-23T22:22:49.495Z",
        "createdAt": "2020-02-10T04:22:19.400Z",
        "__v": 1
    }
}
```

This endpoint allows you to create a new shopping cart. you cannot have two active shopping carts since we need to complete order first to open a new cart.

## Update Shopping Cart 

> PUT - https://node.chefsurf.io/api/shopping-carts/shopping_cart_id

```javascript
import {
  HttpClient
} from '@angular/common/http';

const path = 'https://node.chefsurf.io/api/shopping-carts';

constructor(private http: HttpClient) {
}

updateShoppingCart(shopping_cart_id, params) {
  return this.http.put(`${path}/${shopping_cart_id}`, params, {
    headers: {
      Authorization: `JWT ${jwt_token}`
    }
  });
}
```

> Sample Data ( you can send the params you want to be updated in your request )

```json
{
  "completed": true,
}
```

> The above command returns JSON structured like this:

```json
{
    "data": {
        "completed": true,
        "order": null,
        "dates": [],
        "shoppingCartItems": [
            "5e52fb397896c40fb0833efc",
            ...
        ],
        "creditsUsed": 0,
        "subTotal": 12000,
        "discount": 2000,
        "taxes": 960,
        "total": 10960,
        "_id": "5e40da7bdd54ce1b2f57d7ec",
        "restaurant": "5dd9790212256f10e83bb934",
        "owner": "5dfc657506b7c674c1fbf0dd",
        "user": "5dfc657506b7c674c1fbf0de",
        "updatedAt": "2020-02-23T22:22:49.495Z",
        "createdAt": "2020-02-10T04:22:19.400Z",
        "__v": 1
    }
}
```

This endpoint allows you to modify the shopping cart, not all of the properties can be modified and there are formats that must be followed otherwise it will throw an error.

### HTTP Request

`PUT - https://node.chefsurf.io/api/shopping-carts/shopping_cart_id`

### Fillable properties

Parameter   | Type      |   Description     |
---------   | ------    |   -----------     |
completed   | Boolean   | true or false, this will define when the cart has been completed based on the order Object ID assigment.  
coupon      | ObjectID  | Coupon Object ID.
creditsUsed | Number    | Quantity of credits used - pending to create Credit Object ID.
order       | ObjectID  | Order Object ID.

### Non fillable

Parameter | Type        | Description
--------- | ----------- | ------------
_id       | ObjectID    | Primary key
restaurant| ObjectID    | Restaurant Object ID
owner     | ObjectID    | Ower Object ID
user      | ObjectID    | User Object ID 
updatedAt | DateTime    | Update timestamps - auto generated.
createdAt | DateTime    | Create timestamps - auto generated.

## Delete Shopping Cart 


> DELETE - https://node.chefsurf.io/api/shopping-carts/shopping_cart_id

```javascript
import {
  HttpClient
} from '@angular/common/http';

const path = 'https://node.chefsurf.io/api/shopping-carts';

constructor(private http: HttpClient) {
}

/**
 * @param {String} shopping_cart_id
*/
deleteShoppingCart(shopping_cart_id) {
  return this.http.delete(`${path}/${shopping_cart_id}`, {
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
        "completed": true,
        "order": null,
        "dates": [],
        "shoppingCartItems": [
            "5e52fb397896c40fb0833efc",
            ...
        ],
        "creditsUsed": 0,
        "subTotal": 12000,
        "discount": 2000,
        "taxes": 960,
        "total": 10960,
        "_id": "5e40da7bdd54ce1b2f57d7ec",
        "restaurant": "5dd9790212256f10e83bb934",
        "owner": "5dfc657506b7c674c1fbf0dd",
        "user": "5dfc657506b7c674c1fbf0de",
        "updatedAt": "2020-02-23T22:22:49.495Z",
        "createdAt": "2020-02-10T04:22:19.400Z",
        "__v": 1,
        "deletedAt": "2020-02-23T22:30:00.400Z"
    }
}
```

> If you are trying to delete a shopping cart that it has been deleted, you will get an exception: 404.

```json
{
    "code": "NotFound",
    "message": "Record not found."
}
```

This endpoint deletes a specific shopping cart.

### HTTP Request

`DELETE - https://node.chefsurf.io/api/shopping-carts/shopping_cart_id`


