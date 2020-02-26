# Dispensers

## Get Dispensers

```javascript
import {
  HttpClient
} from '@angular/common/http';

const path = 'https://node.chefsurf.io/api/open-kitchen/dispensers';

constructor(private http: HttpClient) {
}

requestDispensers(params) {
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
            "label": "Dispenser 001",
            "identifier": "disp001",
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

This endpoint retrieves a list of dispensers that the staff / chef can see under the same ownership.

### HTTP Request

`GET https://node.chefsurf.io/api/open-kitchen/dispensers`

### URL Parameters

Parameter | Description |
--------- | ----------- |
where_active | apply a 'active' condition to the query. i.e <strong>true</strong>
where_inventoryItem | apply a 'inventoryItem' condition to the query i.e <strong>5dd9790312256f10e83bb93f</strong>
where<_currentLoad | apply a 'currentLoad' condition to the query i.e <strong>10</strong>
where_identifier| apply a 'identifier' condition to the query i.e <strong>disp001</strong>

## Get a Dispenser

> GET - https://node.chefsurf.io/open-kitchen/dispensers/:dispenser_id

```javascript
import {
  HttpClient
} from '@angular/common/http';

const path = 'https://node.chefsurf.io/api/open-kitchen/dispensers';

constructor(private http: HttpClient) {
}

requestDispenser(dispenser_id, params) {
  return this.http.get(`${path}/${dispenser_id}`, {
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
        "label": "Dispenser A",
        "identifier": "disp1",
        "restaurant": "5dd9790212256f10e83bb934",
        "owner": "5dd9790112256f10e83bb932",
        "updatedAt": "2020-01-05T07:28:11.412Z",
        "createdAt": "2020-01-05T07:22:04.868Z",
        "__v": 0
    }
}
```

This endpoint retrieves one dispenser by the ID.

### HTTP Request

`GET https://node.chefsurf.io/open-kitchen/dispensers/:dispenser_id`

<!-- ### URL Parameters -->
<!-- 
Parameter | Description
--------- | -----------
ID | The ID of the kitten to delete
 -->

## Create a Dispenser

> POST = https://node.chefsurf.io/api/open-kitchen/dispensers

```javascript
  import {
  HttpClient
} from '@angular/common/http';

const path = 'https://node.chefsurf.io/api/open-kitchen/dispensers';

constructor(private http: HttpClient) {
}

createDispenser(data) {
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

This endpoint allows you to create a new dispenser. if you create a new dispenser you need to be aware that you need to make sure to add a identifier that is not taken already. otherwise it will throw an exception.


## Update a Dispenser 

> PUT - https://node.chefsurf.io/api/open-kitchen/dispensers/dispenser_id

```javascript
import {
  HttpClient
} from '@angular/common/http';

const path = 'https://node.chefsurf.io/api/open-kitchen/dispensers';

constructor(private http: HttpClient) {
}

updateDispenser(dispenser_id, params) {
  return this.http.put(`${path}/${dispenser_id}`, params, {
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

This endpoint allows you to modify the dispenser, not all of the properties can be modified and there are formats that must be followed otherwise it will throw an error.

### HTTP Request

`PUT - https://node.chefsurf.io/api/open-kitchen/dispensers/dispenser_id`

### Fillable properties

Parameter | Type   | Description |
--------- | ------ | ----------- |
label     | String | You can modify the label (human friendly identifier)
identifier | String | You can modify the identifier ( it has to be unique )
inventoryItem | ObjectID | You can assign an InventoryItem to the dispenser to track statistics.
capacity | Number | You can set the capacity the dispenser has (maximum load)
currentLoad | Number | You can set the current load (so we can notify the staff about low quantities).
active | Boolean | You can Enable/Disable the dispenser.
notes | String | You can add some notes to the dispenser in case there are some special instructions.

### Non fillable

Parameter | Type | Description
--------- | ---- | ------------
_id       | ObjectID | Primary key
restaurant| ObjectID | Restaurant Object ID
owner     | ObjectID | Ower Object ID
updatedAt | DateTime | Update timestamps - auto generated.
createdAt | DateTime | Create timestamps - auto generated.

## Delete Dispenser 


> DELETE - https://node.chefsurf.io/api/open-kitchen/dispensers/dispenser_id

```javascript
import {
  HttpClient
} from '@angular/common/http';

const path = 'https://node.chefsurf.io/api/open-kitchen/dispensers';

constructor(private http: HttpClient) {
}

/**
 * @param {String} dispenser_id
*/
deleteDispenser(dispenser_id) {
  return this.http.delete(`${path}/${dispenser_id}`, {
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

> If you are trying to delete a dispenser that it has been deleted, you will get an exception: 404.

```json
{
    "code": "NotFound",
    "message": "Record not found."
}
```

This endpoint deletes a specific dispenser.

### HTTP Request

`DELETE - https://node.chefsurf.io/api/open-kitchen/dispensers/dispenser_id`


