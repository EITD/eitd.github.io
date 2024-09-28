---
layout: post
section-type: post
has-comments: true
title: "System Design"
category: mmse
---

# **Coupling and Cohesion**

> Goal: Reduction of **complexity while change occurs**
> 

**Coupling** measures dependencies **between subsystems**

- High coupling: Changes to one subsystem will have high impact on the other subsystem (change of model, massive recompilation, etc.)
- **Low coupling**: A change in one subsystem does not affect any other subsystem

**Cohesion** measures the dependence **within the system**

- **High cohesion**: The classes in the subsystem perform similar tasks and are related to each other (via associations)
- Low cohesion: Lots of miscellaneous and auxiliary classes, no associations

<aside>
💡 Subsystems should have as maximum cohesion and minimum coupling as possible.

</aside>
<br>
# **Partitions and Layers**

> Partitioning and layering are techniques to achieve
low coupling.
> 

**Partitions** vertically divide a system into several independent (or weakly-coupled) subsystems that provide services on the same level of abstraction.
A **layer** is a subsystem that provides subsystem services to a higher layers (level of abstraction)

- A layer can only depend on lower layers
- A layer has no knowledge of higher layers

# **Client/Server Architectural Style**

- One or many servers provide services to instances of
subsystems, called clients.
- Client calls on the server, which performs some service
and returns the result
    - Client knows the interface of the server (its service)
    - Server does not need to know the interface of the client
- Response in general immediate
- Users interact only with the client

# **Peer-to-Peer Architectural Style**

- Generalization of Client/Server Architecture
- Clients can be servers and servers can be clients
- More difficult because of possibility of deadlocks

# **Model/View/Controller**

- Model subsystem: Responsible for application domain knowledge
- View subsystem: Responsible for displaying application domain objects to the user
- Controller subsystem: Responsible for sequence of interactions with the user