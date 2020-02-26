## Dish

> Schema definition

```javascript
let DishSchema = new mongoose.Schema({
    dishName: {
        type: types.String,
        required: false,
        default: ``
    },
    dishPicture: {
        type: types.ObjectId,
        required: false,
        ref: 'Attachment',
    },
    product: {
        type: types.ObjectId,
        required: false,
        index: true,
        ref: 'Product',
    },
    priority: {
        type: types.String,
        enum: ['low', 'normal', 'urgent'],
        default: 'normal'
    },
    status: {
        type: types.String,
        enum: ['queue', 'cooking', 'packing', 'finished', 'failed', 'cancelled', 'on_review'],
        required: false,
        default: 'queue'
    },
    sortOrder: {
        type: types.Number,
        default: 0,
    },
    simplifiedId: {
        type: types.String,
        default: '----',
        // required: true
    },
    cookingTime: {
        type: types.Number,
        default: 0,
        // required: true
    },
    pendingIngredients: [{
        type: types.ObjectId,
        ref: 'DishIngredient',
    }],
    addedIngredients: [{
        type: types.ObjectId,
        ref: 'DishIngredient',
    }],
    failedIngredients: [{
        type: types.ObjectId,
        ref: 'DishIngredient',
    }],
    orderItem: {
        type: types.ObjectId,
        ref: 'OrderItem',
        required: true,
        index: true
    },
    restaurant: {
        type: types.ObjectId,
        ref: 'Restaurant',
        required: true,
        index: true
    },
    owner: {
        type: types.ObjectId,
        ref: 'Owner',
        required: true,
        index: true
    },
    customer: {
        type: types.ObjectId,
        ref: 'User',
        required: true,
        index: true
    },
    wok: {
        type: types.ObjectId,
        ref: 'Wok',
        require: false,
    }
});
```