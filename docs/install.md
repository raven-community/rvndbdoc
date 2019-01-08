---
id: install
title: Run a node
sidebar_label: Run a node
---

In this section, we will take a look at how you can run your own RvnDB node.

> Note that you DO NOT have to run a node to use RvnDB. Just like how not everyone needs to run a Ravencoin full node, you do not need to have to run RvnDB full node.
> For most casual developers, it is recommended that you start by using the public API.

---

## Prerequisite

First you need the following:

1. **Ravencoin:** You must have a Ravencoin running on your computer.
2. **MongoDB:** You must have set up a MongoDB database on your computer.

### 1. Ravencoin

RvnDB sits on top of Ravencoin, therefore you need to have a Ravencoin node running.

Also, you need to configure your ravencoin node for RvnDB to work, such as:

- Higher RPC limit
- Zeromq broadcast setting
- RPC username and password setting

Here's an example ravencoin.conf file to get your Ravencoin node to work with RvnDB:

```
# location to store blockchain and other data.
datadir=/data/Ravencoin
dbcache=4000
# Must set txindex=1 so Ravencoin keeps the full index
txindex=1
​
# [rpc]
# Accept command line and JSON-RPC commands.
server=1
# Default Username and Password for JSON-RPC connections
# RvnDB uses these values by default, but if you can change the settings
# By setting the config.json file in RvnDB folder
rpcuser=root
rpcpassword=ravencoin
​
# If you want to allow remote JSON-RPC access
rpcallowip=0.0.0.0/0
# [wallet]
disablewallet=1
​
# [ZeroMQ]
# ZeroMQ messages power the realtime RvnDB crawler
# so it's important to set the endpoint
zmqpubhashtx=tcp://127.0.0.1:28332
zmqpubhashblock=tcp://127.0.0.1:28332
​
# RvnDB makes heavy use of JSON-RPC so it's set to a higher number
# But you can tweak this number as you want
rpcworkqueue=512
```

### 2. MongoDB

RvnDB is powered by MongoDB, so you need to have installed MongoDB already.

---

## Install RvnDB

Once you've configured all of the above, you can install RvnDB.

First, clone the repository:

```
$ git clone https://github.com/raven-community/rvnd.git
```

Install dependencies:

```
npm install
```

Then run:

```
npm start
```

---

## Configuration

You can also change the configuration by tweaking the `config.json` file.

---

