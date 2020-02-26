## Chef

> Schema definition

```javascript
let ChefSchema = new mongoose.Schema({
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
        required: false
    },
    jobTitle: {
        type: mongoose.Schema.Types.String,
        default: 'Chef',
        required: false
    },
    active: {
        type: Boolean,
        default: true
    }
});
```