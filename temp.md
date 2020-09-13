
```js
const express = require('express');
const path = require('path');

// Instantiate our Express instance
const app = express();

// Tell Express to use the json() method to parse the HTTP request body. (Please note, you don't need body-parser anymore. Express now includes that functionality natively.)
app.use(express.json());
// Decode encoded content
app.use(express.urlencoded({extended: true}));

// Serve static files from this directory
app.use(express.static(path.join(__dirname, public)));

// ROUTES

// GET the homepage
app.get('/', function (req, res) {
   res.send('Welcome to the homepage!');
});

// Tell Express which port to listen to
app.listen(process.env.PORT || 8080);
```