---
layout: post
section-type: post
has-comments: true
title: "Distributed Transactions"
category: distributed basic
---

# Phantom deadlock


A deadlock that is detected but is not really a deadlock is called a **phantom deadlock**. In ***distributed deadlock detection***, information about wait-for relationships between transactions is transmitted from one server to another. If there is a deadlock, the necessary information will eventually be collected in one place, and a cycle will be detected. ***As this procedure will take some time, there is a chance that one of the transactions that holds a lock (see U above) will have released it, in which case the deadlock will no longer exist.***
