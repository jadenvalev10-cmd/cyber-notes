# TryHackMe: Client-Server Basics

Completed 100% (all 4 tasks).

The room covers the client-server model, DNS, client, server, port, protocol, and network (at a surface level), plus HTTP basics.

## Task 1: Introduction

Lists the room's objectives (the topics above).

## Task 2: Pizza Delivery

A pizza-order analogy for the client-server model.

- **Client / server:** Alice (client) wants pizza, and Bob delivers her order to Luigi's (server). The client always initiates the request. In computer terms, a browser (client) requests a webpage from a server.
- **Request / response:** Alice's order is the request. If it is malformed or unavailable, an error response comes back (e.g. "no pepperoni available").
- **Protocol:** Bob is the protocol: the shared rules for how client and server communicate. These cover which commands are understood (e.g. "get"), how a request is structured, what syntax or language is used, and what response is given for valid versus faulty requests.
- **Port:** identifies which specific service on a server you are reaching, like different doors at Luigi's for takeaway, dine-in, and delivery. One server can run multiple services, each on its own port.
- **DNS (Domain Name System):** resolves a name (e.g. "Luigi's Pizza") to a location, like a GPS. Online, DNS resolves a domain name to an IP address.

## Task 3: Web Communication in Practice

HTTP(S) basics.

- HTTP(S) is a **stateless** client-server protocol for the web: each request is handled independently, with no memory of past requests. Statefulness (e.g. staying logged in) is added at the application level via cookies or session tokens.
- There are 9 core HTTP methods (defined in RFCs): GET, POST, PUT, DELETE, PATCH, HEAD, OPTIONS, CONNECT, TRACE. The room focuses on GET, which retrieves a resource, e.g. `GET https://tryhackme.com/index.php`.
- **Practical lab:** used Firefox Developer Tools (F12) -> Network tab to inspect a real GET request and response on a demo site.
- **Key request fields:**
  - Scheme: http or https
  - Host: the domain name requested
  - Filename: the path requested ("/" = index.html)
  - Address: the server's IP address
  - Status: e.g. `200 OK` = success
- A response is a header (metadata) plus a body (the actual content, e.g. HTML).

## Task 4: Conclusion

Recap: the client-server model (the client initiates and the server replies), demonstrated with the pizza analogy, then HTTP as a concrete example of a client request and server response. The next room in the path is Virtualisation Basics.
