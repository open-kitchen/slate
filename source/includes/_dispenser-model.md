## Dispenser

> Schema Definition

```javascript
let DispenserSchema = new mongoose.Schema({
    restaurant: {
        type: types.ObjectId,
        ref: 'Restaurant',
        required: true,
        index: true
    },
    label: {
        type: types.String,
        required: true,
    },
    identifier: {
        type: types.String,
        required: true,
    },
    owner: {
        type: types.ObjectId,
        ref: 'Owner',
        required: true,
        index: true,
    },
    inventoryItem: {
        type: types.ObjectId,
        ref: 'InventoryItem',
        required: false,
    },
    capacity: {
        type: types.Number,
        default: null,
        required: false
    },
    currentLoad: {
        type: types.Number,
        default: null,
        required: false
    },
    active: {
        type: types.Boolean,
        default: false,
        required: true,
    },
    notes: {
        type: types.String,
        default: "",
        required: false
    }
});
```