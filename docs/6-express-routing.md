<!-- @format -->

[back to index](/README.md) | [prev](/docs/5.md) | [next](/docs/7.md)

# Step 6 - Adding API Routes to the Express Server

The Home and Log In components that you created on the front-end will eventually communicate with the Express server. Before that can happen, you need to create the routes that those components will interact with. Open server.js and replace the current text with the text below. We've removed the comments from previous steps and marked the new code block.

```js
// server.js

const express = require("express");
const mongoose = require("mongoose");

const app = express();

app.get('/', function (req, res) {
   res.send('Welcome to the home page.');
});

// START OF NEW STUFF

// Route to home page info
app.get('/api/home', function (req, res) {
   res.send('Welcome!');
});

// Route to log in info
app.get('/api/login', function (req, res) {
   res.send('Please log in.');
});

// END OF NEW STUFF

const mongo_uri = 'mongodb://localhost/first-mern';
mongoose.connect(mongo_uri, {useNewUrlParser: true, useUnifiedTopology: true}, function (err) {
   if (err) {throw err} 
   else {console.log(`Connected to ${mongo_uri}`)}
});

app.listen(process.env.PORT || 8080);
```

Note that both of these routes start with “/api/”. Also note that the callback function is sending some text back to the browser.

You can test these two new routes by going to localhost:8080/api/home and localhost:8080/api/login.
