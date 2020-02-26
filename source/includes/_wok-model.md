## Wok

> Schema definition

```javascript
let WokSchema = new mongoose.Schema({
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
    label: {
        type: types.String,
        required: true
    },
    identifier: {
        type: types.String,
        required: true
    },
    status: {
        type: types.String,
        enum: [
            'available', 
            'waiting_for_ingredients', 
            'cooking', 
            'dispensing', 
            'cleaning'
        ],
        required: true,
        default: 'available'
    },
    hasErrors: {
        type: types.Boolean,
        default: false,
        required: false
    },
    errorCode: {
        type: types.String,
        required: false
    },
    notes: {
        type: types.String,
        required: false,
        default: ' '
    },
    dish: {
        type: types.ObjectId,
        ref: 'Dish',
        required: false,
        default: null
    },
    temperature: {
        type: types.Number,
        required: false
    },
    cookingTime: {
        type: types.Number,
        required: false
    }
});
```