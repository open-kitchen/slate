## Inventory 

> Schema Definition

```javascript
let InventorySchema = new mongoose.Schema({
    owner: {
        type: mongoose.Schema.Types.ObjectId,
        ref: 'Owner',
        required: true,
        index: true
    },
    restaurant: {
        type: SchemaTypes.ObjectId,
        ref: 'Restaurant',
        required: true,
        index: true
    },
    maxCapacity: {
        type: SchemaTypes.Number,
        min: 1,
        max: 9999,
        required: true,
        default: 10
    },
    sendAlertsOnLowInventory: {
        type: SchemaTypes.Boolean,
        default: false
    },
    alertOnQuantity: {
        type: SchemaTypes.Number,
        min: 1,
        default: 1,
        required: true
    },
    current: {
        type: SchemaTypes.Boolean,
        default: false
    }
});
```