---
tags:
  - Studies
  - Acronym
  - Networking
  - Programming
  - CCNA
  - Theory
---
REST APIs are not one specific [[APIs|API]], rather it describes ==a set of rules== about how this type of APIs should work. REST stands for Representation State Transfer.

Web browsers use [[HTTP and HTTPS]] to request (GET) a web page. If successfully requested (HTTP status code 200), web servers respond to GET requests with an [[HTTP and HTTPS|HTTP]] coded web page.

Simply stated, a REST API is an [[APIs|API]] that works on top of the [[HTTP and HTTPS|HTTP]] protocol. It defines a set of functions developers can use to perform requests and receive responses via [[HTTP and HTTPS|HTTP]] protocol such as GET and POST.

For details of the specific types of RESTful API requests, see [[CRUD]].
## RESTful API Architecture

## Client-Server

RESTful APIs use a client-server architecture. The client uses [[APIs|API]] calls (usually in the form of HTTP requests) to access resources on the server. The separation between the client and the server means that they ==can both change and evolve independently== of each other.

![[Pasted image 20231213114644.png#invert]]
## Stateless Architecture

RESTful API exchanges are ==stateless== which means that each [[APIs|API]] exchange is a separate event which is independent of all past exchanges between the client and the server. This means that the ==server does not store any information about previous requests==.

If authentication is required to enable access to the server, the stateless architecture means that this authentication must be carried out as a part of each request to it.

It is important to note that although REST API requests are stateless, HTTP uses [[TCP]] (at layer four of [[The OSI Model]]) and this layer is stateful. So at the Application layer, the [[APIs|API]] request is stateless, but ==other layers are still independent and can still be stateful==.

## Cacheable or Non-Cacheable

REST APIs must support the caching of data or storing it for later. This doesn't mean to say that *all* resources must be cached, but cacheable resources *must* be declared as cacheable.

## Summary

Although this is all there is to know for the CCNA, there is a lot more to it. Refer to [Free CCNA | REST APIs | Day 61 | CCNA 200-301 Complete Course - YouTube](https://youtu.be/Luei0p-2h10?si=KT14dOPB8VM_A6N) for more information.