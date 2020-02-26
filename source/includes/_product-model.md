## Product

> Schema definition

```javascript
let ProductSchema = new mongoose.Schema({
    owner: {
        type: mongooseType.ObjectId,
        ref: 'Owner',
        required: true,
        index: true
    },
    user: {
        type: mongooseType.ObjectId,
        ref: 'User',
        required: true,
        index: true
    },
    restaurant: {
        type: mongooseType.ObjectId,
        ref: 'Restaurant',
        required: true,
        index: true
    },
    category: {
        type: mongooseType.String,
        enum: [
            'grains_bowl_category',
            'greens_grains_bowl_category',
            'greens_bowl_category',
            'pita_category',
            'mini_pita_category',
            'soup_pita_category',
            'drink',
            'none'
        ],
        default: 'none',
        required: true
    },
    title: {
        type: String,
        required: true
    },
    price: {
        type: Number,
        required: true
    },
    description: {
        type: String,
        required: false
    },
    position: {
        type: Number,
        required: false
    },
    measurement: {
        type: String,
        enum: ['gram', 'kilogram', 'oz', 'piece', 'none'],
        default: 'none'
    },
    measurementUnit: {
        type: Number,
        default: null
    },
    calories: {
        type: Number,
        default: null
    },
    attachments: [{
        type: mongooseType.ObjectId,
        ref: 'Attachment'
    }],
    availability: {
        monday: {
            type: mongooseType.Boolean,
            required: false,
            default: true
        },
        tuesday: {
            type: mongooseType.Boolean,
            required: false,
            default: true
        },
        wednesday: {
            type: mongooseType.Boolean,
            required: false,
            default: true
        },
        thursday: {
            type: mongooseType.Boolean,
            required: false,
            default: true
        },
        friday: {
            type: mongooseType.Boolean,
            required: false,
            default: true
        },
        saturday: {
            type: mongooseType.Boolean,
            required: false,
            default: true
        },
        sunday: {
            type: mongooseType.Boolean,
            required: false,
            default: true
        }
    },
    ingredients: [{
        type: mongooseType.ObjectId,
        ref: 'ProductIngredient',
        index: true,
        required: false
    }],
    drinks: [{
        type: mongooseType.ObjectId,
        ref: 'ProductIngredient',
        index: true,
        required: false
    }],
    desserts: [{
        type: mongooseType.ObjectId,
        ref: 'ProductIngredient',
        index: true,
        required: false
    }],
    cookingTime: {
        type: mongooseType.Number,
        default: 0,
        required: true
    },
    createdBy: {
        type: mongooseType.ObjectId,
        ref: 'User',
        required: true,
        index: true
    },
});
```