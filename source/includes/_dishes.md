# Dishes

## Get Dishes

```javascript
import {
  HttpClient
} from '@angular/common/http';

const path = 'https://node.chefsurf.io/api/open-kitchen/dishes';

constructor(private http: HttpClient) {
}

requestQueueDishes(params) {
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
            "ingredients": {
                "pending": [
                    {
                        "ingredientId": "5dd9840a64bebe12632fb79c",
                        "type": "protein",
                        "identifier": "protein",
                        "title": "Proteinas",
                        "options": [],
                        "total": 0
                    },
                    ...
                ],
                "added": [
                    ...
                ],
                "failed": [],
                "additions": []
            },
            "dishName": "Elote Bowl",
            "priority": "normal",
            "status": "queue",
            "sortOrder": 0,
            "simplifiedId": "8d16-8d17",
            "cookingTime": 2,
            "deleted": false,
            "_id": "5e067f54056e410a8e2f2746",
            "orderItem": "5e067e7575f5160a6fcb8d17",
            "customer": "5dfc657506b7c674c1fbf0de",
            "restaurant": "5dd9790212256f10e83bb934",
            "owner": "5dd9790112256f10e83bb932",
            "updatedAt": "2019-12-29T19:59:17.260Z",
            "createdAt": "2019-12-27T22:01:56.797Z",
            "__v": 0
        },
        ...
    ]
}
```

This endpoint retrieves a list of dishes that inside the queue. The Raspberry pi needs this list to know which dishes are in which line so we can assign them to woks and start collecting ingredients from dispensers if needed. all those steps are based on the information provided inside ingredients./ and we update the status of each dish when we move them from one state to another.


### HTTP Request

`GET https://node.chefsurf.io/api/open-kitchen/dishes`

### URL Parameters

Parameter | Description |
--------- | ----------- |
where_status | apply a status condition to the query. i.e <strong>queue</strong>
wherein_status | apply a list of statuses condition to the query i.e <strong>['failed', 'cancelled']
where_priority | apply a priority condition to the query i.e <strong>urgent</strong>
where_cookingTime | apply a cooking time condition to the query i.e <strong>2</strong>. 


## Get Dish 

> GET - https://node.chefsurf.io/open-kitchen/dishes/:queue_dish_id

```javascript
import {
  HttpClient
} from '@angular/common/http';

const path = 'https://node.chefsurf.io/api/open-kitchen/dishes';

constructor(private http: HttpClient) {
}

requestQueueDish(queue_dish_id, params) {
  return this.http.get(`${path}/${queue_dish_id}`, {
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
        "ingredients": {
            "pending": [
                {
                    "ingredientId": "5dd9797f12256f10e83bb9c9",
                    "type": "base",
                    "identifier": "base",
                    "title": "Bases",
                    "options": [
                        {
                            "optionId": "5dd9797f12256f10e83bb9cd",
                            "title": "Warm Quinoa",
                            "mandatory": false,
                            "quantity": 1,
                            "price": 0,
                            "total": 0,
                            "inventoryItem": "5dd9790312256f10e83bb949"
                        },
                        {
                            "optionId": "5dd9797f12256f10e83bb9cc",
                            "title": "Organic arugula",
                            "mandatory": false,
                            "quantity": 1,
                            "price": 0,
                            "total": 0,
                            "inventoryItem": "5dd9790312256f10e83bb941"
                        },
                        {
                            "optionId": "5dd9797f12256f10e83bb9cb",
                            "title": "Shredded Kale",
                            "mandatory": false,
                            "quantity": 1,
                            "price": 0,
                            "total": 0,
                            "inventoryItem": "5dd9790312256f10e83bb947"
                        },
                        {
                            "optionId": "5dd9797f12256f10e83bb9ca",
                            "title": "Organic Wild Rice",
                            "mandatory": false,
                            "quantity": 1,
                            "price": 0,
                            "total": 0,
                            "inventoryItem": "5dd9790312256f10e83bb945"
                        }
                    ],
                    "total": 0
                },
                ...
            ],
            "added": [...],
            "failed": [...],
            "additions": [...]
        },
        "dishName": "Elote Bowl",
        "priority": "normal",
        "status": "queue",
        "sortOrder": 0,
        "simplifiedId": "8d16-8d17",
        "cookingTime": 2,
        "deleted": false,
        "_id": "5e067f54056e410a8e2f2746",
        "orderItem": "5e067e7575f5160a6fcb8d17",
        "customer": "5dfc657506b7c674c1fbf0de",
        "restaurant": "5dd9790212256f10e83bb934",
        "owner": "5dd9790112256f10e83bb932",
        "updatedAt": "2019-12-29T19:59:17.260Z",
        "createdAt": "2019-12-27T22:01:56.797Z",
        "__v": 0
    }
}
```

This endpoint retrieves one queue dish by the ID.

### HTTP Request

`GET https://node.chefsurf.io/open-kitchen/dishes/:queue_dish_id`

<!-- ### URL Parameters -->
<!-- 
Parameter | Description
--------- | -----------
ID | The ID of the kitten to delete
 -->


## Update Dish 

> PUT - https://node.chefsurf.io/api/open-kitchen/dishes/queue_dish_id

```javascript
import {
  HttpClient
} from '@angular/common/http';

const path = 'https://node.chefsurf.io/api/open-kitchen/dishes';

constructor(private http: HttpClient) {
}

updateQueueDish(queue_dish_id, params) {
  return this.http.put(`${path}/${queue_dish_id}`, params, {
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
        "ingredients": {
            "pending": [
                {
                    "ingredientId": "5dd9797f12256f10e83bb9c9",
                    "type": "base",
                    "identifier": "base",
                    "title": "Bases",
                    "options": [
                        {
                            "optionId": "5dd9797f12256f10e83bb9cd",
                            "title": "Warm Quinoa",
                            "mandatory": false,
                            "quantity": 1,
                            "price": 0,
                            "total": 0,
                            "inventoryItem": "5dd9790312256f10e83bb949"
                        },
                        ...
                    ],
                    "total": 0
                },
                ...
            ],
            "added": [...],
            "failed": [...],
            "additions": [...]
        },
        "dishName": "Elote Bowl",
        "priority": "normal",
        "status": "queue",
        "sortOrder": 2,
        "simplifiedId": "8d16-8d17",
        "cookingTime": 2,
        "deleted": false,
        "_id": "5e067f54056e410a8e2f2746",
        "orderItem": "5e067e7575f5160a6fcb8d17",
        "customer": "5dfc657506b7c674c1fbf0de",
        "restaurant": "5dd9790212256f10e83bb934",
        "owner": "5dd9790112256f10e83bb932",
        "updatedAt": "2020-01-01T22:19:14.257Z",
        "createdAt": "2019-12-27T22:01:56.797Z",
        "__v": 0
    }
}
```
This endpoint allows you to modify the queue dish in place, not a lot of the properties can be modified and there are formats that must be followed otherwise it will throw an error.

### HTTP Request

`PUT - https://node.chefsurf.io/api/open-kitchen/dishes/queue_dish_id`

### Fillable properties

Parameter | Type  | Description |
--------- | ----- | ----------- |
simplifiedId | String   |  it's an ID that gets the last 4 digits of the order + last 4 digits of the order item + number of the dish ( in case if the quantity is greater than 1)
dishName     | String   | it's the name of the dish added to the order
orderItem    | ObjectId | it's the primary key of the orderItem
priority     | String   | it identifies the level of the dish [low, normal, urgent]
ingredients  | Object   | it's an object that contains 4 arrays [pending, added, failed, additions] ( we will explain them in detail in the model documentation)
status       | String   | it's a representation of the current state of the dish which changes between these values [queue, cooking, packing, finished, failed, cancelled, on_review]
sortOrder    | Number   | it's a helper to sort them manually inside the application when we drag and drop them inside the board.
logs         | Object   | it's an Object 
cookingTime  | Number   | it's a representation of the cooking time in minutes, to know how long the dish will be in the wok.


## Delete Dish 


> DELETE - https://node.chefsurf.io/api/open-kitchen/dishes/queue_dish_id

```javascript
import {
  HttpClient
} from '@angular/common/http';

const path = 'https://node.chefsurf.io/api/open-kitchen/dishes';

constructor(private http: HttpClient) {
}
/**
 * @param {string} queue_dish_id 
*/
deleteQueueDish(queue_dish_id) {
  return this.http.delete(`${path}/${queue_dish_id}`, {
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
        "ingredients": {
            ...
        },
        "dishName": "Elote Bowl",
        "priority": "normal",
        "status": "queue",
        "sortOrder": 4,
        "simplifiedId": "8d16-8d17",
        "cookingTime": 2,
        "deleted": true,
        "_id": "5e067f54056e410a8e2f2746",
        "orderItem": "5e067e7575f5160a6fcb8d17",
        "customer": "5dfc657506b7c674c1fbf0de",
        "restaurant": "5dd9790212256f10e83bb934",
        "owner": "5dd9790112256f10e83bb932",
        "updatedAt": "2020-01-01T23:11:18.702Z",
        "createdAt": "2019-12-27T22:01:56.797Z",
        "__v": 0,
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

This endpoint deletes a specific queue dish.

### HTTP Request

`DELETE - https://node.chefsurf.io/api/open-kitchen/dishes/queue_dish_id`


