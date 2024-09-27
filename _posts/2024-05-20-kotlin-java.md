---
layout: post
section-type: post
has-comments: true
title: "Kotlin VS Java"
category: kotlin
---

| Extension | Need to create a new class and derive the parent class. | Enhance an existing class by prefixing the name of the class to name of the new function. |
| --- | --- | --- |
| Null Safe | NullPointerException | Cannot define null to any type of variable. Use ?. to assign null. |
| Coroutines | Difficult to manage multiple threads in the background. | Use coroutine to terminate execution at a specific point without blocking other threads. |
| Data Class | Class only holding data needs constructor, getter and setter, toString(), equals() functions. | Keyword ‘data’ and compiler will automatically take care of constructor getter and setter methods. |
| Type Inference | Define a type of each variable. | No need to define type. |
| Smart cast | Compulsory to check variable types and cast the object accordingly. | Handle casting checks with is. |