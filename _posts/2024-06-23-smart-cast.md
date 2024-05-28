---
layout: post
title: "Smart Cast"
category: kotlin
---

In Java, there is a requirement of **explicit** type casting on the variable before accessing the properties of that variable.

```kotlin
Object ob = "GeeksforGeeks";
 
if(ob instanceof String) {
    // Explicit type casting
    String str = (String) ob;
 
    System.out.println("length of String " + str.length());
 }
```

In Kotlin, no need to explicitly cast something that was already checked.

```kotlin
val str1: String? = "GeeksforGeeks"
    
if(str1 is String) { //already checked
        
   // No Explicit type Casting needed.
   println("length of String ${str1.length}")
}
```