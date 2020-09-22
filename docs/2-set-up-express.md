[back to index](/README.md) | [prev](/docs/1.md) | [next](/docs/3.md)

# Step 2 - Set up the Express Server

The next step is to install Express, a minimal web framework built on top of Node.js. Express plays much the same role in the JavaScript ecosystem that Django does in Python, Rails does in Ruby, or Laravel does in PHP. 

```
 npm i express
```

You’ll see some more information printed to your screen.

Next, create a new file at the top level and name it server.js. This file should appear at the same level as package.json and README.md.

Open server.js and paste in the following pared-down Express server script:

```js
// server.js

// Use Node's require method to import the Express library
const express = require("express");

// Instantiate an instance of Express
const app = express();

// Create a route that handles HTTP GET requests for the site's root URL. app.get()'s first parameter is the route. The second is the route handler. Pass the route handler the HTTP request and response objects and use Express's send() method to send a line of text back to the browser. Different methods can be used to send  different types of data, for example, an HTML document or JSON.
app.get("/", function (req, res) {
	res.send("Welcome to the API home page.");
});

// Tell Express to listen to port 8080
app.listen(8080);
```

Next, open package.json and at the top level, the same level as “name” and “version,” insert the line:

```js
"proxy": "http://localhost:8080"
```

It's important that you don't accidentally insert that line within an object, e.g. don't accidentally insert it in "dependencies" or "scripts".

You’re almost ready to start the Express server, but first you need to install Nodemon. Nodemon is a package that will update your Express server when you make changes to any files. Using Nodemon, you won’t have to manually stop and restart the server every time you make a change.

```
 npm i nodemon
```

Now open package.json again and insert a new script in the scripts object:

```js
"server": "nodemon server.js --inspect --unhandled-rejections=strict"
```

Note that installing Nodemon was necessary to avoid stopping and restarting the Express server every time you make a change. This extra step was not necessary for the React development server. This feature is built into Create React App applications by default.

You can now start the Express server with:

```
 npm run server
```

Open your browser and in the address bar, type in localhost:8080. The page should load, and you should see the “Welcome to the home page” message. 

This may be a bit confusing. *Didn't I just use React to serve a different home page on port 3000?* Yes, you did. *So why am I serving two different home pages to two different ports?* Great question! For now, it suffices to say that the React front-end is the real front-end. The page you're serving from the Express server simply confirms that the server is working. Later on, the Express server will serve an API with which the React front-end will communicate.


