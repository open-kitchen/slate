## Coupon

> Schema definition

```javascript
let CouponSchema = new mongoose.Schema({
    creator: {
        type: mongoose.Schema.Types.ObjectId,
        ref: 'User',
        required: true
    },
    category: {
        type: String,
        enum: ['food_discount', 'order_discount', 'delivery_discount', 'waive_delivery', 'waive_food'],
        required: true
    },
    type: {
        type: String,
        enum: ['percentage', 'amount'],
        required: true
    },
    value: {
        type: Number,
        required: false,
    },
    currency: {
        type: String,
        enum: ['cop', 'mxn', 'usd', 'cad'],
        default: 'cop'
    },
    availability: {
        type: String,
        enum: ['all_chefs', 'exclusive_chef', 'exclusive_product'],
        required: true,
        default: 'all_chefs'
    },
    user: {
        type: mongoose.Schema.Types.ObjectId,
        ref: 'User',
        required: false
    },
    chef: {
        type: mongoose.Schema.Types.ObjectId,
        ref: 'Chef',
        required: false
    },
    startDate: {
        type: Date
    },
    endDate: {
        type: Date
    },
    availableForInDays: {
        type: Number,
        required: false
    },
    invitation: {
        type: Boolean,
        required: false
    },
    code: {
        type: String,
        default: null,
        unique: true
    },
    conditions: {
        minQuantity: {
            type: Number,
            default: 5000,
            min: 1
        },
        maxQuantity: {
            type: Number
        },
        minProducts: {
            type: Number,
            default: 1,
            min: 0
        },
        maxProducts: {
            type: Number,
            default: 99
        },
        onlyIfPairs: {
            type: Boolean,
            default: false
        },
        usageLimit: {
            type: Number,
            required: false,
            default: 1,
            min: 1
        }
    },
    usages: [{
        type: mongoose.Schema.Types.ObjectId,
        ref: 'Order'
    }]
});
```