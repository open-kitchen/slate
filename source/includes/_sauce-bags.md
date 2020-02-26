# Sauce Bags

## Get Sauce Bags

```javascript
import {
  HttpClient
} from '@angular/common/http';

const path = 'https://node.chefsurf.io/api/open-kitchen/sauce-bags';

constructor(private http: HttpClient) {
}

requestSauceBags(params) {
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
            "capacity": 0,
            "currentLoad": null,
            "active": false,
            "notes": "",
            "deleted": false,
            "_id": "5e118e9c11a8820b7ea66efa",
            "inventoryItem": "5dd9790312256f10e83bb93f",
            "label": "Teriyaki Sauce",
            "identifier": "sg_teri_sauce",
            "restaurant": "5dd9790212256f10e83bb934",
            "owner": "5dd9790112256f10e83bb932",
            "updatedAt": "2020-01-05T07:28:11.412Z",
            "createdAt": "2020-01-05T07:22:04.868Z",
            "__v": 0
        },
        ...
    ]
}
```

This endpoint retrieves a list of sauce bags that the staff / chef can see under the same ownership.

### HTTP Request

`GET https://node.chefsurf.io/api/open-kitchen/sauce-bags`

### URL Parameters

Parameter | Description |
--------- | ----------- |
where_inventoryItem | apply a 'inventoryItem' condition to the query. i.e <strong>5dd9790312256f10e83bb93f</strong>
where_active | apply a 'active' condition to the query i.e <strong>true</strong>
where_identifier | apply a 'identifier' condition to the query i.e <strong>sg_001</strong>

## Get Sauce Bag

> GET - https://node.chefsurf.io/open-kitchen/sauce-bags/:sauce_bag_id

```javascript
import {
  HttpClient
} from '@angular/common/http';

const path = 'https://node.chefsurf.io/api/open-kitchen/sauce-bags';

constructor(private http: HttpClient) {
}

requestSauceBag(sauce_bag_id, params) {
  return this.http.get(`${path}/${sauce_bag_id}`, {
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
        "label": "Oil",
        "identifier": "sg_oil",
        "restaurant": "5dd9790212256f10e83bb934",
        "owner": "5dd9790112256f10e83bb932",
        "updatedAt": "2020-01-05T07:28:11.412Z",
        "createdAt": "2020-01-05T07:22:04.868Z",
        "__v": 0
    }
}
```

This endpoint retrieves one sauce bag by the ID.

### HTTP Request

`GET https://node.chefsurf.io/open-kitchen/sauce-bags/:sauce_bag_id`

<!-- ### URL Parameters -->
<!-- 
Parameter | Description
--------- | -----------
ID | The ID of the kitten to delete
 -->

## Create Sauce Bag

> POST = https://node.chefsurf.io/api/open-kitchen/sauce-bags

```javascript
  import {
  HttpClient
} from '@angular/common/http';

const path = 'https://node.chefsurf.io/api/open-kitchen/sauce-bags';

constructor(private http: HttpClient) {
}

createSauceBag(data) {
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
        "label": "Soy Sauce",
        "identifier": "sg_soys",
        "restaurant": "5dd9790212256f10e83bb934",
        "owner": "5dd9790112256f10e83bb932",
        "updatedAt": "2020-01-05T07:22:04.868Z",
        "createdAt": "2020-01-05T07:22:04.868Z",
        "__v": 0
    }
}
```

This endpoint allows you to create a new sauce bag. if you create a new sauge bag you need to be aware that you need to make sure to add an identifier that is not taken already. otherwise it will throw an exception.

## Update Sauce Bag 

> PUT - https://node.chefsurf.io/api/open-kitchen/sauce-bags/sauce_bag_id

```javascript
import {
  HttpClient
} from '@angular/common/http';

const path = 'https://node.chefsurf.io/api/open-kitchen/sauce-bags';

constructor(private http: HttpClient) {
}

updateSauceBag(sauce_bag_id, params) {
  return this.http.put(`${path}/${sauce_bag_id}`, params, {
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
  "capacity": 50,
  "notes": "This sauce bag sometimes releases more content than normal"
}
```

> The above command returns JSON structured like this:

```json
{
    "data": {
       "capacity": 50,
        "currentLoad": null,
        "active": false,
        "notes": "This sauce bag sometimes releases more content than normal",
        "_id": "5e118e9c11a8820b7ea66efa",
        "deleted": false,
        "inventoryItem": "5dd9790312256f10e83bb93f",
        "label": "Soy Sauce",
        "identifier": "sg_soys",
        "restaurant": "5dd9790212256f10e83bb934",
        "owner": "5dd9790112256f10e83bb932",
        "updatedAt": "2020-01-05T07:22:04.868Z",
        "createdAt": "2020-01-05T07:22:04.868Z",
        "__v": 0
    }
}
```

This endpoint allows you to modify the sauce bag, not all of the properties can be modified and there are formats that must be followed otherwise it will throw an error.

### HTTP Request

`PUT - https://node.chefsurf.io/api/open-kitchen/sauce-bags/sauce_bag_id`

### Fillable properties

Parameter | Type   | Description |
--------- | ------ | ----------- |
label     | String | You can modify the label (human friendly identifier)
identifier | String | You can modify the identifier ( it has to be unique )
inventoryItem | ObjectID | You can assign an InventoryItem to the sauce bag to track statistics.
capacity | Number | You can set the capacity the sauce bag has (maximum load)
currentLoad | Number | You can set the current load (so we can notify the staff about low quantities).
active | Boolean | You can Enable/Disable the sauce bag.
notes | String | You can add some notes to the sauce bag in case there are some special instructions.

### Non fillable

Parameter | Type | Description
--------- | ---- | ------------
_id       | ObjectID | Primary key
restaurant| ObjectID | Restaurant Object ID
owner     | ObjectID | Ower Object ID
updatedAt | DateTime | Update timestamps - auto generated.
createdAt | DateTime | Create timestamps - auto generated.

## Delete Sauce Bag 


> DELETE - https://node.chefsurf.io/api/open-kitchen/sauce-bags/sauce_bag_id

```javascript
import {
  HttpClient
} from '@angular/common/http';

const path = 'https://node.chefsurf.io/api/open-kitchen/sauce-bags';

constructor(private http: HttpClient) {
}

/**
 * @param {String} sauce_bag_id
*/
deleteSauceBag(sauce_bag_id) {
  return this.http.delete(`${path}/${sauce_bag_id}`, {
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
        "active": false,
        "notes": "This sauce bag sometimes releases more content than normal",
        "_id": "5e118e9c11a8820b7ea66efa",
        "deleted": false,
        "inventoryItem": "5dd9790312256f10e83bb93f",
        "label": "Soy Sauce",
        "identifier": "sg_soys",
        "restaurant": "5dd9790212256f10e83bb934",
        "owner": "5dd9790112256f10e83bb932",
        "updatedAt": "2020-01-05T07:22:04.868Z",
        "createdAt": "2020-01-05T07:22:04.868Z",
        "__v": 0,
        "deletedAt": "2020-01-05T07:30:56.096Z"
    }
}
```

> If you are trying to delete a sauce bag that it has been deleted, you will get an exception: 404.

```json
{
    "code": "NotFound",
    "message": "Record not found."
}
```

This endpoint deletes a specific sauce bag.

### HTTP Request

`DELETE - https://node.chefsurf.io/api/open-kitchen/sauce-bags/sauce_bag_id`


