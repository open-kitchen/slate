## Client

> Schema definition

```javascript
let ClientSchema = new mongoose.Schema({
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
    allowCashPayments: {
        type: mongoose.Schema.Types.Boolean,
        default: false
    },
    identityNumber: {
        type: mongoose.Schema.Types.String,
        required: true
    },
    phone: {
        type: mongoose.Schema.Types.String,
        required: false
    },
    active: {
        type: Boolean,
        default: true
    },
    lastAddressUsed: {
        
    },
    lastPaymentMethodUsed: {
        type: mongoose.Schema.Types.String,
        enum: ['cash', 'credit_card', 'credits', 'rappi'],
        required: false
    }
});
```