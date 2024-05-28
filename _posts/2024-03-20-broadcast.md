---
layout: post
title: "Broadcast"
category: distributed advanced
---

# Quorums

> Quorum is any set of majority of processes.
> 

<aside>
💡 Quorums used in Fail-Silent (asynchronous) and Fail-Noisy (partially synchronous) algorithms.

</aside>

# Broadcast Abstractions

- **Best-effort Broadcast**
    - Guarantees reliability only if sender is correct
- **Reliable Broadcast**
    - Guarantees reliability independent of whether sender is correct
- **Uniform Reliable Broadcast**
    - Also considers behaviour of failed nodes
- **Causal Order Reliable Broadcast**
    - Reliable broadcast with causal delivery order

# Best-Effort Broadcast

- Intuitively: everything perfect unless sender crashes
- Properties
    - BEB1. Best-effort-Validity: If pi and pj are correct, then any broadcast by pi is eventually delivered by pj
    - BEB2. No duplication: No message delivered more than once
    - BEB3. No creation: No message delivered unless broadcast

# Reliable Broadcast

- BEB gives no guarantees if sender crashes
    - Strengthen to give guarantees if sender crashes
- Reliable Broadcast Intuition
    - Same as BEB, plus
    - If sender crashes: ensure all or none of the correct processes get msg
    - *one correct deliver m, every correct deliver m*
- Properties
    - RB1. Validity: If a correct process pi broadcasts a message m, then pi should eventually deliver m
    - RB2 = BEB2. No duplication
    - RB3 = BEB3. No creation
    - RB4. Agreement: If a correct process delivers m, then every correct process delivers m

### Complexity of lazy reliable broadcast

- Assume N processes
- Message complexity
    - Best case: O(N) messages
    - Worst case: O(N2) messages
- Time complexity
    - Best case: 1 round
    - Worst case: 2 rounds

### Eager reliable broadcast

What happens if we replace P with ◊P?

- Only affects performance
- Only affects correctness
- No effect
- Affects performance and correctness

# Uniform Reliable Broadcast

- Uniform reliable broadcast intuition
    - If a failed node delivers, everyone must deliver…
    - At least correct nodes, we cannot revive the dead…
    - *One fail deliver m, every correct deliver m*
- Properties
    - URB1 = RB1.
    - URB2 = RB2.
    - URB3 = RB3.
    - URB4. Uniform Agreement: For any message m, if a process delivers m, then every correct process delivers m

### Uniform eager reliable broadcast

- Messages are **pending** until all correct processes get it
    - Collect acks from processes that got msg
- Deliver once all correct processes acked
    - Use perfect FD
    - **function canDeliver**(m):
        
        **return** correct ⊆ ack[m]
        
- Has resilience = N − 1

### Majority-ack uniform reliable broadcast

- Replace one function
- function canDeliver(m)
return |ack[m]|>n/2
- Has resilience less than N/2

# Causal Order Reliable Broadcast

## Causality

- single-source FIFO:  Some process pi broadcasts m1 before broadcasting m2
- network order: Some process pi delivers m1 and later broadcasts m2
- transitivity: There is a message m’ such that m1 → m’ and m’ → m2

## Specification

<aside>
💡 CB: If process pi delivers m, then pi must deliver every message causally preceding (→) m before m

</aside>

## No-Wait causal broadcast

> Each message m carries ordered list of causally preceding messages in **pastm.**
> 

## Waiting COB algorithm(vector clock)

- At process pi
    - VC[i]: number of messages pi coBroadcasted & Delivered
    - VC[j], j≠i: number of messages pi coDelivered from pj
- Upon RB delivery of m with attached VCm
- compare VCm with local VCi
    - Only deliver m once VCm ≤ VCi
    - Do Not deliver if VCm > VCi or VCm ≠ VCi
- Each message m is not delivered until all causally preceding messages are delivered