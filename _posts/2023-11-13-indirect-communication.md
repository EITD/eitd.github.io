---
layout: post
section-type: post
has-comments: true
title: "Indirect Communication"
category: distributed basic
---

# Time and space uncoupling

- **Space coupling - Time-coupled**: Properties: Communication directed towards a given
receiver or receivers; receiver(s) must exist at that moment. Examples: Message passing, remote invocation
- **Space coupling - Time-uncoupled:** Properties: Communication directed towards a
given receiver or receivers; sender(s) and receiver(s) can have independent lifetimes. Examples: email
- **Space uncoupling - Time-coupled**: Properties: The sender does not need to know the identity of the receiver(s); the receiver(s) must exist at that moment. Example: IP
multicast
- **Space uncoupling - Time-uncoupled**: Properties: The sender does not need to know the identity of the receiver(s); sender(s) and receiver(s) can have independent lifetimes. Examples: Most indirect communication paradigms covered in this chapter

# **Ordering of messages**

- ***FIFO order***: All messages are received in the order sent.
- ***Causal order***: If a message ***m*2** is sent as a consequence of a message ***m*1** (i.e., a process has seen ***m*1** and then sends ***m*2**), then all members should see ***m*1** before ***m*2**.
- ***Total order***: All members will see messages in precisely the same order.

> Causal ordering does not strictly imply FIFO; a process can send ***m*1** and then ***m*2** but has not yet seen its message ***m*1**.
> 

# Subscriptions

- ***Channel***: events are published to a channel that processes can subscribe to.
- ***Topic (Subject)***: an event is published given one or more topics(#foo). If topics are structured in a hierarchy, processes can choose to subscribe to a topic or a sub-topic.
- ***Content***: subscribers specify properties of the content, more general - harder to implement
- ***Type***: used by object-oriented languages; subscribe on an event of a particular class

# Event routing

The ***event routing*** depends on our subscription model and performance, fault tolerance, availability, and consistency requirements.

## Flooding

- send all published events to all nodes in the network
- each node does matching
- can be implemented using underlying network multicast

## Filtering

- a subscription is sent to the closest broker
- brokers share information about subscriptions
- a broker knows which neighboring brokers should be sent published events

## Advertisement

- Publishers advertise event classes
- advertisements are propagated in the network
- subscribers contact publishers if they are interested.