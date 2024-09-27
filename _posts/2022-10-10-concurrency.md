---
layout: post
section-type: post
has-comments: true
title: "Concurrency"
category: database
---

## Consistent Problem

### Loss Modification

The **update operation** of one transaction is **replaced** by the update operation of another transaction. 


### Read Dirty Data

The current transaction can **read the uncommitted data** of another transaction.


### Non-repeatable Read

Before this transaction is over, **another transaction accesses and modifies** the same data set. Due to the modification of the second transaction, the **data may be inconsistent**.

### shadow read

Included in Non-repeatable read.

## Lock Level

### Lock

- **Exclusive lock**: **X** lock, it can read and update A. **Other transactions cannot lock** A during locking.
- **Shared lock**: **S** lock, which can read A, but cannot be updated. Other transactions **can S lock** A, but **not X lock**.


### Lock Protocol

1. **First-level Lockdown Protocol**
    
    Transaction T **must add an X lock to modify data A**, and the lock will **not be released until the end** of T.
    
    **Solve** **Loss Modification problem** because two transactions cannot modify the same data at the same time.
    
    
2. **Second-level** **Lockdown Protocol**
    
    Transaction T is required to **add an S lock when reading data A**, and the S lock must be **released immediately after reading**.
    
    **Solve Read Dirty Data problem** because if a transaction is modifying data A and an X lock is added, then the S lock can not be added and the data can not be read.
    
    
3. **Third-level** **Lockdown Protocol**
    
    Transaction T is required to **add an S lock when reading data A**, and the S lock **cannot be released until the transaction is over**.
    
    **Solve Non-repeatable Read problem** because when reading A, other transactions cannot X lock A, thus avoiding changes in data during reading.
    
    

## Isolation Level

- **READ UNCOMMITTED**
    
    **Modifications** in transactions are **visible** to other transactions even if they are **not committed**.
    
- **SUBMIT READ**
    
    A transaction can **only read changes** made by **committed** transactions. 
    
- **REPEATABLE READ**
    
    Ensure that the result of **reading the same data** multiple times in the **same transaction** is the **same**.
    
- **Serializable**
    
    Force transactions to **execute serially**, so that multiple transactions do not interfere with each other and there will be no concurrency consistency problem.
    