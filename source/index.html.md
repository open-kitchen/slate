---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - javascript (Angular)

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/lord/slate'>Documentation Powered by Slate</a>

includes:
  - queueDishes
  - errors

search: true
---

# Introduction

Welcome to the ChefSurf & OpenKitchen API. You can use our API documentation to access all our endpoints that are being used across the ChefSurf | Satee | OpenKitchen applications, which can get information on all the products, orders, dishes in the queue, etc.

At this point we will only write documentation for JavasCript and then we will add documentation for Python and PHP. You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

<!-- This example API documentation page was created with [Slate](https://github.com/lord/slate). Feel free to edit it and use it as a base for your own API's documentation. -->

# Authentication

> To authorize, use this code:

```javascript
import {
  HttpClient
} from '@angular/common/http';

const path = 'https://node.chefsurf.io';

constructor(private http: HttpClient) {
}

signIn(email: string, password: string) {
  return this.http.post(`${path}/api/auth/token`, {
    email,
    password
  });
}
```


> The above command returns JSON structured like this:

```json
{
    "token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJfaWQiOiI1ZGQ5NzkwMjEyMjU2ZjEwZTgzYmI5MzciLCJpZGVudGl0eSI6IjVkZDk3OTAyMTIyNTZmMTBlODNiYjkzNyIsInJvbGUiOiJjaGVmIiwib3duZXIiOiI1ZGQ5NzkwMTEyMjU2ZjEwZTgzYmI5MzIiLCJjbGllbnQiOm51bGwsIm93bmVyVHlwZSI6InJlc3RhdXJhbnQiLCJlbWFpbCI6ImNoZWYxQHNhdGVlLmRldiIsImNoZWYiOiI1ZGQ5NzkwMjEyMjU2ZjEwZTgzYmI5MzgiLCJyZXN0YXVyYW50IjoiNWRkOTc5MDIxMjI1NmYxMGU4M2JiOTM0IiwiaWF0IjoxNTc3NjU1OTU2fQ.pnCOJ6TfP3Xjll9znrEiEY458kwJqtylOtIsruKH5FA"
}
```

> Make sure to replace `{{token_here}}` with your API Token.

All the endpoints uses JWT tokens to allow access to the API. If you have a restaurant and you have access to the Satee Admin panel. you can obtain the token from inside the Web application [Satee Web Application](https://satee.com/admin).

Satee | Node ChefSurf | OpenKitchen expects for the API Token to be included in all API requests to the server in a header that looks like the following:

`Authorization: JWT {{token_here}}`

<aside class="notice">
You must replace <code>{{token_here}}</code> with your personal API Token.
</aside>

# First Open Kitchen endpoints

## Get Restaurant & Dependencies


> GET - https://node.chefsurf.io/open-kitchen

```javascript
import {
  HttpClient
} from '@angular/common/http';

const path = 'https://node.chefsurf.io';

constructor(private http: HttpClient) {
}

getDependencies(params) {
  return this.http.get(`${path}/api/open-kitchen`, {
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
    "restaurant": {
        "chefs": [
            "5dd9790212256f10e83bb936",
            "5dd9790212256f10e83bb938",
            "5dd9790212256f10e83bb93a",
            "5dd9790212256f10e83bb93c",
            "5dd9790312256f10e83bb93e"
        ],
        "logo": null,
        "background": null,
        "name": "Demo restaurant",
        "automatedKitchen": true,
        "deliveryAvailable": true,
        "pickUpAvailable": true,
        "cashPaymentAvailable": true,
        "creditCardPaymentAvailable": true,
        "_id": "5dd9790212256f10e83bb934",
        "domain": "restaurant.com",
        "owner": "5dd9790112256f10e83bb932",
        "user": "5dd9790112256f10e83bb933",
        "updatedAt": "2019-11-23T18:22:59.212Z",
        "createdAt": "2019-11-23T18:22:58.081Z",
        "__v": 1
    },
    "inventory": {
        "maxCapacity": 10,
        "sendAlertsOnLowInventory": false,
        "alertOnQuantity": 1,
        "_id": "5dd9790312256f10e83bb93f",
        "restaurant": "5dd9790212256f10e83bb934",
        "owner": "5dd9790112256f10e83bb932",
        "updatedAt": "2019-11-23T18:22:59.213Z",
        "createdAt": "2019-11-23T18:22:59.213Z",
        "__v": 0
    },
    "inventoryItems": [
        {
            "category": "ingredient",
            "type": "none",
            "description": null,
            "onStock": false,
            "stockQuantity": 200,
            "onProduction": false,
            "productionQuantity": 15,
            "referenceId": "lett",
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
            "_id": "5dd9790312256f10e83bb941",
            "owner": "5dd9790112256f10e83bb932",
            "restaurant": "5dd9790212256f10e83bb934",
            "inventory": "5dd9790312256f10e83bb93f",
            "title": "Organic lettuce",
            "updatedAt": "2019-11-23T18:22:59.215Z",
            "createdAt": "2019-11-23T18:22:59.215Z",
            "__v": 0
        },
        ...
    ],
    "woks": [
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
        ...
    ]
}
```

This endpoint retrieves the restaurant and it's dependencies. 

### HTTP Request

`GET  https://node.chefsurf.io/open-kitchen`

### Headers

Parameter | Content | Description
--------- | ------- | -----------
Authorization | JWT {{auth_token}} | Your token should be placed in the request, otherwise it will return a 403 error.

<!-- ### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
include_cats | false | If set to true, the result will also include cats.
available | true | If set to false, the result will include kittens that have already been adopted. -->

## Assign Dishes

> POST - https://node.chefsurf.io/open-kitchen/assign/dishes

```javascript
import {
  HttpClient
} from '@angular/common/http';

const path = 'https://node.chefsurf.io';

constructor(private http: HttpClient) {
}

assignDishes(params) {
  return this.http.post(`${path}/api/open-kitchen/assign/dishes`, {
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
                "pending": [],
                "added": [],
                "failed": [],
                "additions": []
            },
            "dishName": "Elote Bowl",
            "priority": "normal",
            "status": "queue",
            "sortOrder": 0,
            "simplifiedId": "3d79-3d7c",
            "cookingTime": 0,
            "_id": "5e09a4f5ab7c8b2691551468",
            "deleted": false,
            "orderItem": "5e091e65f79a1c3227d93d7c",
            "customer": "5e091e65f79a1c3227d93d73",
            "restaurant": "5dd9790212256f10e83bb934",
            "owner": "5dd9790112256f10e83bb932",
            "updatedAt": "2019-12-30T07:19:17.541Z",
            "createdAt": "2019-12-30T07:19:17.541Z",
            "__v": 0
        },
        ...
    ]
}
```

This endpoint assign dishes to the queue. The queue contains dishes splitted individually so the Raspberry Pi pulls those and assign them to the woks.

<aside class="warning">This endpoint will not longer be supported soon, it will be replaced with another endpoint.</aside>

### HTTP Request

`GET https://node.chefsurf.io/api/open-kitchen/assign/dishes`

### URL Parameters

The parameters are applied to the OrderItem's properties.

Parameter | Description
--------- | -----------
where_date | apply a date condition to the query. i.e <strong>2019-12-22</strong>
where_time | apply a time condition to the query i.e <strong>13:00:00</strong>
where_status | apply a status condition to the query i.e <strong>placed</strong>
where_priority | apply a priority condition to the query i.e <strong>urgent</strong>
where_customer | apply a customer._id condition to the query i.e <strong>5e091e65f79a1c3227d93d73</strong>

