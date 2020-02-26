## Shopping Cart Item

> Schema definition

```javascript
let ShoppingCartItemSchema = new mongoose.Schema({
    shoppingCart: {
        type: types.ObjectId,
        ref: 'ShoppingCart',
        required: true
    },
    owner: {
        type: types.ObjectId,
        ref: 'Owner',
        required: true
    },
    product: {
        type: types.ObjectId,
        ref: 'Product',
        required: true,
        index: true
    },
    restaurant: {
        type: types.ObjectId,
        ref: 'Restaurant',
        required: true
    },
    quantity: {
        type: types.Number,
        required: true
    },
    productPrice: {
        type: types.Number,
        required: true,
    },
    subTotal: {
        type: types.Number,
        required: false
    },
    total: {
        type: types.Number,
        required: true
    },
    notes: {
        type: types.String,
        required: false
    },
    selectedDate: {
        date: types.String, //string now
        dayInEnglish: types.String,
        dayInSpanish: types.String,
        dayNumber: types.Number,
        time: {
            type: types.String,
            default: '12:00:00'
        }
    },
    type: {
        type: String,
        enum: ['drink', 'dish'],
        default: 'dish',
        required: true,
    },
    selectedIngredients: [{
        type: types.ObjectId,
        ref: 'ShoppingCartItemIngredient',
    }],
    drinkDetails: {},
    ingredients: [{}],
    customerName: {
        type: types.String,
        required: false
    }
});
```

The shopping cart items are essential for our proper functionality of the order flow inside Satee, it's not mandatory to follow this but it's recommended since OpenKitchen works better with all this models connected properly. Your integration will work at the best shape if you use our ChefSurf api's to create this data for your restaurant website/app.