---
layout: post
section-type: post
has-comments: true
title: "Delegation"
category: kotlin
---

### Explicitly delegation

Supported by all object-oriented language by passing a delegate object (the one **to be implemented**) to a delegating object (the one that will **implement** delegate object).

```kotlin
interface delegation 
{
    fun mymessage()
}
  
class delegationimplementation(val y: String) : delegation
{
    override fun mymessage() 
    { 
        print(y)
    }
}

fun main() 
{
    val b = delegationimplementation("\nWelcome, GFG!")
      
    b.mymessage()
}
```

### Implicit delegation

Require language-level support: in Kotlin, use keyword `by` . 

```kotlin
interface delegation 
{
    fun mymessage()
    fun mymessageline()
}
  
class delegationimplementation(val y: String) : delegation
{
    override fun mymessage() 
    { 
        print(y)
    }
    override fun mymessageline() 
    { 
        println(y)
    }
}
  
class Newfeature(m: delegation) : delegation by m
{
    override fun mymessage() 
    {
        print("GeeksforGeeks")
    }
}
  
fun main() 
{
    val b = delegationimplementation("\nWelcome, GFG!")
      
    Newfeature(b).mymessage()
    Newfeature(b).mymessageline()
}
```

**Output**

```kotlin
GeeksforGeeks
Welcome, GFG!
```

**Advantages**:

- Multiple interfaces can be implemented with the **help of existing** ones.
- Used to **add new features** and values to current implementations.