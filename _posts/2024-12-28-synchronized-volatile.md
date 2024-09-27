---
layout: post
section-type: post
has-comments: true
title: "synchronized VS volatile"
category: java
---

## Thread Safety

1. Execution control (order, execute concurrently)
2. Memory visibility (results visibility to other threads)

<aside>
💡 Thread will copy the main memory data to local and flush result back after completion.

</aside>


## Synchronized

- Prevents any other thread from obtaining the monitor lock for **the same object**, thereby preventing other threads to access the object and executing concurrently.
- Creates a **memory barrier** which flushes results to CPU main memory and ensures the thread  acquiring the lock first to operate **before** the thread acquiring the lock subsequently.

## synchronous Vs asynchrounous

- Synchronous functions are **blocking** while asynchronous functions are not. In synchronous functions, statements complete before the next statement is run. In this case, the program is evaluated **exactly in order of the statements** and execution of the program is paused if one of the statements take a very long time.
- Asynchronous functions usually accepet a **callback** as a parameter and execution continue on the **next line immediately** after the asynchronous function is invoked. The callback is only invoked when the asynchronous operation is complete and the call stack is empty. **Heavy duty** operations such as loading data from a web server or querying a database should be done asynchronously so that the **main thread can continue** executing other operations instead of blocking until that long operation to complete.

## Volatile

- Forces all accesses(read and write) to the variable to **occur to main memory**, which is useful for actions requiring correct visibility and **order** of accesses is **not important**.