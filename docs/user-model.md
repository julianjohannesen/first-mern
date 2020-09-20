[back to index](/README.md) | [prev](/docs/7.md) | [next](/docs/.9md)

# Step 8 - Creating the User Model

Now that Mongo is properly installed and running, it's time to install Mongoose.

```
npm i mongoose
```

Create a new file in the src directory and name it User.js. You'll use this file to define a schema for a user collection.  Remember, a collection is similar to a table in a relational database. Strictly speaking, Mongo does not use schemas. However, Mongoose can create a sort of schema for us.

Copy and paste this code into User.js:

```js
// User.js
const mongoose = require('mongoose');

// Instantiate an instance of Mongoose's Schema class and name it UserSchema. The argument passed to Schema defines the fields that appear in each document in the collection. Remember, a document is similar to a record.
const UserSchema = new mongoose.Schema({
    // The key is the name of the field and the value is an object defining the field's properties.
    fname: { type: String, required: true },
    lname: { type: String, required: true },
    email: { type: String, required: true, unique: true },
    password: { type: String, required: true }
});

// Next, the schema needs to be turned into a model using Mongoose's model() method. The model method takes as parameters the name of the model and a schema. The model makes it possible to perform CRUD operations on the collection. You're also exporting this module at the same time.
module.exports = mongoose.model('User', UserSchema);
```

Now that the User model is defined, import it into server.js.

```js
// server.js
// Add this to the import section of server.js
const User = require("./User.js");
```

Now oad the React front-end and use the registration form to register a new user.
