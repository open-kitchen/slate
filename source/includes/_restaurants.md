# Restaurants

## Get Restaurants

```javascript
import {
  HttpClient
} from '@angular/common/http';

const path = 'https://node.chefsurf.io/api/restaurants';

constructor(private http: HttpClient) {
}

requestRestaurants(params) {
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
            "chefs": [
                "5dd9790212256f10e83bb936",
                "5dd9790212256f10e83bb938",
                "5dd9790212256f10e83bb93a",
                "5dd9790212256f10e83bb93c",
                "5dd9790312256f10e83bb93e"
            ],
            "logo": null,
            "background": null,
            "name": "Satee",
            "automatedKitchen": true,
            "deliveryAvailable": true,
            "pickUpAvailable": true,
            "cashPaymentAvailable": true,
            "creditCardPaymentAvailable": true,
            "deleted": false,
            "_id": "5dd9790212256f10e83bb934",
            "defaultDeliveryGuy": null,
            "domain": "comesate.com",
            "owner": "5dd9790112256f10e83bb932",
            "user": "5dd9790112256f10e83bb933",
            "updatedAt": "2019-11-23T18:22:59.212Z",
            "createdAt": "2019-11-23T18:22:58.081Z",
            "__v": 1
        }
    ]
}
```

This endpoint retrieves a list of restaurants that the staff / chef can see under the same ownership.

### HTTP Request

`GET https://node.chefsurf.io/api/restaurants`

### URL Parameters

Parameter | Description |
--------- | ----------- |
where_name | apply a name condition to the query. i.e <strong>Satee</strong>
where_domain | apply a domain condition to the query i.e <strong>comesate.com</strong>

## Get a Restaurant

> GET - https://node.chefsurf.io/open-kitchen/restaurants/:restaurant_id

```javascript
import {
  HttpClient
} from '@angular/common/http';

const path = 'https://node.chefsurf.io/api/restaurants';

constructor(private http: HttpClient) {
}

requestRestaurant(restaurant_id, params) {
  return this.http.get(`${path}/${restaurant_id}`, {
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
        "chefs": [
            "5dd9790212256f10e83bb936",
            "5dd9790212256f10e83bb938",
            "5dd9790212256f10e83bb93a",
            "5dd9790212256f10e83bb93c",
            "5dd9790312256f10e83bb93e"
        ],
        "logo": null,
        "background": null,
        "name": "Satee",
        "automatedKitchen": true,
        "deliveryAvailable": true,
        "pickUpAvailable": true,
        "cashPaymentAvailable": true,
        "creditCardPaymentAvailable": true,
        "deleted": false,
        "_id": "5dd9790212256f10e83bb934",
        "defaultDeliveryGuy": null,
        "domain": "comesate.com",
        "owner": "5dd9790112256f10e83bb932",
        "user": "5dd9790112256f10e83bb933",
        "updatedAt": "2019-11-23T18:22:59.212Z",
        "createdAt": "2019-11-23T18:22:58.081Z",
        "__v": 1
    }
}
```

This endpoint retrieves one restaurant by the ID.

### HTTP Request

`GET https://node.chefsurf.io/open-kitchen/restaurants/:restaurant_id`

<!-- ### URL Parameters -->
<!-- 
Parameter | Description
--------- | -----------
ID | The ID of the kitten to delete
 -->

## Create Restaurant

> POST = https://node.chefsurf.io/api/restaurants

```javascript
  import {
  HttpClient
} from '@angular/common/http';

const path = 'https://node.chefsurf.io/api/restaurants';

constructor(private http: HttpClient) {
}

createRestaurant(data) {
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
        "chefs": [],
        "logo": null,
        "background": null,
        "name": "New restaurant",
        "automatedKitchen": false,
        "deliveryAvailable": true,
        "pickUpAvailable": false,
        "cashPaymentAvailable": true,
        "creditCardPaymentAvailable": true,
        "_id": "5e0ec1eb8fbe5c18ac3f72e3",
        "deleted": false,
        "domain": "newrestaurant.dev",
        "owner": "5dd9790112256f10e83bb932",
        "user": "5dd9790212256f10e83bb937",
        "updatedAt": "2020-01-03T04:24:11.972Z",
        "createdAt": "2020-01-03T04:24:11.972Z",
        "__v": 0
    }
}
```

This endpoint allows you to create a new restaurant. if you create a new restaurant you need to be aware that you need to make sure to add a domain that is not taken already. otherwise it will throw an exception.

Chefs are created in a different endpoint, and they will be added automatically to the Restaurant record that it belongs to.


## Update a Restaurant 

> PUT - https://node.chefsurf.io/api/restaurants/restaurant_id

```javascript
import {
  HttpClient
} from '@angular/common/http';

const path = 'https://node.chefsurf.io/api/restaurants';

constructor(private http: HttpClient) {
}

updateRestaurant(restaurant_id, params) {
  return this.http.put(`${path}/${restaurant_id}`, params, {
    headers: {
      Authorization: `JWT ${jwt_token}`
    }
  });
}
```

> Sample Data ( you can send the params you want to be updated in your request )

```json
{
  
  "name": "New restaurant - updated",
  "domain": "newrestaurant.app"  
}
```

> The above command returns JSON structured like this:

```json
{
    "data": {
        "chefs": [],
        "logo": null,
        "background": null,
        "name": "New restaurant - updated",
        "automatedKitchen": false,
        "deliveryAvailable": true,
        "pickUpAvailable": false,
        "cashPaymentAvailable": true,
        "creditCardPaymentAvailable": true,
        "_id": "5e0ec1eb8fbe5c18ac3f72e3",
        "deleted": false,
        "domain": "newrestaurant.app",
        "owner": "5dd9790112256f10e83bb932",
        "user": "5dd9790212256f10e83bb937",
        "updatedAt": "2020-01-03T10:20:00.972Z",
        "createdAt": "2020-01-03T04:24:11.972Z",
        "__v": 0
    }
}
```

This endpoint allows you to modify the restaurant, not a lot of the properties can be modified and there are formats that must be followed otherwise it will throw an error.

### HTTP Request

`PUT - https://node.chefsurf.io/api/restaurants/restaurant_id`

### Fillable properties

Parameter | Type   | Description |
--------- | ------ | ----------- |
logo       | String   | You can modify the logo url.
background | String   | You can modify the background url.
location   | Object   | You can add a Google location which includes the address, coordinates, etc.
name       | String   | You can change the name of the restaurant that is visible to the customers.
automatedKitchen | Boolean  | Enable/Disable the automatedKitchen feature ( OpenKitchen )
deliveryAvailable | Boolean | Enable/Disable delivery to address feature
cashPaymentAvailable | Boolean | Enable/Disable cash payments feature
creditCardPaymentAvailable | Boolean | Enable/Disable credit card payments feature

### Non fillable

Parameter | Type | Description
--------- | ---- | ------------
_id       | ObjectID | Primary key
chefs     | Array  | Array of Chef Objects.
owner     | ObjectID | Ower Object ID
user      | ObjectID | User Object ID
updatedAt | DateTime | Update timestamps - auto generated.
createdAt | DateTime | Create timestamps - auto generated.

## Delete Restaurant 


> DELETE - https://node.chefsurf.io/api/restaurants/restaurant_id

```javascript
import {
  HttpClient
} from '@angular/common/http';

const path = 'https://node.chefsurf.io/api/restaurants';

constructor(private http: HttpClient) {
}

/**
 * @param {String} restaurant_id
*/
deleteRestaurant(restaurant_id) {
  return this.http.delete(`${path}/${restaurant_id}`, {
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
        "chefs": [],
        "logo": null,
        "background": null,
        "name": "New restaurant",
        "automatedKitchen": false,
        "deliveryAvailable": true,
        "pickUpAvailable": false,
        "cashPaymentAvailable": true,
        "creditCardPaymentAvailable": true,
        "deleted": true,
        "_id": "5e0ec1eb8fbe5c18ac3f72e3",
        "domain": "newrestaurant.app",
        "owner": "5dd9790112256f10e83bb932",
        "user": "5dd9790212256f10e83bb937",
        "updatedAt": "2020-01-03T06:24:06.699Z",
        "createdAt": "2020-01-03T04:24:11.972Z",
        "__v": 0,
        "deletedAt": "2020-01-03T06:24:06.698Z"
    }
}
```

> If you are trying to delete a restaurant that it has been deleted, you will get an exception: 404.

```json
{
    "code": "NotFound",
    "message": "Record not found."
}
```

This endpoint deletes a specific restaurant.

### HTTP Request

`DELETE - https://node.chefsurf.io/api/restaurants/restaurant_id`


