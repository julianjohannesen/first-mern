[back to index](/README.md) | [prev](/docs/6.md) | [next](/docs/8.md)

# Step 7 - Requesting data from the Express server

Remember that the ultimate goal is to create a site where users can create a new account and log in and out. What you’ve done so far is to (1) build a React front-end with some custom routing and a couple of simple components, (2) build an Express server with a couple of routes that will serve an API with which the React front-end will eventually communicate, and (3) connect the Express server to a database. But you have a long way to go. The React front-end doesn’t yet talk to the Express server. Nor have you a created, read, updated, or deleted any records in the database. Eventually you want the front-end to be able to request, via the API, that the Express server create and retrieve records from the database and send information back to the front-end.

Next we're going to install a ORM called Mongoose. Mongoose will help us talk to the Mongo database. Using Mongoose you can quickly accomplish what would otherwise be much more verbose, tedious, and repetitive tasks.

```
npm i mongoose
```


