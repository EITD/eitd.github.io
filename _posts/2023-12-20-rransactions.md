---
layout: post
section-type: post
has-comments: true
title: "Transactions"
category: distributed basic
---

Even if we have a distributed system that provides atomic operations, we sometimes want to group a sequence of operations in a transaction where:

- either all are executed or
- none is executed
- even if a node crash

# ACID

- **Atomic:** either all or nothing
- **Consistent:** the server should be left in a consistent state
- **Isolation:** total order of transactions
- **Durability:** persistent, once acknowledged

# Lost update


The lost update problem occurs when two transactions read the old value of a variable and then use it to calculate the new value. It cannot occur if the retrieval transaction is performed before or after the update transaction.


Serial equivalence is used as a criterion for the derivation of concurrency control protocols. These protocols attempt to serialize transactions in their access to objects:

- **most practical systems use locking**
- **optimistic concurrency control**
- **timestamp ordering.**

# **Unrepeatable/Dirty read**


The ‘dirty read’ problem is caused by the interaction between a read operation in one transaction and an earlier write operation in another transaction on the same object. In the case that p
aborts, then q must abort as well.


Allow for the fact that a transaction may abort by preventing it affecting other concurrent transactions if it does so. ***The isolation property of transactions requires that transactions do not see the uncommitted state of other transactions.

# **Cascading abort**

To avoid cascading aborts, transactions are only allowed to read objects that were written by committed transactions. **To ensure that this is the case, any read operation must be delayed until other transactions that applied a write operation to the same object have committed or aborted.** 

# Two-phase locking

- The first phase of each transaction is a ‘**growing phase**’, during which new locks are acquired.
- In the second phase, the locks are released (a ‘**shrinking phase**’).

## Read and write locks

- A request for a write lock on an object is delayed by the presence of a read lock belonging to another transaction.
- A request for either a read lock or a write lock on an object is delayed by the presence of a write lock belonging to another transaction.

# **Optimistic concurrency control**

- Perform transaction in a copy of an object, hoping that no other transaction will interfere.
- When performing a commit operation the validity is controlled.
- If transaction is valid, the values written to permanent storage.
- A transaction passes three phases:
    1. Working
    2. Validation: if passed, commit
    3. Update
    Validation and update are a critical section
    

## Validation

### Backward

> check my reads with committed writes.
> 

Validate a transaction by comparing all:

- read operations with committed write operations (rule 2)
- if a conflict is found, abort

### **Forward**

> check later reads with my (uncommitted) writes.
> 

Validate a transaction by comparing all:

- write operations with conflicting read operations (rule 1)
- if a conflict is found, abort ..