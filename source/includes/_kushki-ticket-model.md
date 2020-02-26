## Kushki Ticket

> Schema definition

```javascript
let KushkiTicketSchema = new mongoose.Schema({
    user: {
        type: types.ObjectId,
        ref: 'User',
        required: true,
        index: true
    },
    kushkiCard: {
        type: types.ObjectId,
        ref: 'KushkiCard',
        required: true,
    },
    ticketNumber: {
        type: types.String,
        required: true,
        set: _encryptIt,
    },
    token: {
        type: types.String,
        required: true,
        set: _encryptIt,
    },
    requiresWebhook: {
        type: types.Boolean,
        default: false
    },
    currencyCode: {
        type: types.String,
        enum: ['COP', 'USD', 'CAD']
    },
    ip: {
        type: types.String,
        required: false,
        set: _encryptIt,
    },
    maskedCardNumber: {
        type: types.String,
    },
    approvedTransactionAmount: {
        type: types.Number
    },
    subtotalIva: {
        type: types.Number,
        required: false
    },
    subtotalIva0: {
        type: types.Number,
        required: false
    },
    responseCode: {
        type: types.String,
    },
    transactionType: {
        type: types.String,
    },
    approvalCode: {
        type: types.String,
    },
    transactionStatus: {
        type: types.String,
        required: false
    },
    requestAmount: {
        type: types.Number,
    },
    type: {
        type: types.String,
        enum: ['single_charge', 'subscription', 'refund', 'void'],
        default: 'single_charge'
    },
    details: {
        type: JSON,
        set: _encryptDetails
    }
});
```