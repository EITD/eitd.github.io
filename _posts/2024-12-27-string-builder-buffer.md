---
layout: post
section-type: post
has-comments: true
title: "String/Builder/Buffer"
category: java
---

|  | String | StringBuilder | StringBuffer |
| --- | --- | --- | --- |
| Storage area | String pool | Heap | Heap |
| Mutability | Immutable and concatenation operator(+) internally uses StringBuilder or StringBuffer class. | Mutable | Mutable |
| Efficiency | Slowest because new memory is required for the new String with appended character | Fastest | Faster than String, Slower than String Builder |
| Thread-safe | Immutable and not used in threaded environment | Suitable for an environment with a single thread | Suitable for multiple threads |