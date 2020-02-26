## Inventory Item

> Schema definition 

```javascript
let InventoryItemSchema = new mongoose.Schema({
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
    inventory: {
        type: SchemaTypes.ObjectId,
        ref: 'Inventory',
        required: true,
        index: true
    },
    category: {
        type: SchemaTypes.String,
        enum: ['ingredient', 'drink', 'dessert'],
        default: 'ingredient'
    },
    type: {
        type: SchemaTypes.String,
        enum: ['base', 'veggie', 'dressing', 'protein', 'extra', 'drink', 'dessert', 'topping', 'premium', 'none'],
        default: 'none',
        required: false
    },
    origin: {
        type: SchemaTypes.String,
        enum: ['dispenser', 'cold_bar', 'fridge', 'other'],
        default: 'dispenser',
        required: true,
    },
    otherOrigin: {
        type: SchemaTypes.String,
        default: null,
        required: false
    },
    title: {
        type: SchemaTypes.String,
        required: true,
        index: false
    },
    description: {
        type: SchemaTypes.String,
        required: false,
        default: null
    },
    onStock: {
        type: SchemaTypes.Boolean,
        default: false,
        required: false
    },
    stockQuantity: {
        type: SchemaTypes.Number,
        required: true,
        min: 0,
        max: 9999,
        default: 0
    },
    onProduction: {
        type: SchemaTypes.Boolean,
        default: false,
        required: false
    },
    productionQuantity: {
        type: SchemaTypes.Number,
        required: true,
        min: 0,
        max: 9999,
        default: 0
    },
    referenceId: {
        type: SchemaTypes.String,
        required: true,
        default: '---'
    },
    maxProductionCapacity: {
        type: SchemaTypes.Number,
        required: false,
        min: 1,
        max: 9999,
        default: 50
    },
    price: {
        type: SchemaTypes.Number,
        required: false,
        min: 0,
        default: 0
    },
    measurement: {
        type: String,
        enum: ['gram', 'kilogram', 'oz', 'piece', 'none'],
        default: 'none',
        required: false
    },
    measurementUnit: {
        type: Number,
        default: null,
        required: false
    },
    totalMeasurement: {
        type: String,
        enum: ['gram', 'kilogram', 'oz', 'piece', 'none'],
        default: 'none',
        required: false
    },
    totalMeasurementUnits: {
        type: Number,
        default: null,
        required: false
    },
    priceForRawItem: {
        type: SchemaTypes.Number,
        required: false,
        min: 0,
        default: 0
    },
    pictures: [{
        type: SchemaTypes.ObjectId,
        ref: 'Attachment',
        required: false,
    }]
});
```