# Products

## Get Products

```javascript
import {
  HttpClient
} from '@angular/common/http';

const path = 'https://node.chefsurf.io/api/products';

constructor(private http: HttpClient) {
}

requestProducts(params) {
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
            "availability": {
                "monday": true,
                "tuesday": true,
                "wednesday": true,
                "thursday": true,
                "friday": true,
                "saturday": true,
                "sunday": true
            },
            "category": "grains_bowl_category",
            "measurement": "gram",
            "measurementUnit": 700,
            "calories": 580,
            "attachments": [
                "5dd9797f12256f10e83bb9c7"
            ],
            "ingredients": [
                "5dd9797f12256f10e83bb9c9",
                ...
            ],
            "drinks": [
                "5dd9840a64bebe12632fb79e",
                ...
            ],
            "desserts": [
                "5dd9840a64bebe12632fb7a1",
                ...
            ],
            "deleted": false,
            "_id": "5dd9797f12256f10e83bb9c8",
            "owner": "5dd9790112256f10e83bb932",
            "user": "5dd9790112256f10e83bb933",
            "restaurant": "5dd9790212256f10e83bb934",
            "title": "Elote Bowl",
            "price": 12000,
            "description": "organic arugula,\n        warm quinoa,\n        cilantro,\n        shredded cabbage,\n        spicy sunflower seeds,\n        tomato,\n        tortilla chips,\n        goat cheese,\n        roasted corn + peppers,\n        lime cilantro jalapeno vinaigrette",
            "position": 1,
            "updatedAt": "2019-11-23T19:10:02.600Z",
            "createdAt": "2019-11-23T18:25:03.203Z",
            "__v": 2
        },
        ...
    ]
}
```

This endpoint retrieves a list of products that the staff / chef can see under the same ownership.

### HTTP Request

`GET https://node.chefsurf.io/api/products`

### URL Parameters

Parameter | Description |
--------- | ----------- |
where_title | apply a title condition to the query. i.e <strong>Elote Bowl</strong>
like_title  | apply a title condition to the query where it finds any possible match not the exact title, i.e <strong>Elote</strong>, that will bring Elote Bowl in the request response.
where_price | apply a price condition to the query i.e <strong>12000</strong>
where_category | apply a category condition to the query i.e <strong>greens_grains_bowl_category</strong>
where_availability.monday | apply a availability condition to specific day to the query i.e <strong>true</strong>

## Get Product

> GET - https://node.chefsurf.io/open-kitchen/products/:product_id

```javascript
import {
  HttpClient
} from '@angular/common/http';

const path = 'https://node.chefsurf.io/api/products';

constructor(private http: HttpClient) {
}

requestProduct(product_id, params) {
  return this.http.get(`${path}/${product_id}`, {
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
        "availability": {
            "monday": true,
            "tuesday": true,
            "wednesday": true,
            "thursday": true,
            "friday": true,
            "saturday": true,
            "sunday": true
        },
        "category": "grains_bowl_category",
        "measurement": "gram",
        "measurementUnit": 700,
        "calories": 580,
        "attachments": [
            "5dd9797f12256f10e83bb9c7"
        ],
        "ingredients": [
            "5dd9797f12256f10e83bb9c9",
            ...
        ],
        "drinks": [
            "5dd9840a64bebe12632fb79e",
           ...
        ],
        "desserts": [
            "5dd9840a64bebe12632fb7a1",
            ....
        ],
        "deleted": false,
        "_id": "5dd9797f12256f10e83bb9c8",
        "owner": "5dd9790112256f10e83bb932",
        "user": "5dd9790112256f10e83bb933",
        "restaurant": "5dd9790212256f10e83bb934",
        "title": "Elote Bowl",
        "price": 12000,
        "description": "organic arugula,\n        warm quinoa,\n        cilantro,\n        shredded cabbage,\n        spicy sunflower seeds,\n        tomato,\n        tortilla chips,\n        goat cheese,\n        roasted corn + peppers,\n        lime cilantro jalapeno vinaigrette",
        "position": 1,
        "updatedAt": "2019-11-23T19:10:02.600Z",
        "createdAt": "2019-11-23T18:25:03.203Z",
        "__v": 2
    }
}
```

This endpoint retrieves one product by the ID.

### HTTP Request

`GET https://node.chefsurf.io/open-kitchen/products/:product_id`

<!-- ### URL Parameters -->
<!-- 
Parameter | Description
--------- | -----------
ID | The ID of the kitten to delete
 -->

## Create Product

> POST = https://node.chefsurf.io/api/products

```javascript
  import {
  HttpClient
} from '@angular/common/http';

const path = 'https://node.chefsurf.io/api/products';

constructor(private http: HttpClient) {
}

createProduct(data) {
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
        "availability": {
            "monday": true,
            "tuesday": true,
            "wednesday": true,
            "thursday": true,
            "friday": true,
            "saturday": true,
            "sunday": true
        },
        "category": "grains_bowl_category",
        "measurement": "gram",
        "measurementUnit": 700,
        "calories": 580,
        "attachments": [
            "5dd9797f12256f10e83bb9c7",
            ...
        ],
        "ingredients": [
            "5dd9797f12256f10e83bb9c9",
            ...
        ],
        "drinks": [
            "5dd9840a64bebe12632fb79e",
            ...
        ],
        "desserts": [
            "5dd9840a64bebe12632fb7a1"
        ],
        "_id": "5e1b5b97ab6f9f1a03679d05",
        "deleted": false,
        "owner": "5dd9790112256f10e83bb932",
        "user": "5dd9790212256f10e83bb937",
        "restaurant": "5dd9790212256f10e83bb934",
        "title": "Elote Bowl",
        "price": 12000,
        "description": "organic arugula,\n        warm quinoa,\n        cilantro,\n        shredded cabbage,\n        spicy sunflower seeds,\n        tomato,\n        tortilla chips,\n        goat cheese,\n        roasted corn + peppers,\n        lime cilantro jalapeno vinaigrette",
        "position": 1,
        "createdBy": "5dd9790212256f10e83bb937",
        "updatedAt": "2020-01-12T17:47:03.314Z",
        "createdAt": "2020-01-12T17:47:03.314Z",
        "__v": 0
    }
}
```

This endpoint allows you to create a new product. if you create a new product you need to be aware that you need to make sure to only pass the fillable properties. otherwise it will throw an exception or it will be overriden by the authUser information.

## Update Product 

> PUT - https://node.chefsurf.io/api/products/product_id

```javascript
import {
  HttpClient
} from '@angular/common/http';

const path = 'https://node.chefsurf.io/api/products';

constructor(private http: HttpClient) {
}

updateProduct(product_id, params) {
  return this.http.put(`${path}/${product_id}`, params, {
    headers: {
      Authorization: `JWT ${jwt_token}`
    }
  });
}
```

> Sample Data ( you can send the params you want to be updated in your request )

```json
{
  "title": "Elote Bowl Updated",
  "price": 15000  
}
```

> The above command returns JSON structured like this:

```json
{
    "data": {
        "availability": {
            "monday": true,
            "tuesday": true,
            "wednesday": true,
            "thursday": true,
            "friday": true,
            "saturday": true,
            "sunday": true
        },
        "category": "grains_bowl_category",
        "measurement": "gram",
        "measurementUnit": 700,
        "calories": 580,
        "attachments": [
            "5dd9797f12256f10e83bb9c7"
        ],
        "ingredients": [
            "5dd9797f12256f10e83bb9c9",
            ...
        ],
        "drinks": [
            "5dd9840a64bebe12632fb79e",
            ...
        ],
        "desserts": [
            "5dd9840a64bebe12632fb7a1"
        ],
        "deleted": false,
        "_id": "5e1b5b97ab6f9f1a03679d05",
        "owner": "5dd9790112256f10e83bb932",
        "user": "5dd9790212256f10e83bb937",
        "restaurant": "5dd9790212256f10e83bb934",
        "title": "Elote Bowl Updated",
        "price": 15000,
        "description": "organic arugula,\n        warm quinoa,\n        cilantro,\n        shredded cabbage,\n        spicy sunflower seeds,\n        tomato,\n        tortilla chips,\n        goat cheese,\n        roasted corn + peppers,\n        lime cilantro jalapeno vinaigrette",
        "position": 1,
        "createdBy": "5dd9790212256f10e83bb937",
        "updatedAt": "2020-01-12T17:49:41.358Z",
        "createdAt": "2020-01-12T17:47:03.314Z",
        "__v": 0
    }
}
```

This endpoint allows you to modify the product, not a lot of the properties can be modified and there are formats that must be followed otherwise it will throw an error.

### HTTP Request

`PUT - https://node.chefsurf.io/api/products/product_id`

### Fillable properties

Parameter | Type   | Description |
--------- | ------ | ----------- |
category  | String   | You can modify the category the product belongs to.
price | Number   | you can modify the price of the product.
description   | String   | You can modify the description of the product.
position       | Numner   | You can change the order of the product, sorting is based on this property.
measurement | String  | You can specify the measurement of the product content, it could be any of this values ['gram', 'kilogram', 'oz', 'piece', 'none'].
measurementUnit | Number | You can specify the units depending of the measurement selected.
calories | Number | You can specify the number of calories the dish contains ( without the aditional toppings the client might add to it ).
attachments | Array<ObjectID> | You can add upto 5 pictures you want for the product.
availability | Map<Boolean> | You can specify which days of the week, this product will be visible.
ingredients | Array<ObjectID> | You can add all the ingredients needed for the product and specify all the details on the ProductIngredient model.
drinks | Array<ObjectID> | You can add all the drinks needed for the product and specify all the details on the ProductIngredient model.
desserts | Array<ObjectID> | You can add all the desserts needed for the product and specify all the details on the ProductIngredient model.

### Non fillable

Parameter | Type | Description
--------- | ---- | ------------
_id       | ObjectID | Primary key.
restaurant| ObjectID | Restaurant Object ID.
owner     | ObjectID | Ower Object ID.
createdBy | ObjectID | User Object ID.
updatedAt | DateTime | Update timestamps - auto generated.
createdAt | DateTime | Create timestamps - auto generated.

## Delete Product 

> DELETE - https://node.chefsurf.io/api/products/product_id

```javascript
import {
  HttpClient
} from '@angular/common/http';

const path = 'https://node.chefsurf.io/api/products';

constructor(private http: HttpClient) {
}

/**
 * @param {String} product_id
*/
deleteProduct(product_id) {
  return this.http.delete(`${path}/${product_id}`, {
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
        "availability": {
            "monday": true,
            "tuesday": true,
            "wednesday": true,
            "thursday": true,
            "friday": true,
            "saturday": true,
            "sunday": true
        },
        "category": "grains_bowl_category",
        "measurement": "gram",
        "measurementUnit": 700,
        "calories": 580,
        "attachments": [
            "5dd9797f12256f10e83bb9c7"
        ],
        "ingredients": [
            "5dd9797f12256f10e83bb9c9",
            ...
        ],
        "drinks": [
            "5dd9840a64bebe12632fb79e",
            ...
        ],
        "desserts": [
            "5dd9840a64bebe12632fb7a1"
        ],
        "deleted": true,
        "_id": "5e1b5b97ab6f9f1a03679d05",
        "owner": "5dd9790112256f10e83bb932",
        "user": "5dd9790212256f10e83bb937",
        "restaurant": "5dd9790212256f10e83bb934",
        "title": "Elote Bowl Updated",
        "price": 15000,
        "description": "organic arugula,\n        warm quinoa,\n        cilantro,\n        shredded cabbage,\n        spicy sunflower seeds,\n        tomato,\n        tortilla chips,\n        goat cheese,\n        roasted corn + peppers,\n        lime cilantro jalapeno vinaigrette",
        "position": 1,
        "createdBy": "5dd9790212256f10e83bb937",
        "updatedAt": "2020-01-12T17:49:41.358Z",
        "createdAt": "2020-01-12T17:47:03.314Z",
        "deletedAt": "2020-01-03T06:24:06.698Z",
        "__v": 0
    }
}
```

> If you are trying to delete a product that it has been deleted, you will get an exception: 404.

```json
{
    "code": "NotFound",
    "message": "Record not found."
}
```

This endpoint deletes a specific product.

### HTTP Request

`DELETE - https://node.chefsurf.io/api/products/product_id`


