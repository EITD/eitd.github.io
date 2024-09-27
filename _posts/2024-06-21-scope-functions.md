---
layout: post
section-type: post
has-comments: true
title: "Scope functions"
category: kotlin
---

<aside>
💡 let, with, run, also, apply

</aside>

## Context object: this or it

### this

`run`, `apply`, `with` refer to the context object as a lambda receiver.

Operate on the object members: call its functions or assign properties.

### it

`let`, `also` refer to the context object as a lambda argument.

Easier for reading, object used as an argument in function calls and multiple variables in a block.

## Return value

### context object

Can continue chaining function calls on the same object after `apply`,`also` .

### lambda result

`run`, `let`,`with` can assign result to a variable.

> `run` does the same as `with`, but invokes as `let`.
>