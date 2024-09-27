---
layout: post
section-type: post
has-comments: true
title: "Consensus"
category: distributed advanced
---

# Properties

- C1. Validity
Any value decided is a value proposed
- C2. Regular Agreement
No two correct processes decide differently
    
    Uniform Agreement
    No two processes decide different values
    
- C3. Termination
Every correct process eventually decides
- C4. Integrity
A process decides at most once

# Resilience

- Solvable in Fail-Stop model (decide on last round) with strong FD
- Not solvable in the Fail-Silent model (asynchronous system model)

# Paxos

## Terminology

### Proposers

Will attempt imposing their proposal to set of acceptors

### Acceptors

May accept values issued by proposers

### Learners

Will decide depending on acceptors acceptances

---

- Acceptors cannot communicate with each other.
- Proposers cannot communicate with each other either.
- Each process plays all 3 roles in classic setting

## Quorum approach

- Each proposer tries to impose its value v on the set of acceptors
- If **majority** of acceptors accept v, then v is chosen
- Learners try to decide the chosen value

## Ballot

Ideally, there will be a single proposer should at least provide **obstruction-free progress**

> Obstruction-free = if a single proposer executes without interference (contention) it makes progress
> 

### Invariant

- P1. An acceptor accepts **first** proposal it receives
- P2. If proposal (n,v) is chosen, every higher numbered proposal chosen has value v
    - P2a. If v is chosen, every higher proposal **accepted** has value v
    - P2b. If v is chosen, every higher proposal **issued** has value v
    - P2c. If any proposal (n,v) is issued, there is a majority set S of acceptors such that either
        - **no one** in S has accepted any proposal numbered less than n
        - v is the value of **the highest proposal** among all proposals less than n accepted by acceptors in S

## Optimization

- Necessary
    - Reject accept(n,v) if answered prepare(m) : m>n
- Optimizations
    - Reject prepare(n) if answered prepare(m) : m>n
    - Reject accept(n,v) if answered accept(m,u) : m>n
    - Reject prepare(n) if answered accept(m,u) : m>n
    - Ignore old messages to proposals that got majority