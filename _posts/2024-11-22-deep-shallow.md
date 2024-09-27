---
layout: post
section-type: post
has-comments: true
title: "Deep Copy VS Shallow Copy"
category: java
---

### Shallow copy

Shallow copy will create a **new object** on the heap. However, if the property inside the original object is a reference type, shallow copy will directly refer to the reference address of the internal object, which means the copy object and the original object **share the same internal reference object**.

### Deep copy

Deep copy **completely copies** the entire object, including the internal objects.
