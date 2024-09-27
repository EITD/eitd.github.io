---
layout: post
section-type: post
has-comments: true
title: "Coordination"
category: distributed basic
---

> For a set of processes to coordinate their actions or to agree on one or more values.
> 

# Example of coordination

- ***Mutual exclusion*** - who is to enter a critical section
- ***Leader election*** - who is to be the new leader
- ***Group communication*** - same messages in the same order

## Mutual exclusion

***Safety***: at most one process may be in a critical section at a time

***Liveness***: starvation-free, deadlock-free

***Ordering***: enter in request happened-before order

### **Ricart and Agrawala**

A request contains a *Lamport time stamp* and a *process identifier*.
Request can be ordered based on the time stamp and the process identifier if time stamps are equal.

When you’re waiting for permissions and receive a request from another node:

- if the request is *smaller*, then give permission
- otherwise, save the request

### **Maekawa’s Voting Algorithm**

To request entry:

- *ask* all nodes of your quorum for permission
- *wait* for all to vote for you:
    - queue requests from other nodes
- *enter* the critical section
- *leave* the critical section:
    - return all votes
    - vote for the first request, if any, in the queue

Otherwise:

- if you have not voted:
    - vote for the first node to send a request
- if you have voted:
    - wait for your vote to return, queue requests from other nodes
    - when your vote is returned, vote for the
    first request, if any, in the queue


### **A ring-based approach**

- a node starts an election
- the call is updated
- the leader is identified
- and proclaimed


## Group communication

> Multicast a message to *specified group of nodes with certain guarantees*
> 

Ordering of delivery:

- ***FIFO***: in the order of the sender
- ***causal***: in a happened-before order
- ***total***: the same order for all nodes

### **Reliable multicast**

When receiving a message, forward it to all nodes.
Watch out for duplicates.

### **Uniform agreement**

***Uniform agreement***: if any node, correct or incorrect, delivers a message, then all correct nodes will deliver the message.

***Non-uniform agreement***: if a correct node delivers a message, then all correct nodes will deliver the message.