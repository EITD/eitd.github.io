---
layout: post
section-type: post
has-comments: true
title: "synchronized VS volatile"
category: distributed advanced
---

## what is a distributed system

> A set of nodes, connected by a network, which appear to its users as a **single coherent** system.
> 

## what is a distributed algorithm

> A copy of a program running in each process.
> 

## Consensus: agreeing on a number

All nodes/processes propose a value
Some nodes (non correct nodes) might crash & stop responding

The algorithm must ensure a set of properties(specification):

- All correct nodes eventually decide
- Every node decides the same
- Only decide on proposed values

## Atomic Broadcast

- A node broadcasts a message
- If sender correct, all correct nodes deliver msg
- All correct nodes deliver the same messages
- Messages delivered in the same order

## Atomic Broadcast ↔ Consensus

- I. Atomic broadcast can be used to solve Consensus
    
    i.e., Every node broadcasts its proposal
    
    - Decide on the first received proposal
    - Messages received in same order
        - Thus, all nodes will decide the same value.
- II. Consensus can be used to solve Atomic broadcast

<aside>
💡 I+II: Atomic Broadcast equivalent to Consensus

</aside>