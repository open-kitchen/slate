## Restaurant   

> Schema definition

```javascript
let RestaurantSchema = new mongoose.Schema({
    owner: {
        type: mongoTypes.ObjectId,
        ref: 'Owner',
        required: true,
        index: true
    },
    user: {
        type: mongoTypes.ObjectId,
        ref: 'User',
        required: true,
        index: true
    },
    chefs: [{
        type: mongoTypes.ObjectId,
        ref: 'Chef'
    }],
    logo: {
        type: String,
        required: false,
        default: null
    },
    background: {
        type: String,
        required: false,
        default: null
    },
    location: {},
    name: {
        type: mongoTypes.String,
        default: null
    },
    automatedKitchen: {
        type: Boolean,
        required: false,
        default: false
    },
    deliveryAvailable: {
        type: Boolean,
        default: true,
        required: false
    },
    pickUpAvailable: {
        type: Boolean,
        default: true,
        required: false
    },
    cashPaymentAvailable: {
        type: Boolean,
        default: true,
        required: false
    },
    creditCardPaymentAvailable: {
        type: Boolean,
        default: true,
        required: false
    },
    domain: {
        type: mongoTypes.String,
        required: true,
        unique: true
    }
});
```