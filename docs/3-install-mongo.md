<!-- @format -->

[back to index](/README.md) | [prev](/docs/2.md) | [next](/docs/4.md)

# Step 3 - Install MongoDB

So far, you’ve created a boilerplate React project and confirmed that it can successfully serve the home page on port 3000. You’ve also installed the Express library and created a very simple server script to confirm that Express is serving a welcome message on port 8080.

Here’s a quick overview of what you need to do next. First, you need to install a database that you’ll use to store the users’ account information, i.e. their email address and password. When a user submits the registration form or the login form (neither of which we've created yet) from their browser, the browser will send an HTTP POST request to the Express server. Express uses another piece of software called an ORM to talk to the database. If the user is creating a new account, the ORM will tell the database to save that new information to a new document (aka record). If the user is just logging in, the ORM will query the database to make sure that a document with a matching email and password combination exists.

The database you’re using is MongoDB. The ORM is Mongoose.

## Is MongoDB Installed?

First, let's check to see if MongoDB is already installed on your system.

NOTE: “mongod” is the name of the MongoDB server application. “mongo” is the name of the MongoDB shell application. The mongo shell can be used to tell mongod to do things from the command line.

On Mac and Linux, if mongod is properly installed and the path is set correctly, then you should be able to run:

```
 mongod --version
```

> **Question for Ben** - if mongod was installed without using a package manager, or if the path is NOT set correctly, how else do you find out if mongod is installed?

This will tell you what version of mongod is running. Don't worry if you have an older version installed. Upgrading is complicated and unnecessary for whatyouwant to do.

On Windows you need to search for mongod.exe, which is usually in C:\Program Files\MongoDB.

## Installing MongoDB

If you discover that mongod is not yet installed onthesystem, the next thing you need to do is ...

> **Note for Ben** - I was thinking about recommending that people upgrade if they have an old install, but the process is incredibly complicated and unnecessary in terms of building the app. I want to avoid forcing the read to go through unnecessary steps if possible. Thoughts?

## Start MongoDB

Remember that mongod is the name of the MongoDB process. To check to see whether mongod is already running on Mac or Linux, run:

> **Note for Ben** I'm conflicted about mentioning systemctl. I'd prefer to use something that's going to work for everyone and to skip anything that would require the reader to go through additional steps that aren't essential to building the app. Am I correct in thinking that ps -C mongod is going to work on any Mac or Linux distro?

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

Later on,you'llconnect the Express server to a Mongo database. Once that's done, whenever you want to start the Express server, you'll need to make sure that mongo is running beforehand, otherwise you'll get an error when Express attempts to connect.

## Using the MongoDB CLI

Some quick terminology beforeyouget into using the MongoDB CLI - if you have any familiarity with SQL databases, you'll be familiar with terms like database, table, record, row, and column. MongoDB is a NoSQL database, so the terms for these things are a bit different. A table is called a collection. A record or row is called a document. Columns are referred to only as fields. 

With that out of the way, once mongod is running, you can start the CLI in a new terminal with:

```
mongo
```

To show all available local databases, use:

```
show dbs
```

Once the first-mern database has been created, when using the mongo CLI, you may need to tell the CLI which database you want to use.

```
use first-mern
```

To see all collections inthecurrent database use:

```
show collections
```

db.users.find( {} )

Note that {} is an empty argument that should return all entries within users object.

This is long overdue, but Last Week I Learned (LWIL): (See my new thread for a full list of items.)

-   On Linux, [MongoDB](https://www.mongodb.com/) database software requires a [manual install on Fedora distros](https://fedoramagazine.org/how-to-get-mongodb-server-on-fedora/), even though it was previously included. Be prepared to create a repository file in \*\*<code>/etc/yum.repos.d/mongodb.repo. </code>Yum.repos.d</strong> is one of the default directories used by the Fedora’s system package manager (<strong>dnf</strong> and <strong>yum</strong>) to find source code and install it for us.youalso need to also manually set up a directory in the root of the system called <strong>/Data/db</strong> directory that Mongo uses as a convention to store all databasesyoucreate locally. This extra work upfront guarantees ease of use later whenyouwant to install and updatetheMongoDB packages when running sudo dnf install mongo. Unfortunately, this requires use to run Mongo with superuser privileges, and I haven’t gotten around to fixing this yet, although it’s likelyyoucan simply change the permissions of the <strong>/Data</strong> directory to be assigned totheuser, and that would be sufficient.
-   Afterthesession, I looked into why MongoDB wasn’t included in Fedora and required as much work as it did to install. One of the strengths of Fedora is how many dev tools and products are pre-installed on their OS or easily available with their DNF package manager. On principle, Fedora only pre-installs software that they consider a [valid open source license](https://opensource.org/osd)--more or less the same approved by the [Freedom Software Foundation](https://www.fsf.org/about/what-is-free-software) or they consider compatible with their GPLv3/AGPLv3 licenses. MongoDB switched to their own license based on the GPLv3 called The Server Side Public License (SSPL) (FAQ linked [here](https://www.mongodb.com/licensing/server-side-public-license/faq)), in an attempt to stop companies like Amazon from using their products as [Software as a Service](https://www.infoworld.com/article/3226386/what-is-saas-software-as-a-service-defined.html) (SaaS) for free. This is in line with licensing changes by [Redis](https://redislabs.com/blog/redis-labs-modules-license-changes/) and other companies. [The Fedora Project determined MongoDB’s license had enough issues to remove it from their supported repositories](https://lists.fedoraproject.org/archives/list/legal@lists.fedoraproject.org/thread/IQIOBOGWJ247JGKX2WD6N27TZNZZNM6C/).
-   MongoDB itself is centralized: any DB started with Mongo on my machine will be accessible or switch-able through the console, once the Mongo daemon is running and I type in “<strong>mongo</strong>” to the command line to start it’s interactive terminal (written in JavaScript, conveniently).
-   Once logged into the interactive console,youcan use the “show-db” command to list all available databases Mongo can see onthelocal machine.youcan then switch tothedesired database using the “<strong>use &lt;databaseNameHere></strong>” command and argument.
-   To effectively use a [MERN](https://www.educative.io/edpresso/what-is-mern-stack) stackyoumust at least have three servers running:
    -   The Mongo daemon,
    -   the Express.js backend server/application (Node),
    -   andtheReact.js frontend application.
-   [Mongoose](https://mongoosejs.com/) is an Object Relational Mapper that lets us designtheschema and enter data programmatically throughthefrontend and backend code, rather than needing to manipulate MongoDB, directly. I liked how straightforward and simple their approach was, using simple functions to do most of the heavy lifting for the request and response cycle.
