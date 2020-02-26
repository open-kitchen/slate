## Order Item

> Schema definition

```javascript
let OrderItemSchema = new mongoose.Schema({
    restaurant: {
        type: types.ObjectId,
        ref: 'Restaurant',
        required: true,
        index: true
    },
    customer: {
        type: types.ObjectId,
        ref: 'User',
        required: true,
        index: true
    },
    order: {
        type: types.ObjectId,
        ref: 'Order',
        required: true,
        index: true
    },
    date: {
        type: types.String
    },
    time: {
        type: types.String
    },
    dateTime: {
        type: types.String
    },
    shoppingCartItem: {
        type: types.ObjectId,
        ref: 'ShoppingCartItem',
        required: true,
        index: true
    },
    complete: {
        type: types.Boolean,
        default: false
    },
    references: {
        shoppingCartItem: {}
    },
    status: {
        type: types.String,
        enum: ['placed', 'queue', 'cooking', 'delivering', 'ready_for_pickup', 'at_address', 'complete', 'returned', 'cancelled'],
        default: 'placed',
        required: true
    },
    priority: {
        type: types.String,
        enum: ['low', 'normal', 'urgent'],
        default: 'normal'
    },
    product: {
        type: types.ObjectId,
        ref: 'Product',
        required: true,
        index: true
    },
    total: {
        type: types.Number,
        required: true
    },
});
```