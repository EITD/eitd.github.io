---
layout: post
section-type: post
has-comments: true
title: "Concurrency"
category: java
---

## Atomicity

> One or more operations are either **performed all** and the process will not be interrupted by any factors, or they will **not be executed**.

**Example**:
    
```java
x = 10;        //atomicity
y = x;         //two operations: read x and assign x to y
x++;           //three operations: read x, plus 1 and write new value
```
    
<br>
## Visibility

> When multiple threads access the same variable, **one thread modifies** the value of the variable, and **other threads** **can see** the modified value.
> 

## Orderly

> The order in which the program is executed according to the order of the code.
>