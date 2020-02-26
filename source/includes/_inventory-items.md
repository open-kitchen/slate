# InventoryItems

## Get Inventory Items

```javascript
import {
  HttpClient
} from '@angular/common/http';

const path = 'https://node.chefsurf.io/api/inventory-items';

constructor(private http: HttpClient) {
}

requestInventoryItems(params) {
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
            "category": "ingredient",
            "type": "none",
            "description": null,
            "onStock": false,
            "stockQuantity": 200,
            "onProduction": false,
            "productionQuantity": 15,
            "referenceId": "arugula",
            "maxProductionCapacity": 1,
            "price": 0,
            "measurement": "none",
            "measurementUnit": null,
            "totalMeasurement": "none",
            "totalMeasurementUnits": null,
            "priceForRawItem": 0,
            "pictures": [
                "5dd9790312256f10e83bb940"
            ],
            "deleted": false,
            "_id": "5dd9790312256f10e83bb941",
            "owner": "5dd9790112256f10e83bb932",
            "restaurant": "5dd9790212256f10e83bb934",
            "inventory": "5dd9790312256f10e83bb93f",
            "title": "Organic arugula",
            "updatedAt": "2019-11-23T18:22:59.215Z",
            "createdAt": "2019-11-23T18:22:59.215Z",
            "__v": 0
        },
        ...
    ]
}
```

This endpoint retrieves a list of inventory Items that the staff / chef can see under the same ownership.

### HTTP Request

`GET https://node.chefsurf.io/api/inventory-items`

### URL Parameters

Parameter | Description |
--------- | ----------- |
where_category | apply a category condition to the query. i.e <strong>ingredient</strong>
where_type | apply a type condition to the query i.e <strong>protein</strong>

## Get a Inventory Item

> GET - https://node.chefsurf.io/open-kitchen/inventory-items/:item_id

```javascript
import {
  HttpClient
} from '@angular/common/http';

const path = 'https://node.chefsurf.io/api/inventory-items';

constructor(private http: HttpClient) {
}

requestInventoryItem(item_id, params) {
  return this.http.get(`${path}/${item_id}`, {
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
        "category": "ingredient",
        "type": "none",
        "description": null,
        "onStock": false,
        "stockQuantity": 200,
        "onProduction": false,
        "productionQuantity": 15,
        "referenceId": "arugula",
        "maxProductionCapacity": 1,
        "price": 0,
        "measurement": "none",
        "measurementUnit": null,
        "totalMeasurement": "none",
        "totalMeasurementUnits": null,
        "priceForRawItem": 0,
        "pictures": [
            "5dd9790312256f10e83bb940"
        ],
        "deleted": false,
        "_id": "5dd9790312256f10e83bb941",
        "owner": "5dd9790112256f10e83bb932",
        "restaurant": "5dd9790212256f10e83bb934",
        "inventory": "5dd9790312256f10e83bb93f",
        "title": "Organic arugula",
        "updatedAt": "2019-11-23T18:22:59.215Z",
        "createdAt": "2019-11-23T18:22:59.215Z",
        "__v": 0
    }
}
```

This endpoint retrieves one inventory item by the ID.

### HTTP Request

`GET https://node.chefsurf.io/open-kitchen/inventory-items/:item_id`

<!-- ### URL Parameters -->
<!-- 
Parameter | Description
--------- | -----------
ID | The ID of the kitten to delete
 -->

## Create Inventory Item

> POST = https://node.chefsurf.io/api/inventory-items

```javascript
  import {
  HttpClient
} from '@angular/common/http';

const path = 'https://node.chefsurf.io/api/inventory-items';

constructor(private http: HttpClient) {
}

createInventoryItem(data) {
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
        "category": "ingredient",
        "type": "none",
        "description": null,
        "onStock": false,
        "stockQuantity": 200,
        "onProduction": false,
        "productionQuantity": 15,
        "referenceId": "new_ing1",
        "maxProductionCapacity": 1,
        "price": 0,
        "measurement": "none",
        "measurementUnit": null,
        "totalMeasurement": "none",
        "totalMeasurementUnits": null,
        "priceForRawItem": 0,
        "pictures": [],
        "_id": "5e117fb6fa6f3a02580f84cc",
        "deleted": false,
        "inventory": "5dd9790312256f10e83bb93f",
        "title": "new inventory item",
        "owner": "5dd9790112256f10e83bb932",
        "restaurant": "5dd9790212256f10e83bb934",
        "updatedAt": "2020-01-05T06:18:30.418Z",
        "createdAt": "2020-01-05T06:18:30.418Z",
        "__v": 0
    }
}
```

This endpoint allows you to create a new inventory Item. if you create a new inventoryItem you need to be aware that you need to make sure to add a referenceId that is not already taken. otherwise it will throw an exception.


## Update Inventory Item 

> PUT - https://node.chefsurf.io/api/inventory-items/item_id

```javascript
import {
  HttpClient
} from '@angular/common/http';

const path = 'https://node.chefsurf.io/api/inventory-items';

constructor(private http: HttpClient) {
}

updateInventoryItem(item_id, params) {
  return this.http.put(`${path}/${item_id}`, params, {
    headers: {
      Authorization: `JWT ${jwt_token}`
    }
  });
}
```

> Sample Data ( you can send the params you want to be updated in your request )

```json
{
  "title": "Lettuce",
  "referenceId": "lettuce_refid"  
}
```

> The above command returns JSON structured like this:

```json
{
    "data": {
        "category": "ingredient",
        "type": "none",
        "description": null,
        "onStock": false,
        "stockQuantity": 200,
        "onProduction": false,
        "productionQuantity": 15,
        "referenceId": "lettuce_refid",
        "maxProductionCapacity": 1,
        "price": 0,
        "measurement": "none",
        "measurementUnit": null,
        "totalMeasurement": "none",
        "totalMeasurementUnits": null,
        "priceForRawItem": 0,
        "pictures": [],
        "deleted": false,
        "_id": "5e117fb6fa6f3a02580f84cc",
        "inventory": "5dd9790312256f10e83bb93f",
        "title": "Lettuce",
        "owner": "5dd9790112256f10e83bb932",
        "restaurant": "5dd9790212256f10e83bb934",
        "updatedAt": "2020-01-05T06:28:04.065Z",
        "createdAt": "2020-01-05T06:18:30.418Z",
        "__v": 0
    }
}
```

This endpoint allows you to modify the inventory Item, not a lot of the properties can be modified and there are formats that must be followed otherwise it will throw an error.

### HTTP Request

`PUT - https://node.chefsurf.io/api/inventory-items/item_id`

### Fillable properties

Parameter | Type   | Description |
--------- | ------ | ----------- |
category | String | You can modify the category to any of these values ['ingredient', 'drink', 'dessert'].
type | String | You can modify the type to any of these values ['base', 'veggie', 'dressing', 'protein', 'extra', 'drink', 'dessert', 'topping', 'premium', 'none'].
title | String | You can modify the title.
description | String | You can modify the description.
onStock | Boolean | You can Enable/Disable the inventory item to be in stock.
stockQuantity | Number | You can modify the actual quantity in stock.
onProduction | Boolean | You can Enable/Disable the inventory item to be in production.
productionQuantity | Number | You can modify the quantity that is in production.
maxProductionCapacity | Number | You can modify the max production capacity (it cannot be lower than the actual production quantity).
referenceId | String | You can modify the referenceId (this value has to be unique)
price | Number | You can modify the price of the inventory item.
measurement | String | You can modify the measurement of the inventory item to any of these values ['gram', 'kilogram', 'oz', 'piece', 'none'].
measurementUnit | Number | You can modify the quantity of the measurement set for the inventory item.
totalMeasurement | String | You can modify the total measurement of the inventory item to any of these values ['gram', 'kilogram', 'oz', 'piece', 'none']
totalMeasurementUnits | Number | You can modify the quantity of the total measurement set for the inventory item.
priceForRawItem | Number | You can set the price of the raw item ( cost )
pictures | Array | Array of Attachment Objects

### Non fillable

Parameter | Type | Description
--------- | ---- | ------------
_id       | ObjectID | Primary key
restaurant| ObjectID | Restaurant Object ID
owner     | ObjectID | Ower Object ID
inventory | ObjectID | Inventory Object ID
updatedAt | DateTime | Update timestamps - auto generated.
createdAt | DateTime | Create timestamps - auto generated.

## Delete Inventory Item 


> DELETE - https://node.chefsurf.io/api/inventory-items/item_id

```javascript
import {
  HttpClient
} from '@angular/common/http';

const path = 'https://node.chefsurf.io/api/inventory-items';

constructor(private http: HttpClient) {
}

/**
 * @param {string} item_id
*/
deleteInventoryItem(item_id) {
  return this.http.delete(`${path}/${item_id}`, {
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
        "category": "ingredient",
        "type": "none",
        "description": null,
        "onStock": false,
        "stockQuantity": 0,
        "onProduction": false,
        "productionQuantity": 0,
        "referenceId": "lettuce_refid",
        "maxProductionCapacity": 1,
        "price": 499,
        "measurement": "none",
        "measurementUnit": null,
        "totalMeasurement": "none",
        "totalMeasurementUnits": null,
        "priceForRawItem": 0,
        "pictures": [],
        "deleted": true,
        "_id": "5e118bbf11a8820b7ea66ef8",
        "owner": "5dd9790112256f10e83bb932",
        "restaurant": "5dd9790212256f10e83bb934",
        "inventory": "5dd9790312256f10e83bb93f",
        "title": "Lettuce",
        "updatedAt": "2020-01-05T07:10:25.099Z",
        "createdAt": "2020-01-05T07:09:51.415Z",
        "__v": 0,
        "deletedAt": "2020-01-05T07:10:25.097Z"
    }
}
```

> If you are trying to delete a inventoryItem that it has been deleted, you will get an exception: 404.

```json
{
    "code": "NotFound",
    "message": "Record not found."
}
```

This endpoint deletes a specific inventoryItem.

### HTTP Request

`DELETE - https://node.chefsurf.io/api/inventory-items/item_id`


