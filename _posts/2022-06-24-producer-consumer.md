---
layout: post
title: "Producer-Consumer"
category: os
---

<aside>
💡 One producer and one consumer and they **share** the same memory buffer that is of **fix-sized.**

</aside>

# Problem

1. Producer can produce data only when the buffer is **not full**.
2. Consumer can consume data only when the buffer is **not empty**.
3. Producer and Consumer should **not access** the buffer at **same time**.

# Solution - Semaphore

- Semaphore S
    
    Achieve **mutual exclusion** between processes.
    
- Semaphore E
    
    Define the **empty** space in the buffer.
    
- Semaphore F
    
    Define the space that is **filled** by the producer.
    
- `wait()`
    
    **Decrease** the semaphore variable by 1.
    
- `signal()`
    
    **Increase** the semaphore variable by 1.
    

## Producer

```java
void producer() {
    while(T) {
        produce()
        wait(E)
        wait(S)
        append()
        signal(S)
        signal(F)
    }
}
```

> If the buffer is full i.e. **“E” is “0”**, the program will stop and no production will be done.
> 

## Consumer

```java
void consumer() {
    while(T) {
        wait(F)
        wait(S)
        take()
        signal(S)
        signal(E)
        use()
    }
}
```

> If the buffer is empty i.e. “**F” is “0”**, no consumption will be made.
> 