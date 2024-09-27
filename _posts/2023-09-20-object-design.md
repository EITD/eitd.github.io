---
layout: post
section-type: post
has-comments: true
title: "Object Design"
category: mmse
---

# **Delegation instead of Implementation Inheritance**

- **Inheritance**: Extending a Base class by a new operation or overwriting an operation.
- **Delegation**: Catching an operation and sending it to another object.

## **Comparison**

**Delegation**

- Pro: Flexibility: Any object can be replaced at run time by another one (as long as it has the same type)
- Con**:** Inefficiency: Objects are encapsulated.

**Inheritance**

- Pro:
    - Straightforward to use
    - Supported by many programming languages
    - Easy to implement new functionality
- Con:
    - Inheritance exposes to a subclass the details of its parent class
    - Any change in the parent class implementation forces the subclass to change (which requires recompilation of both)

# **Implementation Inheritance vs Interface Inheritance**

- Implementation inheritance
    - Also called class inheritance
    - Goal: Extend an applications’ functionality by reusing
    functionality in parent class
    - Inherit from an existing class with some or all
    operations already implemented
- Interface inheritance (specification inheritance)
    - Also called subtyping
    - Inherit from an abstract class with all operations
    specified, but not yet implemented

# **The Liskov Substitution Principle**

- In class hierarchies, it should be possible to treat a specialized object as if it were a base class object.
- If an object of type S can be substituted in all the places where an object of type T is expected, then S is a subtype of T.
- An inheritance relationship that complies with the Liskov Substitution Principle is called *strict
inheritance*.


# **Adapter vs Bridge**

- Similarities:
    - Both are used to hide the details of the underlying implementation.
- Difference:
    - The Adapter pattern is geared towards making unrelated components work together
    - A Bridge, on the other hand, is used up-front in a design to let abstractions and implementations vary independently.

# Command Pattern

- **Client** creates a **ConcreteCommand** and binds it with a **Receiver.**
- **Client** hands the **ConcreteCommand** over to the **Invoker** which stores it.
- The **Invoker** has the responsibility to do the command (“execute” or “undo”)**.**

# Observer Pattern

- The **Subject** represents the actual state, the **Observers**
represent different views of the state.
- **Observer** can be implemented as a Java interface.
- **Subject** is a superclass needs to store the observers
