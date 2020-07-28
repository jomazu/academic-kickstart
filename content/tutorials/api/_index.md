---
# Course title, summary, and position.
linktitle: APIs 
summary: Application Programming Interfaces.
weight: 7

# Page metadata.
title: Overview
date: "2020-07-26T00:00:00Z"
lastmod: "2020-07-26T00:00:00Z"
draft: false  # Is this a draft? true/false
toc: true  # Show table of contents? true/false
type: docs  # Do not modify.

# Add menu entry to sidebar.
# - name: Declare this menu item as a parent with ID `name`.
# - weight: Position of link in menu.
menu:
  api:
    name: Overview
    weight: 7
---

---
<br>

## Useful Links
* [APIs 101](https://www.youtube.com/watch?v=cpRcK4GS068&list=PLcgRuP1JhcBP8Kh0MC53GH_pxqfOhTVLa)
* [API Guide](https://www.moesif.com/blog/api-guide/) - Best practices and API tools
* [REST API Tutorial](https://restfulapi.net/)


## API
**A**pplication **P**rogramming **I**nterface  

*An API is a contract between application (app) and service.*

* Consumer vs Provider
  * A software app is often the **consumer** of an API.
  * When an API is offered over a network for consumption, the service that offers the API is said to be the **provider** or "API provider."

* The app may outsource requirements for data or functionality through an API by **calling** that API. To illustrate...
  * Patient record
  * Location represented as a pin on a map
  * The execution of a financial transaction

* It's a technical contract
  * Like a legal contract, it represents an understanding by all parties involved
  * The contract also represents agreed-upon standards




## REST
**RE**presentational **S**tate **T**ransfer

* Architectural style of the web
* A standard / set of guidelines by which you can structure and create APIs
* REST APIs have identifiable properties...
  * They make use of Resource-based URLs

---
The guiding architectural constraints required for an API to be considered RESTful:

1. Client-Server Architecture
2. Statelessness
3. Layered System
4. Cacheability
5. Uniform Design
6. Code on Demand

## Client-Server Architecture and Statelessness
REST APIs sit on top of web technology, like a hat. Similar to the web, a client (your program) makes a request to a server for a resource (i.e. an object). You will likely be using some sort of library to create the request to the server. The [protocol](https://developer.mozilla.org/en-US/docs/Glossary/protocol) used is HTTP and it's [stateless](https://en.wikipedia.org/wiki/Stateless_protocol). The server won't remember anything about the particular client. If you want to maintain state like your login credentials, you must send it with each and every request - you will do this using [Headers](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers).

## 

## Glossary of Terms

* [DNS](https://www.cloudflare.com/learning/dns/what-is-dns/) - Domain Name System
* [HTTP](https://developer.mozilla.org/en-US/docs/Web/HTTP/Overview) - HyperText Transfer Protocol
* [IP](https://www.cloudflare.com/learning/network-layer/internet-protocol/#:~:text=The%20Internet%20Protocol%20(IP)%20is%20a%20protocol%2C%20or%20set,into%20smaller%20pieces%2C%20called%20packets.&text=The%20most%20common%20transport%20protocols%20are%20TCP%20and%20UDP.) - Internet Protocol
* [TCP](https://condor.depaul.edu/jkristof/technotes/tcp.html) - Transmission Control Protocol
* [TLS](https://tls13.ulfheim.net/) - Transport Layer Security
* [UDP](https://hpbn.co/building-blocks-of-udp/) - User Datagram Protocol
* [URL and URI](https://www.baeldung.com/java-url-vs-uri) - Uniform Resource Locator (URL) and Uniform Resource Identifier (URI)
