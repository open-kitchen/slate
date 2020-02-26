# Inventories

## Get Inventories

```javascript
import {
  HttpClient
} from '@angular/common/http';

const path = 'https://node.chefsurf.io/api/inventories';

constructor(private http: HttpClient) {
}

requestInventories(params) {
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
            "maxCapacity": 10,
            "sendAlertsOnLowInventory": false,
            "alertOnQuantity": 1,
            "current": false,
            "deleted": false,
            "_id": "5dd9790312256f10e83bb93f",
            "restaurant": "5dd9790212256f10e83bb934",
            "owner": "5dd9790112256f10e83bb932",
            "updatedAt": "2019-11-23T18:22:59.213Z",
            "createdAt": "2019-11-23T18:22:59.213Z",
            "__v": 0
        }
    ]
}
```

This endpoint retrieves a list of inventories that the staff / chef can see under the same ownership.

### HTTP Request

`GET https://node.chefsurf.io/api/inventories`

### URL Parameters

Parameter | Description |
--------- | ----------- |
where_restaurant | apply a restaurant condition to the query. i.e <strong>5dd9790212256f10e83bb934</strong>
where_current | apply a current condition to the query i.e <strong>true</strong>

## Get Inventory

> GET - https://node.chefsurf.io/open-kitchen/inventories/:inventory_id

```javascript
import {
  HttpClient
} from '@angular/common/http';

const path = 'https://node.chefsurf.io/api/inventories';

constructor(private http: HttpClient) {
}

requestInventory(inventory_id, params) {
  return this.http.get(`${path}/${inventory_id}`, {
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
        "maxCapacity": 10,
        "sendAlertsOnLowInventory": false,
        "alertOnQuantity": 1,
        "current": false,
        "deleted": false,
        "_id": "5dd9790312256f10e83bb93f",
        "restaurant": "5dd9790212256f10e83bb934",
        "owner": "5dd9790112256f10e83bb932",
        "updatedAt": "2019-11-23T18:22:59.213Z",
        "createdAt": "2019-11-23T18:22:59.213Z",
        "__v": 0
    }
}
```

This endpoint retrieves one inventory by the ID.

### HTTP Request

`GET https://node.chefsurf.io/open-kitchen/inventories/:inventory_id`

<!-- ### URL Parameters -->
<!-- 
Parameter | Description
--------- | -----------
ID | The ID of the kitten to delete
 -->

## Create Inventory

> POST = https://node.chefsurf.io/api/inventories

```javascript
  import {
  HttpClient
} from '@angular/common/http';

const path = 'https://node.chefsurf.io/api/inventories';

constructor(private http: HttpClient) {
}

createInventory(data) {
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
        "maxCapacity": 10,
        "sendAlertsOnLowInventory": false,
        "alertOnQuantity": 1,
        "current": false,
        "deleted": false,
        "_id": "5dd9790312256f10e83bb93f",
        "restaurant": "5dd9790212256f10e83bb934",
        "owner": "5dd9790112256f10e83bb932",
        "updatedAt": "2019-11-23T18:22:59.213Z",
        "createdAt": "2019-11-23T18:22:59.213Z",
        "__v": 0
    }
}
```

> If you try to create a second inventory you will get a JSON like this:

```json

```

This endpoint allows you to create a new inventory. if you create a new inventory you need to be aware that you need to make sure you don't have one already. otherwise it will throw an exception.

## Update Inventory 

> PUT - https://node.chefsurf.io/api/inventories/inventory_id

```javascript
import {
  HttpClient
} from '@angular/common/http';

const path = 'https://node.chefsurf.io/api/inventories';

constructor(private http: HttpClient) {
}

updateWok(inventory_id, params) {
  return this.http.put(`${path}/${inventory_id}`, params, {
    headers: {
      Authorization: `JWT ${jwt_token}`
    }
  });
}
```

> Sample Data ( you can send the params you want to be updated in your request )

```json
{  
  "maxCapacity": 20,
  "sendAlertsOnLowInventory": true
}
```

> The above command returns JSON structured like this:

```json
{
    "data": {
        "maxCapacity": 20,
        "sendAlertsOnLowInventory": true,
        "alertOnQuantity": 1,
        "current": false,
        "deleted": false,
        "_id": "5dd9790312256f10e83bb93f",
        "restaurant": "5dd9790212256f10e83bb934",
        "owner": "5dd9790112256f10e83bb932",
        "updatedAt": "2020-01-05T03:26:51.972Z",
        "createdAt": "2019-11-23T18:22:59.213Z",
        "__v": 0
    }
}
```

This endpoint allows you to modify the inventory, not a lot of the properties can be modified and there are formats that must be followed otherwise it will throw an error.

### HTTP Request

`PUT - https://node.chefsurf.io/api/inventories/inventory_id`

### Fillable properties

Parameter | Type   | Description |
--------- | ------ | ----------- |
maxCapacity | Number | it determinates the maximum quantity inside an inventory item.
sendAlertsOnLowInventory | Boolean | it determinates if we need to notify the staff about low quantities in the inventory item records.
alertOnQuantity | Number | it determinates the number to check if the sendAlertsOnLowInventory is enabled.
current | Boolean | it determinates if the inventory created is the current one ( at this point it's not being used).

### Non fillable

Parameter | Type | Description
--------- | ---- | ------------
_id       | ObjectID | Primary key
restaurant| Array    | Restaurant Object ID
owner     | ObjectID | Ower Object ID
updatedAt | DateTime | Update timestamps - auto generated.
createdAt | DateTime | Create timestamps - auto generated.

## Delete Inventory 

> DELETE - https://node.chefsurf.io/api/inventories/inventory_id

```javascript
import {
  HttpClient
} from '@angular/common/http';

const path = 'https://node.chefsurf.io/api/inventories';

constructor(private http: HttpClient) {
}

/**
*/
deleteInventory(inventory_id) {
  return this.http.delete(`${path}/${inventory_id}`, {
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
        "maxCapacity": 20,
        "sendAlertsOnLowInventory": true,
        "alertOnQuantity": 1,
        "current": false,
        "deleted": true,
        "_id": "5dd9790312256f10e83bb93f",
        "restaurant": "5dd9790212256f10e83bb934",
        "owner": "5dd9790112256f10e83bb932",
        "updatedAt": "2020-01-05T03:33:43.983Z",
        "createdAt": "2019-11-23T18:22:59.213Z",
        "__v": 0,
        "deletedAt": "2020-01-05T03:33:43.979Z"
    }
}
```

> If you are trying to delete a inventory that it has been deleted, you will get an exception: 404.

```json
{
    "code": "NotFound",
    "message": "Record not found."
}
```

This endpoint deletes a specific inventory.

### HTTP Request

`DELETE - https://node.chefsurf.io/api/inventories/inventory_id`


