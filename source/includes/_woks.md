# Woks

## Get Woks

```javascript
import {
  HttpClient
} from '@angular/common/http';

const path = 'https://node.chefsurf.io/api/open-kitchen/woks';

constructor(private http: HttpClient) {
}

requestWoks(params) {
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
            "status": "available",
            "notes": " ",
            "currentDish": null,
            "deleted": false,
            "_id": "5dd9790412256f10e83bb9c2",
            "restaurant": "5dd9790212256f10e83bb934",
            "owner": "5dd9790112256f10e83bb932",
            "identifier": "XsUbu9o",
            "label": "wok_0",
            "updatedAt": "2019-11-23T18:23:00.123Z",
            "createdAt": "2019-11-23T18:23:00.123Z",
            "__v": 0
        },
        {
            "status": "available",
            "notes": " ",
            "currentDish": null,
            "deleted": false,
            "_id": "5dd9790412256f10e83bb9c3",
            "restaurant": "5dd9790212256f10e83bb934",
            "owner": "5dd9790112256f10e83bb932",
            "identifier": "Lkmx5V1",
            "label": "wok_1",
            "updatedAt": "2019-11-23T18:23:00.124Z",
            "createdAt": "2019-11-23T18:23:00.124Z",
            "__v": 0
        },
        ...
    ]
}
```

This endpoint retrieves a list of woks in the restaurant. The Raspberry pi needs this list to know which woks are working and identify them by it's status.

### HTTP Request

`GET https://node.chefsurf.io/api/open-kitchen/woks`

### URL Parameters

Parameter | Description |
--------- | ----------- |
where_status | apply a status condition to the query. i.e <strong>available</strong>
where_label | apply a label condition to the query i.e <strong>wok_1</strong>
where_currentDish | apply a currentDish condition to the query i.e <strong>5dd9790212256f10e77ab521</strong>. 

## Get a Wok

> GET - https://node.chefsurf.io/open-kitchen/woks/:wok_id

```javascript
import {
  HttpClient
} from '@angular/common/http';

const path = 'https://node.chefsurf.io/api/open-kitchen/woks';

constructor(private http: HttpClient) {
}

requestWok(wok_id, params) {
  return this.http.get(`${path}/${wok_id}`, {
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
        "status": "available",
        "notes": " ",
        "currentDish": null,
        "deleted": false,
        "_id": "5dd9790412256f10e83bb9c3",
        "restaurant": "5dd9790212256f10e83bb934",
        "owner": "5dd9790112256f10e83bb932",
        "identifier": "Lkmx5V1",
        "label": "wok_1",
        "updatedAt": "2019-11-23T18:23:00.124Z",
        "createdAt": "2019-11-23T18:23:00.124Z",
        "__v": 0
    }
}
```

This endpoint retrieves one wok by the ID.

### HTTP Request

`GET https://node.chefsurf.io/open-kitchen/woks/:wok_id`

<!-- ### URL Parameters -->
<!-- 
Parameter | Description
--------- | -----------
ID | The ID of the kitten to delete
 -->


## Update wok 

> PUT - https://node.chefsurf.io/api/open-kitchen/woks/wok_id

```javascript
import {
  HttpClient
} from '@angular/common/http';

const path = 'https://node.chefsurf.io/api/open-kitchen/woks';

constructor(private http: HttpClient) {
}

updateWok(wok_id, params) {
  return this.http.put(`${path}/${wok_id}`, params, {
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
        "status": "available",
        "notes": " ",
        "currentDish": null,
        "deleted": false,
        "_id": "5dd9790412256f10e83bb9c3",
        "restaurant": "5dd9790212256f10e83bb934",
        "owner": "5dd9790112256f10e83bb932",
        "identifier": "Lkmx5V1",
        "label": "wok_1_updated",
        "updatedAt": "2019-11-23T18:23:00.124Z",
        "createdAt": "2019-11-23T18:23:00.124Z",
        "__v": 0
    }
}
```
This endpoint allows you to modify the wok in place, not a lot of the properties can be modified and there are formats that must be followed otherwise it will throw an error.

### HTTP Request

`PUT - https://node.chefsurf.io/api/open-kitchen/woks/wok_id`

### Fillable properties

Parameter | Type   | Description |
--------- | ------ | ----------- |
status      | String   | You can modify the status of the wok to make them available or busy(cooking).
notes       | String   | You can add/update notes for this specific wok.
currentDish | ObjectId | Assign a QueueDish so everyone knows which dish will be cooked on the wok.
identifier  | String   | it's an ID that will map the wok to the one connected in the restaurant.
label       | String   | this is a human friendly label to identify the wok.

## Delete wok 


> DELETE - https://node.chefsurf.io/api/open-kitchen/woks/wok_id

```javascript
import {
  HttpClient
} from '@angular/common/http';

const path = 'https://node.chefsurf.io/api/open-kitchen/woks';

constructor(private http: HttpClient) {
}

/**
 * @param {Object} wok_id
*/
deleteWok(wok_id) {
  return this.http.delete(`${path}/${wok_id}`, {
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
        "status": "available",
        "notes": " ",
        "currentDish": null,
        "deleted": false,
        "_id": "5dd9790412256f10e83bb9c3",
        "restaurant": "5dd9790212256f10e83bb934",
        "owner": "5dd9790112256f10e83bb932",
        "identifier": "Lkmx5V1",
        "label": "wok_1_updated",
        "updatedAt": "2019-11-23T18:23:00.124Z",
        "createdAt": "2019-11-23T18:23:00.124Z",
        "__v": 0,
        "deleted": true,
        "deletedAt": "2020-01-01T23:11:18.702Z"
    }
}
```

> If you are trying to delete a wok that it has been deleted, you will get an exception: 404.

```json
{
    "code": "NotFound",
    "message": "Record not found."
}
```

This endpoint deletes a specific wok.

### HTTP Request

`DELETE - https://node.chefsurf.io/api/open-kitchen/woks/wok_id`


