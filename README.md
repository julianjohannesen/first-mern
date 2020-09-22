# Building Your First MERN App
By [Julian Johannesen](https://github.com/julianjohannesen) and [Ben Davis](https://twitter.com/bengineerdavis) 

### Index

* **[Goal](#Goal)**
* **[Background](#Background)**
* **[Links](#Links)**
* **[Overview](#Overview)**
    * [Step 1 Create the React Project](/docs/1.md) 
    * [Step 2 Set Up Express Server](/docs/2.md)
    * [Step 3 Install MongoDB](/docs/3.md)
    * [Step 4 Connect to MongoDB](/docs/4.md)
    * [Step 5 Add Routes in React](/docs/5.md)
    * [Step 6 Add Routes in Express](/docs/6.md)
    * [Step 7 Request Data](/docs/7.md)

## Goal

**Create a simple web app using the MERN stack and explore basic authentication.**

In this tutorial you'll become familiar with how to build web applications that depend on APIs to provide them with services like user authentication and authorization. You’ll be building a very simple website that will allow a user to register an account, log in and log out securely. The stack you’ll be using is the popular MERN stack, which comprises MongoDB, Express.js, React.js, and Node.js. You’ll be using several other technologies along the way, but those four are the biggies.

This tutorial is not intended to teach everything you need to know to deploy an application. Our intention is to cover only what you need to build a working application.

## Background

This is a tutorial for beginners, so don’t worry if you don’t have very much familiarity with one or more of the technologies we just mentioned. We’ve created a list of resources that should help.

Some of the most import concepts to grasp are:
- how clients and servers interact by exchanging HTTP messages
- the role that React plays as a front-end library
- the role that Node and Express play on the back-end to serve the API
- the difference between client-side routing and traditional server-side routing

## Links
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

## Overview

1. You’ll begin by setting up the React project and ensuring that you’re able to use a development server to serve some React boilerplate to the browser.
2. Next, you’ll set up a very simple Express server and ensure that you can use it to serve a simple page to the browser.
3. Then you’ll install MongoDB, and make sure that you're able to start it, and interact with it via the Mongo shell.
4. Using Express and MongoDB together is much easier with an ORM, so you’ll install Mongoose. After making some edits to the Express server script, you’ll ensure that the Express server can connect to MongoDB.
5. At this point, you’ll jump back to the front-end and use React Router to set up some client-side routing. You’ll also create a couple of simple React components for the routes to render.
6. Returning to the Express server you’ll create a couple of routes that the front-end will eventually use to fetch data.
7. asdf

## During Development

Unless you plan to complete the tutorial in one sitting, there are a few things that you'll need to remember to do when you come back to this project after being away. Failing to take the following steps will cause errors that will annoy you to know end:

1. `Start the React dev server (served on port 3000) and test the navigation links to make sure they're both working.`
2. `Start Mongo, if it isn't already running (default port). If you don't start Mongo before starting the Express server, you'll get an error.`
3. `Start the Express server (served on port 8080)`
4. `Use curl (or Postman) to send a POST request to Express to make sure it's working`
5. `Inspect the database with the mongo CLI and query a record to make sure everything is working as it should`

## GLOSSARY

**JSON** stands for JavaScript Object Notation. JSON uses key:value pairs in which the key is a string and the value can be any data type. It’s very similar to JavaScript’s syntax for objects.

**JWT** stands for JSON Web Token. JWTs are a way of transmitting authentication and authorization information from and to a server without the server needing to store a session ID.

**ORM** which stands Object Relation Management is a way of bridging the gap between object oriented programming languages and (usually) relational databases.


NOTES -

- Talk about the difference between a site and service. The React app is a site that's served from a server, but requires no interaction with the server that's hosting it. The Express server is not a "site", although Express can certainly serve HTML pages. In this tutorial, the Express server is serving an API. The API is a service. Client apps can send data to the API and request data from the API.