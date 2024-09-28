---
layout: post
section-type: post
has-comments: true
title: "Distributed Shared Memory"
category: distributed advanced
---

# Regular Register

### Termination

Each read/write operation issued by a correct process eventually completes.

### Validity

- Read returns last value written if
    - Not concurrent with another write, and
    - Not concurrent with a failed write
- Otherwise may return either the last or a concurrent “value”

### Fail-Stop Read-one write-all (1,N)

- Bogus algorithm modified
    - Use perfect FD P
    - Fail-stop model
- to write(v)
    - Update local value to v
    - Broadcast v to all
    - ⏳ Wait for ACK from all correct processes
    - Return
- to read
    - Return local value

# **Majority Voting in Register Implementation**

## Quorum principle (ex: majority)

- Always write to and read from a majority of processes
- At least one correct process knows most recent value

## Performance and Resilience

### Read-one write-all (1,N) algorithm

- Time complexity (write)
    - 2 communication steps (broadcast and Ack)
- Message complexity: O(N) messages
- Resilience: faulty processes f = N-1

### Majority voting (1,N) algorithm

- Time complexity (write and read)
    - 2 communication steps (one round trip)
- Message complexity: O(N) messages
- Resilience: faulty processes f < ⌈N/2⌉

# Linearizability vs. Sequential Consistency

## Sequential Consistency

> Only allow executions whose results appear as if there is a single system image and “local time” is obeyed.

SC is not compositional

Even though we can show SC(T|xr) for each register, SC(T) may not hold
<br>
## Linearizability/Atomicity

> Only allow executions whose results appear as if there is a single system image and “global time” is obeyed.

Linearizability is compositional
for all registers xr: LIN(T|xr) ⇔ LIN(T)

<aside>
💡 LIN is stronger than SC: LIN(T ) ⇒ SC(T )

</aside>

<br>
## Liveness requirements

- Wait-free
Every correct node should “make progress”
    
    (no deadlocks, no live-locks, no starvation)
    
- Lock-free/non-blocking
At least one correct node should “make progress”
    
    (no deadlocks, no live-locks, maybe starvation)
    
- Obstruction free/solo-termination
if a single node executes without interference (contention) it makes progress
    
    (no deadlocks, maybe live-locks, maybe starvation)
    

# Read-Impose Write Majority (1,N)

When reading, also do an update before responding

# Read-impose write-consult-majority (N,N)

- Before writing, read from majority to get last ts
- Do a query phase to get the latest timestamp before the update phase

### Atomic Register (N,N)

A write to complete requires 2 round-trips of messages

- One for the timestamp (query phase)
- One for broadcast-ACK (update phase)

A read to complete requires 2 round-trips of messages is

- One for read (query phase)
- One for impose if necessary (update phase)