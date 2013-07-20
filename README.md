[npm]: http://en.wikipedia.org/wiki/Npm_(software)

derby-guide
===========

A guide to getting going with Derby.js from scratch. If you are interested in derby.js and want to learn how it works read on.

Note: 
1. This guide is written for a mac but it shouldn't be too hard for Windows and *nix users to tranlate on the fly. (If you are up for it you could even fork the guide, update it for your OS as you go and send us a pull request.)
2. You may need to use sudo for some of the commands below. (Again would be great if someone could run though the and updare the guide with where they have needed sudo.)


Part 1 - Setup Your Machine
===========================

First of all you are going to need to set up your machine. 

### Homebrew

Homebrew is a great way to install development software on a Mac. Read more [here](http://mxcl.github.io/homebrew/) Download and install homebrew with:

```bash
ruby -e "$(curl -fsSL https://raw.github.com/mxcl/homebrew/go)"
````


### node.js, npm, redis, mongodb.

Derby is built on node.js. npm is the node package manager (but don't tell anyone that is what it [stands for][https://npmjs.org/doc/faq.html#If-npm-is-an-acronym-why-is-it-never-capitalized]. Derby uses a combination of database awsomeness from redis and mongodb (to create the "livedb" which you will find out more about later on).

```bash
brew install nodejs
brew install redis
brew install mongo
```

### Git

[Git](http://git-scm.com/) is the fast, effience and clever version control system. If you havn't installed it already do so now - you will use it to "clone" Derby examples from [github](https://github.com/). If you havn't discovered github yet you've been missing out! A huge number of open source projects manage their source code on github, including many node.js projects ike Derby and it's related libraries (more on those later).

Download and install from [git-scm.com/downloads](http://git-scm.com/downloads).

### Coffee

Coffee script compiples into javascript. Derby uses coffeescript internally, as do many of the Derby examples so install it now (and you might find learning tohe cofeescript syntax worth it too, see [coffeescript.org](http://coffeescript.org/)).

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

### Start mongo and redid
You can use a separate terminal for each if you like.

In one run the redis server:
```bash
redis-server
```

In the other run the mongo server:
```bash
mongod
```

They will both run on default ports and output status / debug information to the terminal.

### Clone and Run!
Clone the examples from github and run one (in this case chat):
```bash
git clone 
cd derby-examples/chat 
coffee server.coffee  
```




Step 5 - clone godbox and start it up

git clone 
cd derby-examples/chat 
coffee server.coffee  

Use redis-cli

> INFO keyspace
# Keyspace
db1:keys=15,expires=8
db5:keys=17,expires=6
db11:keys=11,expires=4

tells you you have three redid databases numbered 1, 5 and 11 accordingly

> SELECT 1 

selects redis db1

> keys *

lists all the keys

## Introduction

### Why use Derby?

* To build fast, "live", wen applications like google docs.

### What is Derby?

* A web application programming framework for node.js
* A command line tool which can be used to create a starter Derby project.
* A node.js module, and there are a collection of related modules, that are included in a Derby project.

### How to use Derby?

Read on…

## Getting Started

### 

1. A Derby Server - which runs on node.js and serves ...
2. A Derby Client - a web application which runs in the browser and ...
3. Clients are kept in live sync with the Server and ...
4. The Server stores all data in a database.


