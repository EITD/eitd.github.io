---
layout: post
section-type: post
has-comments: true
title: "Clocks and Time"
category: distributed basic
---

# Logical time

- All events in one process are ordered.
- The sending of a message occurs before the receiving of the message.
- Events in a distributed system are partially ordered.
- The order is called **happened before**.
- Logical time gives us a tool to talk about ordering without having to synchronize clocks.

## Lamport clock

One counter per process:

- initially set to 0
- each process increments only its clock
- sent messages are tagged with a timestamp

Receiving a message:

- set the clock to the greatest of the internal clock and

the time stamp of the message


## **Vector clock**

A **vector** with one counter per process:

- initially set to <0,....>
- each process increments only its index
- sent messages are tagged with a vector

Receiving a message:

- **merge** the internal clock and the time stamp of the message


<aside>
💡 a <a1, a2, a3> all less or equal than b <b1, b2, b3> ⇒ a happened-before b, otherwise they are concurrent.

</aside>