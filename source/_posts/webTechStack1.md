---
title: Web Development Technology Stack --- Part1
date: 2019-08-11 13:01:50
tags:
- 生活
---
# Web Server
## Concepts
### Proxy vs Reverse Proxy
Proxy:
![](/images/proxy.png)

<!--more-->
benefits:
anonymity
caching
blocking unwanted sites
geoFencing

Reverse Proxy:
![](/images/reverseProxy.png)

benefits:
loading balancing
caching
isolating internal traffic
logging
canary deployment

### Dynamic Contents vs Static Contents
Dynamic: may change per-request, like PHP
Static: keep same per-request, good for caching

## Apache vs Nginx
Apache:
1. multi-processing model
2. support dynamic contents
3. support directory level config, based on file system
4. support dynamically module loading


Nginx:
1. async event driven model, support large concurent connections
2. need external modules to support dynamic contents
3. URI based configuration, not support directory level config
4. not support dynamically module loading

Mixed:
Use Nginx for static content requesting and Apache for dymantic content rendering
