---
layout: post
section-type: post
has-comments: true
title: "Variable && Method"
category: java
---

## Member variable VS Local variable

1. **Syntax** form
    
    Member variables belong to **classes**, while local variables are variables or parameters of **methods**.
    
2. **Storage** method
    
    Member variable belongs to the class or instance. Objects exist in **heap** memory, and local variables exist in **stack** memory.
    
3. **Survival** time
    
    Member variables exist with the creation of objects, while local variables are generated with the call of methods and die with the end of method calls.
    
4. **Default** value
    
    Member variable will be automatically assigned to the **default** value of the type (Exception: the final member variable must be explicitly assigned), while the local variable will not be automatically assigned.
    

## Static method VS Instance method

1. **Call**
    
    Static method can be called by`class.method`&&`object.method`, while Instance method can only be called by the latter. Calling a static method does not require creating an object.
    
2. **Restrictions on Access Class Members**
    
    Static methods only allow access to static members.
    

## Final

- **final variable:**
    - The **value can’t be modified** once it has been assigned.
    - If any value has not been assigned to that variable, then it can be **assigned only by the constructor** of the class.
- **final method:**
    - **Cannot be overridden** by its children's classes.
    - A **constructor cannot be marked as final** because whenever a class is inherited, the constructors are not inherited. Hence, marking it final doesn't make sense. Java throws compilation error saying - `modifier final not allowed here`
- **final class:**
    - **No classes can be inherited** **from the final class** . But that final class **can extend other** classes for its usage.

## Static

- **static method and static variable:**
    - **Belong** to the **class**, not to the object of the class, so they are **shared** by all **instances** of the class.
    - **Gets memory** where the **class is loaded** during ****compile time.
    - Directly **called** with the help of **class names**. E.g. static method: `Math.max()`, `Math.min()`. static variable: `array.length`.
- **static class:**
    - ****Only **inner class** and work like other static members of the class.

### Static Method Overload Vs Override

- **Can be overload**: There can be two or more static methods in a class with the same name but differing input parameters.
- **Can’t be override**: **Overriding or dynamic** polymorphism occurs during the **runtime**, but the static methods are **loaded** and looked up at the **compile time** statically.