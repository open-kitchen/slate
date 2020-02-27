## Order

> Schema definition

```javascript
let OrderSchema = new mongoose.Schema({
    shoppingCart: {
        type: mongoose.Schema.Types.ObjectId,
        ref: 'ShoppingCart',
        required: true
    },
    shoppingCartItems: [{
        type: mongoose.Schema.Types.ObjectId,
        ref: 'ShoppingCartItem',
        required: false
    }],
    references: {
        shoppingCartItems: [], //@deprecated
        sellingWeek: {},
    },
    customer: {
        type: mongoose.Schema.Types.ObjectId,
        ref: 'User',
        required: true
    },
    restaurant: {
        type: mongoose.Schema.Types.ObjectId,
        ref: 'Restaurant',
        required: false
    },
    type: {
        type: String,
        enum: ['client', 'chef'],
        default: 'client',
        required: true
    },
    referenceOrder: {
        type: mongoose.Schema.Types.ObjectId,
        ref: 'Order',
        required: false
    },
    receivingMethod: {
        type: mongoose.Schema.Types.String,
        enum: ['delivery', 'eat_here', 'to_go'],
        default: 'eat_here'
    },
    clientLocation: {},
    deliveryFee: {
        type: Number,
        default: 1,
        required: true
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
    paymentMethod: {
        type: String,
        enum: ['cash', 'credit_card', 'credits', 'cash_and_credits', 'credit_card_and_credits'],
        required: true
    },
    cancellationReason: {
        type: String,
        required: false
    },
    transaction: {
        type: mongoose.Schema.Types.ObjectId,
        ref: 'Transaction',
        required: false
    },
    status: {
        type: String,
        enum: ['draft', 'placed', 'preparing_order', 'delivering', 'ready_for_pickup', 'at_address', 'complete', 'refunded', 'cancelled'],
        default: 'draft',
        required: true
    },
    foodStatus: {
        type: String,
        enum: ['not_started', 'preparing', 'cooked', 'packed'],
        default: 'not_started',
        required: true
    },
    paymentStatus: {
        type: String,
        enum: ['pending', 'validating', 'paid', 'rejected'],
        default: 'pending',
        required: true
    },
    deliveryStatus: {
        type: String,
        enum: ['pending', 'delivering', 'at_address', 'delivered', 'returned', 'user_not_showed_up', 'at_front', 'none'],
        default: 'none',
        required: true
    },
    // selectedTime: {
    //     type: mongoose.Schema.Types.String,
    //     default: '12:00:00'
    // },
    // selectedDate: {
    //     type: mongoose.Schema.Types.String,
    // },
    payUResponses: [], //@deprecated
    coupon: {
        _id: {
            type: mongoose.Schema.Types.ObjectId,
            ref: 'Coupon'
        },
        reference: {}
    },
    credit: {
        type: mongoose.Schema.Types.ObjectId,
        ref: 'Credit',
        required: false
    },
    contactPhone: {
        type: mongoose.Schema.Types.String
    },
    origin: {
        type: mongoose.Schema.Types.String,
        enum: ['web', 'android', 'ios', 'bot'],
        default: 'web'
    },
    appVersion: {
        type: mongoose.Schema.Types.String,
        default: 'not_set',
        required: false
    },
    orderItems: [{
        type: mongoose.Schema.Types.ObjectId,
        ref: 'OrderItem',
        required: false
    }]
});
```