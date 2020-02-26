## Shopping Cart 

> Schema definition

```javascript
let ShoppingCartSchema = new mongoose.Schema({
    owner: {
        type: mongoose.Schema.Types.ObjectId,
        ref: 'Owner',
        required: true
    },
    user: {
        type: mongoose.Schema.Types.ObjectId,
        ref: 'User',
        required: true
    },
    restaurant: {
        type: mongoose.Schema.Types.ObjectId,
        ref: 'Restaurant',
        required: true
    },
    completed: {
        type: Boolean,
        default: false
    },
    order: {
        type: mongoose.Schema.Types.ObjectId,
        ref: 'Order',
        required: false,
        default: null
    },
    startDay: { //will be removed
        type: mongoose.Schema.Types.Number,
        required: false
    },
    endDay: { //will be removed
        type: mongoose.Schema.Types.Number,
        required: false
    },
    dates: [], //will be removed
    shoppingCartItems: [{
        type: mongoose.Schema.Types.ObjectId,
        ref: 'ShoppingCartItem'
    }],
    coupon: {
        _id: {
            type: mongoose.Schema.Types.ObjectId,
            ref: 'Coupon'
        },
        reference: {}
    },
    creditsUsed: {
        type: mongoose.Schema.Types.Number,
        default: 0
    },
    subTotal: {
        type: Number,
        default: 0,
        required: true
    },
    discount: {
        type: Number,
        default: 0
    },
    taxes: {
        type: Number,
        default: 0,
        required: true
    },
    total: {
        type: Number,
        default: 0,
        required: true
    },
});
```