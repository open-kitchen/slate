## Kushki Card

> Schema definition

```javascript
let KushkiCardSchema = new mongoose.Schema({
    user: {
        type: types.ObjectId,
        ref: 'User',
        required: true,
        index: true
    },
    last4: {
        type: types.String,
        required: true,
    },
    expMonth: {
        type: types.String,
        required: true,
    },
    expYear: {
        type: types.String,
        required: true,
    },
    cvv: {
        type: types.String,
        required: false
    },
    subscriptionId: {
        type: types.String,
        required: false,
    },
    token: {
        type: types.String,
        required: true
    },
    active: {
        type: types.Boolean,
        default: true
    },
    type: {
        type: types.String,
        enum: ['single_charge', 'subscription'],
        default: 'single_charge'
    },
    singlePaymentAmount: {
        type: types.Number,
        required: false,
        default: null
    },
    currency: {
        type: types.String,
        enum: ['COP', 'USD', 'CAD'],
        default: 'COP',
        required: true
    },
});
```