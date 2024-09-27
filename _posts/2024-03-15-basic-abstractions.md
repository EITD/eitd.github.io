---
layout: post
section-type: post
has-comments: true
title: "Basic Abstractions"
category: distributed advanced
---

# Event-Based Component Model

## Event-Based Programming

- Events include any scheduled action
    - New Message (most of the time)
    - A Timeout (from Environment Clock*)
    - A State Condition (e.g. x==5 & y<9)
- Two types of events
    - Requests (incoming to component)
    - Indications (outgoing from component)

## Channels as Components

Request (input) event:
**Send** to destination some message (with data)

Indication (output) event:
**Deliver** from source some message (with data)

# Specifications

## Specifications of a Service

### declarative specification **“what”** aka **problem**:

1. **Interface(Contract, API)**
    
    Requests
    
    Indications/Responses
    
2. **Correctness Properties**
    
    Safety
    
    Liveness
    
3. **Underlying Model**
    
    Assumptions on failures
    
    Assumptions on timing(amount of synchrony)
    

### imperative many possible **“how”**:

**Implementation**

Composed of other services

Adheres to interface and satisfies correctness

Has internal events

# Safety and Liveness

## Safety

> Properties that state that nothing bad ever happens
> 

**satisfied** in infinite time (you’re never safe)
**violated** in finite time (when the bad happens)
Often involves the word “never”, “at most”, “cannot”,…

## Liveness

> Properties that state that something good eventually happens
> 

**satisfied** in finite time (when the good happens)
**violated** in infinite time (there’s always hope)
Often involves the words eventually, or must

<aside>
💡 Any trace property can be expressed as the conjunction of a safety property and a liveness property

</aside>

# Faults Hierarchy

## Process Failures

Processes may fail in four ways:

- Crash-stop
- Omissions
- Crash-recovery
    
    A process is faulty in an execution if
    
    - It crashes and never recovers, or
    - It crashes and recovers infinitely often (unstable)
- Byzantine/Arbitrary

<aside>
💡 Processes that don’t fail in an execution are correct

</aside>


# Channel Behavior

## Fair-Loss Links

> Channels delivers any message sent with non-zero probability (no network partitions)
> 
- ***FL1. Fair-loss***: If m is sent infinitely often by pi to pj, and neither crash, then m is delivered infinitely often by pj
- ***FL2. Finite duplication:*** If a m is sent a finite number of times by pi to pj, then it is delivered at most a finite number of times by pj
    
    I.e. a message cannot be duplicated infinitely many times
    
- ***FL3. No creation:*** No message is delivered unless it was sent

## Stubborn Links

> Channels delivers any message sent infinitely many times
> 

### Implementation

- Use the Lossy link
- Sender stores every message it sends in **sent**
- It periodically resends all messages in **sent**

### Correctness

- ***SL1. Stubborn delivery:*** if a correct process pi sends a message m to a correct process pj, then pj delivers m an infinite number of times
- ***SL2. No creation:*** if a message m is delivered by some process pj, then m was previously sent by some process pi

## Perfect Links

> Channels that deliver any message sent exactly once
> 

### Implementation

- Use Stubborn links
- Receiver keeps a log of all received messages in **Delivered**
- Only deliver (perfect link Deliver) messages that weren’t delivered before

### Correctness

- ***PL1. Reliable Delivery:***  If pi and pj are correct, then every
message sent by pi to pj is eventually delivered by pj (liveness)
- ***PL2. No duplication:*** Every message is delivered at most once (safety)
- ***PL3. No creation:*** No message is delivered unless it was sent (safety)

# Asynchrony

## Causal Order

Two events are causally ordered iff either:

- a occurs before b on the same process
- a is a send(m) and b deliver(m) event
- there exists a sequence of causally ordered events from a to b (transitive)

## Execution Equivalence

<aside>
💡 If two executions F and E have the same collection of events, and their causal order is preserved, F and E are said to be similar executions, written F~E

</aside>