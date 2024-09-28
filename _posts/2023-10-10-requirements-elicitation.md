---
layout: post
section-type: post
has-comments: true
title: "Requirements Elicitation"
category: mmse
---

- **Scenarios**: Example of the use of the system in terms of a series of interactions between the user and the system
- **Use cases**: Abstraction that describes a class of scenarios

# **Requirements process**

- **Requirements Elicitation**: Definition of the system in terms understood by the **customer** (“Problem Description”)
- **Requirements Analysis**: Technical specification of the system in terms
understood by the **developer** (“Problem Specification”)

# **Principles of requirements determination**

## Requirements determination:

- The least technical phase of system development
- Demands social, communication and managerial skills
- Delivers a (mostly narrative) definition of user requirements

## Requirements definition

- System services - functional requirements
    - scope of the system
    - necessary business functions
    - required data structures
- System constraints - nonfunctional requirements
    - regarding ‘look and feel’, performance, security, etc.
    - also known as supplementary requirements

# **Types of requirements**

## **Functional requirements**

> Describe the interactions between the system and its environment independent from implementation.

- What inputs the system should accept
- What outputs the system should produce
- What data the system should *store* that other systems might use
- What computations the system should perform
- The timing and *synchronization* of the above

## **Nonfunctional requirements**

> User visible aspects of the system not directly related to functional behavior.

- **Usability**
    - ease of use
    - documentation and help, training, user interface, error, handling
- **Reliability**
    - mean time between failures, graceful recovery, dependable (we can depend on it) = reliability+robustness+safety
- **Performance**
    - response time, transaction throughput, resource consumption, concurrency level, uninterrupted availability, accuracy of results
    - efficiency – in terms of time and cost
- **Supportability** = adaptability + maintainability + portability

## **Constraints (“Pseudo requirements”)**

> Imposed by the client or the environment in which the system operates.
>