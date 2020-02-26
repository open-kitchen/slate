## User

> Schema definition

```javascript
const UserSchema = new Schema({
    owner: {
        type: Schema.Types.ObjectId,
        ref: 'Owner',
        required: true
    },
    role: {
        type: String,
        enum: ['chef', 'staff', 'restaurant_owner', 'client', 'delivery_guy', 'chefsurf_admin'],
        default: 'client',
        required: true
    },
    chef: {
        type: Schema.Types.ObjectId,
        ref: 'Chef',
        required: false
    },
    client: {
        type: Schema.Types.ObjectId,
        ref: 'Client',
        required: false
    },
    deliveryGuy: {
        type: Schema.Types.ObjectId,
        ref: 'DeliveryGuy',
        required: false
    },
    superAdmin: {
        type: Schema.Types.ObjectId,
        ref: 'SuperAdmin',
        required: false
    },
    firstName: {
        type: String,
        required: false
    },
    lastName: {
        type: String,
        required: false,
    },
    name: {
        type: String,
        required: false
    },
    username: {
        type: String,
        required: true,
        unique: true,
        index: true
    },
    phone: {
        type: String,
        required: false
    },
    celullar: {
        type: String,
        required: false
    },
    dob: {
        type: Date,
        required: false
    },
    email: {
        type: String,
        required: true,
        unique: true,
        index: {
            unique: true
        }
    },
    pictureUrl: {
        type: String,
        required: false
    },
    active: {
        type: Boolean,
        required: true,
        default: true
    },
    selectedLanguage: {
        type: String,
        enum: ['english', 'spanish', 'portuguese', 'french'],
        default: 'spanish'
    },
    password: {
        type: String,
        required: true
    },
    location: {
        type: String,
        required: false
    },
    nationality: {
        type: String,
        required: false
    },
    gender: {
        type: String,
        enum: ['male', 'female', 'none'],
        default: 'none'
    },
    banned: {
        type: Boolean,
        default: false
    },
    onboardStep: {
        type: Number
    },
    onboardType: {
        type: String,
        enum: ['chef', 'restaurant', 'client', 'delivery_guy', 'chefsurf_admin'],
        default: 'client',
    },
    isEmailVerified: {
        type: Boolean,
        default: false
    },
    isVerified: {
        type: Boolean,
        default: false
    },
    selfCreated: {
        type: Boolean,
        default: true
    },
    googleId: {
        type: String,
        required: false
    },
    facebookId: {
        type: String,
        required: false
    },
    requestToken: {
        type: String,
        required: false
    },
    currency: {
        type: String,
        enum: ['cop', 'mxn', 'usd', 'cad'],
        default: 'cop'
    },
});
```