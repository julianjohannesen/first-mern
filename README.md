# Building Your First MERN App

$ git commit -m "Refactor usability tests.
>
>
Co-authored-by: name <name@example.com>
Co-authored-by: another-name <another-name@example.com>"

### Index

* **[Goal]()**
* **[Background]()**
* **[Links]()**
* **[Overview]()**
* **Tutorial Steps**
    * [Step 1 Use CRA to create project]() 
    * [Step 2 Setup Express Server]()
    * [Step 3 Install MongoDB]()
    * [Step 4 Connecting Express to MongoDB]()
    * [Step 5 Adding Routes in React]()
    * [Step 6 Adding Routes in Express]()
    * [Step 7 Requesting Data]()

### Goal

**Create a twitter-like web app using the MERN stack and explore basic authentication.**

[jjeadon]() and [bengineerdavis](https://twitter.com/bengineerdavis) 

In this tutorial we'll become familiar with how to build web applications that depend on APIs to provide them with services like user authentication and authorization. We’ll be building a very simple website that will allow a user to register an account, log in and log out securely. The stack we’ll be using is the popular MERN stack, which comprises MongoDB, Express.js, React.js, and Node.js. We’ll be using several other technologies along the way, but those four are the biggies.

### Background

This is a tutorial for beginners, so don’t worry if you don’t have very much familiarity with one or more of the technologies we just mentioned. We’ve created a list of resources that should help.

The most import concepts to grasp are how clients and servers interact by exchanging HTTP messages; the role that React plays as a front-end library; the role that Node and Express play on the back-end to serve our API; and the difference between client-side routing and traditional server-side routing.

### Links
The links below will take you to **short videos** about each subject. You certainly don’t need to watch all of them, or to watch them in their entirety, but if any of these topics look unfamiliar, the video will provide you with a quick introduction.

1. [The client server model](https://www.youtube.com/watch?v=L5BlpPU_muY) (6 min)
2. [HTTP](https://www.youtube.com/watch?v=eesqK59rhGA) (9 min), [HTTP methods](https://www.youtube.com/watch?v=guYMSP7JVTA) (5 min) ([more](https://www.youtube.com/watch?v=iYM2zFP3Zn0))
3. [APIs and REST](https://www.youtube.com/watch?v=FOZtRzY5x8E) (15 min)
4. [Server Side Routing and Client Side Routing](https://www.youtube.com/watch?v=ofCoqejWohA&t=79s) (4 min)
5. [Databases, SQL vs. NoSQL databases](https://www.youtube.com/watch?v=Tk1t3WKK-ZY) (4 min) ([more](https://www.youtube.com/watch?v=ZS_kXvOeQ5Y) 22 min), [JSON](https://www.youtube.com/watch?v=iiADhChRriM) (10 min), and [Mongo](https://www.youtube.com/watch?v=9JSG7Na2S4M) (9 min)
6. [ORM](https://www.youtube.com/watch?v=7E1M1W9o7PA) (5 min) and [Mongoose](https://www.youtube.com/watch?v=cVYQEvP-_PA) (14 min)
7. JavaScript and [Node.js](https://www.youtube.com/watch?v=uVwtVBpw7RQ) (4 min)
8. The [Express.js](https://www.youtube.com/watch?v=L6_CoHNSbwc) (6 min) framework for Node.js
9. The [React.js](https://www.youtube.com/watch?v=JPT3bFIwJYA) front-end library (5 min), Create React App
10. [Authentication and Authorization](https://www.youtube.com/watch?v=927KdwZZoU0) (5 min)
11. JSON Web Tokens [Part 1](https://www.youtube.com/watch?v=soGRyl9ztjI) (15 min) [Part 2](https://www.youtube.com/watch?v=_XbXkVdoG_0) (18 min)

If you’d like to go deeper into any of the above topics, these articles are a great place to start:

1. “[What is Server Side Programming](https://developer.mozilla.org/en-US/docs/Learn/Server-side/First_steps/Introduction)” on MDN
2. “[Web Servers and HTTP - A Primer](https://developer.mozilla.org/en-US/docs/Learn/Server-side/First_steps/Client-Server_overview)” on MDN
3. “[Server Side Web Frameworks](https://developer.mozilla.org/en-US/docs/Learn/Server-side/First_steps/Web_frameworks)” on MDN
4. “[Overview of HTTP](https://developer.mozilla.org/en-US/docs/Web/HTTP/Overview)” on MDN
5. “[Express/Node Introduction](https://developer.mozilla.org/en-US/docs/Learn/Server-side/Express_Nodejs/Introduction)” on MDN
6. “[An Introduction to Mongoose for MongoDB](https://www.freecodecamp.org/news/introduction-to-mongoose-for-mongodb-d2a7aa593c57/#:~:text=Mongoose%20is%20an%20Object%20Data,of%20those%20objects%20in%20MongoDB.)” by Nick Karnik
7. “[Getting Started with React](https://developer.mozilla.org/en-US/docs/Learn/Tools_and_testing/Client-side_JavaScript_frameworks/React_getting_started)” on MDN
8. “[Token Authentication: The Secret to Scalable User Management”](https://stormpath.com/blog/token-authentication-scalable-user-mgmt) by Lindsay Brunner

### Overview

1. We’ll begin by setting up our React project and ensuring that we’re able to use a development server to serve some React boilerplate to our browser.
2. Next, we’ll set up a very simple Express server and ensure that we can use it to serve a simple page to our browser.
3. Then we’ll install MongoDB, and make sure that we’re able to start it, and interact with it via the Mongo shell.
4. Using Express and MongoDB together is much easier with an ORM, so we’ll install Mongoose. After making some edits to our Express server script, we’ll ensure that our Express server can connect to MongoDB.
5. At this point, we’ll jump back to the front-end and use React Router to set up some client-side routing. We’ll also create a couple of simple React components for our routes to render.
6. Returning to the back-end we’ll create a couple of routes that our front-end will eventually use to fetch data.
7. asdf

### Step One - Use Create React App to create a boilerplate React project

You’ll need to make sure you have a relatively recent version of Node.js installed on your machine. The most recent version as of this writing is 14.x.

Node will automatically install NPM - the Node Package Manager. You can then use NPM to install all of the other libraries talked about below. There are many package managers. Another popular one is Yarn. We’re going to stick to NPM.

With Node and NPM installed, navigate via the command line to the directory within which you want to put the project. Next run the following commands in sequence, replacing "my-app" with the name of your application:

```
 npx create-react-app my-app
 cd my-app
 code .
```

That will install almost all of the directories and files you’ll need. **The installation will take a while** and you’ll see lots of information printed to your screen. Don’t worry about any warnings. The last line tells your system to open the current directory in VS Code. You can substitute another code editor if you like.

From within your code editor, the file structure should look like this:

```
 node_modules/
 public/
 src/
 .gitignore
 package.json
 package-lock.json
 README.md
```

The directories you’ll work with most are the top level and the src/ directory. Get familiar with the structure and files. And don’t worry if this is all new to you.

Next, from the command line, run:

```
 npm start
```

This will start a development server that will serve your React installation. It will be served to port 3000 by default. Open your browser and open localhost:3000. The site should load with some boilerplate.

NOTE: The NPM start script can be found in package.json. You can create other scripts in the same place. Other scripts will require a slightly different syntax to start. Use `npm run myScript`.

These are the scripts that come with the Create React App installation.

```js
"scripts": {
   "start": "react-scripts start",
   "build": "react-scripts build",
   "test": "react-scripts test",
   "eject": "react-scripts eject",
 },
```

If you'd like to learn more about those scripts, we suggest reading the README.md file.

### Step 2 - Set up the Express server

Now run:

```
 npm i express
```

This will install the Express package. You’ll see some more information printed to your screen.

Next, create a new file at the top level (i.e. as a sibling of package.json, README.md, etc.) called server.js.

Open server.js and paste in the following stripped down Express server script:

```js
// server.js

// Use Node's require method to import the Express package
const express = require("express");

// Instantiate an instance of Express
const app = express();

// Create a route that handles a request for the homepage. The callback is our handler. We pass in the HTTP request and response objects and use Express's send() method to send a line of text back to the browser.
app.get("/", function (req, res) {
	res.send("Welcome to the homepage.");
});

// Tell Express to listen to port 8080
app.listen(process.env.PORT || 8080);
```

Next, open package.json and at the object's top level, the same level as things like “name” and “version” insert the line

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

You can now start the Express server with:

```
 npm run server
```

Open your browser and navigate to localhost:8080. The page should load, and you should see the “Welcome to the homepage” message.

### Step 3 - Install MongoDB

So far, we’ve created a boilerplate React project and confirmed that it can successfully serve our React front-end on port 3000. We’ve also installed the Express package and created a very simple server script to confirm that Express is serving our welcome message on port 8080.

Here’s a quick overview of what we need to do next. We need to install a database that we’ll use to store our users’ account information, i.e. their email address and password. When a user submits the create-an-account form or the login form from their browser, the browser will send an HTTP POST request to our Express server. Express uses another piece of software called an ORM to talk to our database. If the user is creating a new account, our ORM will tell our database to save that new information to a new record. If the user is just logging in, our ORM will query the database to make sure that a record with a matching email and password combination exists.

The database we’re using is MongoDB. The ORM that will talk to MongoDB is called Mongoose.

First, check to see if MongoDB is installed on your system. This is complicated by the fact that Windows, Mac, and different versions of Linux do things differently.

NOTE: “mongod” is the name of the MongoDB server application. “mongo” is the name of the MongoDB shell application. The mongo shell can be used to tell mongod to do things from the command line.

On Mac and Linux, if mongod is properly installed and the path is set correctly, then you should be able to run:

```
 mongod --version
```

[ **Question for Ben** - if mongod was installed without using a package manager, or if the path is NOT set correctly, how else do you find out if mongod is installed?  ]

This will tell you what version of mongod is running.

On Windows you need to search for mongod.exe, which is usually in C:\Program Files\*\*MongoDB\*\*\.

Next, if you have an older version of MongoDB, it might be a good idea to upgrade to 4.4.0, the most recent stable release as of this writing. Use this command on Mac and Linux.

[  **Question for Ben** - what's the best way to upgrade to the most recent version that is agnostic as regards OS, at least for mac and linux, without getting too complicated? ]

To check to see whether mongod is already running on Mac or Linux, run: 

```
ps -C mongod
```

If mongod is running you should see a line that looks like this:

```
PID  TTY   TIME    CMD
5253 pts/2 00:00:03 mongod
```

If it isn't, you can start mongod from the command line by running:

```
sudo mongod
```

LIkewise, you can start the mongo shell with:

```
mongo
```

-   `starting CLI session`
    -   `$ mongo`
-   `show all available local databases`
    -   `$ show dbs `
-   `switch to our database`
    -   `$ use react-auth `
-   `see all collections/groups in our current database`
    -   `$ show collections`
-   `Find specific user entries in our database`
    -   `$ db.users.find( {} ) `
    -   `{} is an empty argument that should return all entries within users object`

This is long overdue, but Last Week I Learned (LWIL): (See my new thread for a full list of items.)

-   On Linux, [MongoDB](https://www.mongodb.com/) database software requires a [manual install on Fedora distros](https://fedoramagazine.org/how-to-get-mongodb-server-on-fedora/), even though it was previously included. Be prepared to create a repository file in \*\*<code>/etc/yum.repos.d/mongodb.repo. </code>Yum.repos.d</strong> is one of the default directories used by the Fedora’s system package manager (<strong>dnf</strong> and <strong>yum</strong>) to find source code and install it for us. We also need to also manually set up a directory in the root of the system called <strong>/Data/db</strong> directory that Mongo uses as a convention to store all databases we create locally. This extra work upfront guarantees ease of use later when we want to install and update our MongoDB packages when running sudo dnf install mongo. Unfortunately, this requires use to run Mongo with superuser privileges, and I haven’t gotten around to fixing this yet, although it’s likely we can simply change the permissions of the <strong>/Data</strong> directory to be assigned to our user, and that would be sufficient.
-   After our session, I looked into why MongoDB wasn’t included in Fedora and required as much work as it did to install. One of the strengths of Fedora is how many dev tools and products are pre-installed on their OS or easily available with their DNF package manager. On principle, Fedora only pre-installs software that they consider a [valid open source license](https://opensource.org/osd)--more or less the same approved by the [Freedom Software Foundation](https://www.fsf.org/about/what-is-free-software) or they consider compatible with their GPLv3/AGPLv3 licenses. MongoDB switched to their own license based on the GPLv3 called The Server Side Public License (SSPL) (FAQ linked [here](https://www.mongodb.com/licensing/server-side-public-license/faq)), in an attempt to stop companies like Amazon from using their products as [Software as a Service](https://www.infoworld.com/article/3226386/what-is-saas-software-as-a-service-defined.html) (SaaS) for free. This is in line with licensing changes by [Redis](https://redislabs.com/blog/redis-labs-modules-license-changes/) and other companies. [The Fedora Project determined MongoDB’s license had enough issues to remove it from their supported repositories](https://lists.fedoraproject.org/archives/list/legal@lists.fedoraproject.org/thread/IQIOBOGWJ247JGKX2WD6N27TZNZZNM6C/).
-   MongoDB itself is centralized: any DB started with Mongo on my machine will be accessible or switch-able through the console, once the Mongo daemon is running and I type in “<strong>mongo</strong>” to the command line to start it’s interactive terminal (written in JavaScript, conveniently).
-   Once logged into the interactive console, we can use the “show-db” command to list all available databases Mongo can see on our local machine. We can then switch to our desired database using the “<strong>use &lt;databaseNameHere></strong>” command and argument.
-   To effectively use a [MERN](https://www.educative.io/edpresso/what-is-mern-stack) stack we must at least have three servers running:
    -   The Mongo daemon,
    -   the Express.js backend server/application (Node),
    -   and our React.js frontend application.
-   [Mongoose](https://mongoosejs.com/) is an Object Relational Mapper that lets us design our schema and enter data programmatically through our frontend and backend code, rather than needing to manipulate MongoDB, directly. I liked how straightforward and simple their approach was, using simple functions to do most of the heavy lifting for the request and response cycle.

### Step 4 - Connecting our Express app to MongoDB

In step 2, we created a paired down server.js file with everything we needed to start the server and display a homepage.

Next, we need to install the Mongoose package. Run:

```
 npm i mongoose
```

Now we need to go back to server.js and write the code that will allow Express and Mongoose to talk to Mongo. Here’s the complete server.js script. We’ve marked the new lines.

```js
// server.js

// Use Node's require method to import the Express package
const express = require('express');
// Require Mongoose
const mongoose = require('mongoose'); // <- THIS IS NEW

// Instantiate an instance of Express
const app = express();

// Create a route that handles a request for the homepage. The callback is our handler. We pass in the HTTP request and response objects and use Express's send() method to send a line of text back to the browser.
app.get('/', function (req, res) {
   res.send('Welcome to the homepage.');
});

// THIS IS NEW

// "first-mern" is the name we're giving our db. It will be created when we connect to it, if it doesn't already exist.
const mongo_uri = 'mongodb://localhost/first-mern';

// Mongoose's connect() method takes three arguments: our db's URI, some connection options, and a callback. Don't worry about the connection options. The callback will catch any connection errors or log a success message.
mongoose.connect(mongo_uri, {useNewUrlParser: true, useUnifiedTopology: true}, function (err) {
   if (err) {
       throw err;
   } else {
       console.log(`Successfully connected to ${mongo_uri}`);
   }
});

// END OF NEW STUFF

// Tell Express to listen to port 8080
app.listen(process.env.PORT || 8080);
```

Now stop the Express server and restart it. In the shell running your server, you should see a message that reads:

```
Successfully connected to mongodb://localhost/first-mern
```

Note that when you passed the URI ending in "first-mern" into connect(), Mongoose recognized that there was no database by that name and created it for you. You can use the Mongo shell to inspect that database with:



### Step 5 - Adding routes to React

Next, we need to add a couple of routes to our React code. Don’t worry if you don’t know much about React or front-end routing. We’re not going to dwell on React. We need just enough code at this point to navigate to a couple of different pages.

First, we’ll install the browser version of a popular routing library called React Router.

```
 npm i react-router-dom
```

Now, open src/App.js.

One of the first things you may notice is that React uses JavaScript’s native module API. That means that modules are imported like this:

```js
import React from 'react';
import logo from './logo.svg';
import './App.css';
```

And exported like this:

```js
export default App;
```

We’re making a note of it here, because we were just looking at a different way to import and export modules in Node.js that used Node’s require() method.

Delete everything in App.js and copy and paste in the following code.

```js
// App.js

import React from 'react';

// Import the methods that we need from 'react-router-dom'
import {BrowserRouter as Router, Switch, Route, Link} from 'react-router-dom';

function App() {
   return (
    <Router>
        <div className="App">
            <Link to="/">Home</Link>
            <Link to="/secret">Secret</Link>
            <Switch>
                <Route exact path="/">
                    <Home />
                </Route>
                <Route exact path="/secret">
                    <Secret />
                </Route>
            </Switch>
        </div>
    </Router>
   );
}

function Home() {
   return <h2>You're on the Homepage!</h2>;
}

function Secret() {
   return <h2>You're on the Secret Page!</h2>;
}

export default App;
```

Note that we’ve added routing to a Home and Secret component, which we defined below App, we can double check that the front-end of our app is still functioning.

### Step 6 - Adding more routes to our Express server

The Home and Secret components that we created on the front-end will eventually fetch some data from our Express server. That means that we need to return to server.js and add two more routes just below the one route we’ve already defined. Note that both of these routes start with “/api/”. Also note that the callback function is sending some text back to the browser.

```
// Route to homepage info
app.get('/api/home', function (req, res) {
   res.send('Welcome!');
});

// Route to secret info
app.get('/api/secret', function (req, res) {
   res.send('The password is potato');
});
```

You can test these two new routes by going to localhost:8080/api/home and localhost:8080/api/secret.

### Step 7 - Requesting data from our Express server

Remember that the ultimate goal is to create a site where users can create a new account and log in and out. What we’ve done so far is to create a front-end and a back-end. We’ve connected our back-end to a database. However, our front-end still doesn’t talk to our back-end. Nor have we attempted to create, read, update, or delete any records in our database. Eventually we want our front-end to be able to request that the back-end create and retrieve records to/from our database and send them back to the front-end.

```
When you come back to this project after being away, remember to:

```

1. `Start the React dev server (port 3000)`
2. `Start Mongo, if it isn't already running (default port). If you don't start Mongo before starting the Express server, you'll get an error.`
3. `Start the Express server (port 8080)`
4. `Use curl (or Postman) to send a POST request to Express to make sure it's working`
5. `Inspect Mongo with Mongo shell and query a record to make sure it's there`

```
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

### GLOSSARY

**JSON** stands for JavaScript Object Notation. JSON uses key:value pairs in which the key is a string and the value can be any data type. It’s very similar to JavaScript’s syntax for objects.

**JWT** stands for JSON Web Token. JWTs are a way of transmitting authentication and authorization information from and to a server without the server needing to store a session ID.

**ORM** which stands Object Relation Management is a way of bridging the gap between object oriented programming languages and (usually) relational databases.
