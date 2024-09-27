---
layout: post
section-type: post
has-comments: true
title: "Interface VS Abstract Class"
category: java
---

## What is Interface

> Does **not contain** any concrete methods.
> 

### Advantages:

- Achieve abstraction
- Loose coupling

## What is Abstract Class

> Should have **at least one abstract** method and can have concrete methods. Inheriting class should implement the abstract methods.
> 

### Advantages:

- Offer default functionality for the subclass
- Code reusability

## Difference between Interface && Abstract Class

|  | Interface | Abstract Class |
| --- | --- | --- |
| Speed | Slow | Fast |
| Inheritance | A Class can implement multiple Interfaces | A Class can inherit only one Abstract Class |
| Access Modifier | Everything is assumed public | Can have an access modifier |