[back to index](/README.md) | [prev](/docs/6.md) | [next](/docs/8.md)

# Step 7 - React Routing Part 2 - Requesting Data from the API

Remember that your ultimate goal is to create a site where users can create a new account and log in and out. What you’ve done so far is to (1) build a React front-end with some routing and a couple of simple components, (2) build an Express server with a couple of routes that will serve an API with which the React front-end will eventually communicate.

The Log In component you wrote in step 3 renders a line of text on the page whenever a user navigates to the /log-in route. That isn't very useful. What you want it to do is render a form into which a user can type their username and password. When the user hits submit, the form should call a submit handler that will send an HTTP POST request containing the form data to the API. Solving this problem will require work on both the front-end/client-side and back-end/server-side. On the front-end, you need to rewrite your Log In component to render the log in form. You also need to write the submit handler that will send the HTTP POST request to the API. On the back-end, you need to write route handlers that will receive and process the request. 

In this step, you'll re-write the Log In component to render the log in form. In the next step, you'll write the submit handler that will send the form data to the API.


 
Next we're going to install a ORM called Mongoose. Mongoose will help us talk to the Mongo database. Using Mongoose you can quickly accomplish what would otherwise be much more verbose, tedious, and repetitive tasks.

```
npm i mongoose
```


