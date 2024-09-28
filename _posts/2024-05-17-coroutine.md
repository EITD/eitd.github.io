---
layout: post
section-type: post
has-comments: true
title: "Coroutine"
category: kotlin
---

## Challenges with Thread

- Require a lot of resources
- `Race conditions` and unpredictable behavior

```kotlin
fun main() {
   var count = 0
   for (i in 1..5) {
       Thread {
           count += 1
           println("Thread: $i count: $count")
       }.start()
   }
}
```

**Output**

```kotlin
Thread: 2 count: 2
Thread: 4 count: 4
Thread: 3 count: 3
Thread: 6 count: 6
Thread: 5 count: 5
```
<br>
## Coroutines in Kotlin

Create and use threads for background tasks. A more flexible and easier way to manage concurrency.

```kotlin
import kotlinx.coroutines.*

fun main() {
    repeat(3) {
        GlobalScope.launch { //CoroutineScope
            println("Hi from ${Thread.currentThread()}") //Job
        }
    }
}
```