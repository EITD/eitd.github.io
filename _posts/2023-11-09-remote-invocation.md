---
layout: post
section-type: post
has-comments: true
title: "Remote Invocation"
category: distributed basic
---

# **Idempotent operations**

> An idempotent operation is an operation that can be performed **repeatedly with the same effect** as if it had been performed exactly once.
> 

# History

If operations are not idempotent, the server must ensure that the same request is **not executed twice**.
Keep a history of all requests and replies. The same reply can be sent without re-executing if a request is resent.

- **At-most-once**: the request has been executed once. *Implemented using a history or simply not resending requests.*
- **At-least-once**: the request has been executed at least once. *No need for a history; simply resend requests until a reply is received.*

# HTTP

Request = Request-Line *(header CRLF) CRLF [ message-body ] 

Request-Line = Method space Request-URI space HTTP-Version CRLF

GET /index.html HTTP/1.1\r\n foo 42 \r\n\r\nHello

> CRLF: carriage return; line feed.
> 

# RPC: Remote Procedure Call

**RPC** is a mechanism that allows a program running on one computer (VM) to cause a procedure to be executed on another computer (VM) without the programmer needing to code for this explicitly.

Two processes are involved:

- **Caller (RPC client)** is a **calling process** that initiates an RPC to a server.
- **Callee (RPC server)** is a **called process** that accepts the call.

<aside>
💡 Each RPC is executed in a **separate process (thread)** on the server side. **An RPC is a synchronous operation.** The caller is suspended until the results of the remote procedure are returned.

</aside>
<br>
## **Executing RPC**

On each RPC, the server starts a **new process** to execute the call.

- The new process terminates when the procedure returns and results are sent to the caller.
- Calls from the same caller and calls from different callers are serviced by **different concurrent processes** on the server.

Concurrent invocations might interfere when accessing shared objects – might need **synchronization.**

# **Java RMI**

A remote object is passed as a reference (by reference), i.e., it remains at the original place it was created.

A serializable object is passed as a copy (by value), i.e., the object is duplicated.