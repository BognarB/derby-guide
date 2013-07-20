[npm]: http://en.wikipedia.org/wiki/Npm_(software)

derby-guide
===========

A guide to getting going with Derby.js from scratch. If you are interested in derby.js and want to learn how it works read on.

Notes: 

  1. This guide is written for a mac but it shouldn't be too hard for Windows and *nix users to tranlate on the fly. (If you are up for it you could even fork the guide, update it for your OS as you go and send us a pull request.)
  1. You may need to use sudo for some of the commands below. (Again would be great if someone could run though the and updare the guide with where they have needed sudo.)

The Basics
==========

### Why use Derby?
To build fast, realtime, colaborative, web applications like google docs.

### What is Derby?

* A web application programming framework for node.js
* A command line tool which can be used to create a starter Derby project.
* A node.js module that is included in a Derby project.

### How to use Derby?

Read on…


Part 1 - Setup Your Machine
===========================

First of all you are going to need to install a few tools.

### Homebrew

Homebrew is a great way to install software on a Mac and we will use it to install some of the software needed by Derby. Read more about homebrew [here](http://mxcl.github.io/homebrew/) and download and install homebrew with:

```bash
ruby -e "$(curl -fsSL https://raw.github.com/mxcl/homebrew/go)"
````


### node.js, npm, redis, mongodb.

Derby is built on node.js. npm is the node package manager (but don't tell anyone that is what it [stands for](https://npmjs.org/doc/faq.html#If-npm-is-an-acronym-why-is-it-never-capitalized). By default Derby uses a combination of database awsomeness from redis and mongodb.

Install all three with:

```bash
brew install nodejs
brew install redis
brew install mongo
```

### Git

[Git](http://git-scm.com/) is the fast, effience and clever version control system and you will use it to "clone" Derby examples from [github](https://github.com/). If you havn't discovered github yet you've been missing out! A huge number of open source projects manage their source code on github, including many node.js projects ike Derby and it's related libraries (more on those later).

Download and install git from [git-scm.com/downloads](http://git-scm.com/downloads).

Set your self up with a github account by following these instuctions [here](https://help.github.com/articles/set-up-git).

### Coffee

Coffee script compiles into javascript. Derby uses coffeescript internally, as do many of the Derby examples so install it now (and you might find learning the cofeescript syntax a useful investment too, see [coffeescript.org](http://coffeescript.org/)).

```bash
npm install -g coffee
```

### Derby
Finally your ready for Derby. This will install the commandline tool `derby` which is used to create Derby projecs from a template. 

```bash
npm install -g derbyjs
```

Part 2 - Run an Example
=======================

### Start mongo and redis
You can use a separate terminal for each if you like. In one run the redis server:
```bash
redis-server
```

In the other run the mongo server:
```bash
mongod
```

They will both run on default ports and log information to the terminal.

### Start an Example
Clone the examples from github and run one, in this case chat:
```bash
git clone 
cd derby-examples/chat 
coffee server.coffee  
```

You will see somthing like:
```
Master pid  33960
33963 listening. Go to: http://localhost:3000/
``` 

So go to [http://localhost:3000/](http://localhost:3000/) and take a look. It's a basic but functional chat room where you can change your name and send messages. If you connect to this URL from two different browsers (or one normal window and one private / ignognito window) you and see how it works with two users. Notice when one user sends a message it autmatically apears in the seond user's window. Near real time updates like this in web apps, without refreshing the page manualy, are often taken for granted but they need some extra care to get right - which is what Derby does for you.


### So how does Derby work?

Here's a short description. A longer explanation and guide to building your own app is below but it's good to understand the basics first. When you run a Derby app (e.g. with the `coffee server.coffee` command you ran above) you get:

1. __A Derby Server__ - running in node.js, and able to serve a ...
2. __A Derby Client__ - that runs in a web browser and connects back to the Server to ensure ...
3. __Synchonised Data__ - accross all connected clients and ...
4. __Persisisted Data__ - in the server side database.


Derby achives this by combining a number of techniques and librbaries. They key ones are:

1. 
2. 
3. 


### A Poke Arround in the Code



### A Poke Arround in the Databases
You can safely skip this section but if you are inquisitve you might want to see inside the databases. As you have probably reliased there are two - redis and mogodb.


#### Mongodb
Start the mongodb client with:
```bash
mongo
```

Find out the database name with:
```
show dbs
```
Mongo will respond with something like:
```
derby-chat  0.203125GB
```

In this case there is only one databse, so select it with `use <name>` where `<n>` is the database name.
```
use derby-chat
```

To list all the collections derby has created in your mongo database use:
```
show collections
```
Mongo will respond with something like:
```
chat
messages
sessions
system.indexes
users
```

To see the data in one of these collection use `db.<collection>.find()`, for example:
```
db.messages.find()`
```
Mongo will return each document in the collection. For example:
```
{ "room" : "lobby", "userId" : "7cab5aaa-b5b1-4f58-b233-f244777a816f", "comment" : "hello world!", "time" : 1374308274283, "id" : "d4bb0848-af17-4562-9266-f77ebe419154", "_type" : "http://sharejs.org/types/JSONv0", "_v" : 1, "_id" : "d4bb0848-af17-4562-9266-f77ebe419154" }
```

This shows some of the internals of how derby's databse engine, livedb, is storing data in mongo. You should also recogonise 

And finally...
```
exit
```

##### Just In Case...
... you ever want to clear down your database to a blank one you can use the mongo command `db.dropDatabase()`. BUT use with care and make sure you have the right database selected first!

#### Redis
Start the redis client with:
```bash
redis-cli
```

Find out the database id with:
```
INFO KEYSPACE
```
Redis will respond with something like:
```
# Keyspace
db1:keys=13,expires=8
```

In this case there is only one databse, so select it with `SELECT <n>` where `<n>` is the db number.
```
SELECT 1 
```

To list all the keys derby has created in your redis database use:
```
KEYS *
```

And finally...
```
EXIT
```

##### Just In Case...
... you ever want to clear down your database to a blank one you can use the redis command `FLUSHDB`. BUT use with care and make sure you have the right database selected first!


### Godbox
All this looking arround inside the databses is a bit low level. Godbox provides a broswer interface to the Derby database. To get started with godbox clone it from github. Before you start it you will need to know the redis db number and the mongo database name / collection to point it at.

You can find these things by poking arround in the databse (see above) or poking arround in the code. 



```bash
git clone git@github.com:share/godbox.git
cd godbox
coffee server.coffee  
```


How To Build A Derby App
========================

Todo

