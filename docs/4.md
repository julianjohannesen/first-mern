<!-- @format -->

[back to index](/README.md) | [prev](/docs/3.md) | [next](/docs/5.md)

# Step 4 - Connecting Express to MongoDB

Now that you've (1) created a pared-down server.js file with everything needed to start the Express server and display a page and (2) installed Mongo, you're ready to install the ORM that will enable Express to talk to Mongo. As was mentioned earlier, the ORM you'll be using is called Mongoose. 

Install the Mongoose package:

```
 npm i mongoose
```

With Mongoose installed, you're ready to connect the Express server to Mongo. Open server.js and replace the existing code with the code below. For the sake of clarity, we've removed the code comments from the previous steps and marked the new lines.

```js
// server.js

const express = require('express');
const mongoose = require('mongoose'); // <- THIS IS NEW

const app = express();

app.get('/', function (req, res) {
   res.send('Welcome to the home page.');
});

// START OF NEW STUFF

// A database named "first-mern" will be created when Express connects to it, if it doesn't already exist.
const mongo_uri = 'mongodb://localhost/first-mern';

// Mongoose's connect() method takes three arguments: the db's URI, some connection options, and a callback.
mongoose.connect(
    // The URI
    mongo_uri, 
    // The connection options (don't worry about these for now)
    {
        useNewUrlParser: true, 
        useUnifiedTopology: true
    }, 
    // The callback
    function (err) {
        // If an error exists, throw it
        if (err) { throw err; }
        // Otherwise log the successful connection
        else { console.log(`Connected to ${mongo_uri}`); }
    }
);

// END OF NEW STUFF

app.listen(process.env.PORT || 8080);
```

Now stop the Express server and restart it. In the shell running your server, you should see a message that reads:

```
Connected to mongodb://localhost/first-mern
```

Note that when you passed the URI ending in "first-mern" into connect(), Mongoose recognized that there was no database by that name and created it for you. It isn't necessary to create the database ahead of time.
