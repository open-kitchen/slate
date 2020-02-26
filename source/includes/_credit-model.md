## Credit 

> Schema definition

```javascript
let CreditSchema = new mongoose.Schema({
    user: {
        type: mongoose.Schema.Types.ObjectId,
        ref: 'User',
        required: true
    },
    order: {
        type: mongoose.Schema.Types.ObjectId,
        ref: 'Order',
        required: false
    },
    reason: {
        type: String,
        required: true
    },
    amount: {
        type: Number,
        required: true
    },
    invitation: {
        type: mongoose.Schema.Types.ObjectId,
        ref: 'Invitation',
        required: false
    },
    referenceCredit: {
        type: mongoose.Schema.Types.ObjectId,
        ref: 'Credit',
        required: false
    },
    type: {
        type: mongoose.Schema.Types.String,
        enum: ['invite', 'transaction', 'refund', 'gift', 'super_admin_granted']
    },
    grantedBy: {
        type: mongoose.Schema.Types.ObjectId,
        ref: 'User',
        required: false
    },
    grantedAt: {
        type: mongoose.Schema.Types.String
    }
});
```