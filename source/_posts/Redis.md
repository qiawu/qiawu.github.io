---
title: Redis Inside(1)
date: 2017-10-20 21:30:43
tags:
- 技术
- Open Source
- Redis
---
## Basic
Redis supports lots of data types:
1. string
2. list
3. set
4. hash (k-v map)
etc.
Examples:

## Single Machine Redis
1. Redis keeps a key-value db structure internally. Normally, it is stored in memory. But it also has persistence strategy:
    * RDB: store the compress the k-v db into disk
    * AOF: store change log of cmd
2. a single machine redis can operate multiple dbs. (in a distributed mode, a redis can only operate one db)
3. server logic:
    * handle IO event (client request) and time event. It is event driven.
    * Reactor pattern
    * Single thread

## Distributed Redis
1. Support Master-Slave mode. (Master will sync up its data with slave)
2. Use Sentinel will monitor Master health
3. Each node in the cluster will maitain the current cluster state: including some health tag, shard-to-slot mapping
4. Node(shard): responsible for a number of slots. Each node has only one db
    * key send to node A
    * node A check if the key is in its slots
    * if no, return the target node
    * if yes, execute the cmd (find the key's value or insert the k-v into its db)

## Other features
1. Lua
    * reduce network cost. We can do multiple cmds in the lua scripts so one request is only needed to do the same
    * atomic in a lua. No other cmds will be executed in the middle of lua
    * we can reuse the lua script in the client any time.
2. Pub-Sub
    * support simple regex pattern match to topics
    * If subscribers are not online, the message will lost

## Use cases
1. find top K hot XXXX in a website
2. find recent visited records
3. sanity check of a request (i.e., if the user id is marched with some fields)
4. statistic: i.e., count how many users are registered, how many visited, etc.