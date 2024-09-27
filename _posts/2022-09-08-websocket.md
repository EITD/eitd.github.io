---
layout: post
section-type: post
has-comments: true
title: "Websocket"
category: network
---

<aside>
💡 Different from HTTP, Websocket provides full-duplex communication.

</aside>

## Advantages

- **Less** **control cost**
    
    The packet **header** used for protocol control is relatively small. 
    
- **Real-time**
    
    Since the protocol is full-duplex, the server can send data to the client at **any time**. Compared with HTTP requests, server needs to **wait for the client** **request**.
    
- **Keep connected**
    
    Unlike HTTP, Websocket needs to create a **connection** before communication.
    
- **Better binary support**
- **Extensions support**
- **Better compression**