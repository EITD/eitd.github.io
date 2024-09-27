---
layout: post
section-type: post
has-comments: true
title: "Concurrent Programming"
category: erlang
---


# Process

> In Erlang, each thread of execution is called a **process**.
> 

The Erlang BIF `spawn` is used to create a new process: 

```jsx
spawn(Module, Exported_Function, List of Arguments). 
```

A function used by `spawn` to start a process, must be exported from the module.

> `spawn` returns a **process identifier**, or **pid**, which uniquely identifies the process.
> 

# Message Passing

Notice how the operator "!" is used to send messages. Message (any Erlang term) is sent to the process with identity Pid.

```jsx
Pid ! Message
```

`self()` returns the pid of the process that executes `self()`

```jsx
Pong_PID ! {ping, self()},
```

# Registered Process Names

Sometimes processes which need to know each other's identities are started independently of each other. 

> Erlang thus provides a mechanism for processes to be **given names** so that these names can be used as **identities instead of pids**.
> 

```jsx
register(some_atom, Pid)
```

Both **start** the "pong" process and **gives it the name** pong:

```jsx
register(pong, spawn(tut16, pong, [])),
```

 In the "ping" process, messages can be sent to pong by:

```jsx
pong ! {ping, self()},
```

# Distributed Programming

> Each Erlang system running on a computer is called an **Erlang node**.
> 

## cookie

The distributed Erlang implementation provides a very basic authentication mechanism to prevent unintentional access to an Erlang system on another computer. Erlang systems which talk to each other must have the same **magic cookie**.

## -name Vs -sname

The Erlang distributed systems normally use domain names rather than explicit IP addresses. This could be a problem since we’re working with laptops that are not regularly given names in the DNS. You will use IP address explicitly when starting an Erlang node.

`erl -sname` assumes that all nodes are in the same IP domain and we can use only the first component of the IP address, if we want to use nodes in different domains we use `-name` instead, but then all IP address must be given in full.

## send message

The "!" operator can be used to send a message disregarding if the process is on the **same node or on a different node**. A difference is how messages are sent to a registered process on another node:

```jsx
{pong, Pong_Node} ! {ping, self()},
```

A tuple `{registered_name,node_name}` is used instead of just the `registered_name`.

## send primitive !

`!` will accept both **registered names, remote names, and process identifiers**. This can sometimes cause a problem. If you implement a concurrent system that is not distributed and has a registered process under the name `foo`, you could pass the atom `foo` around, and anyone could treat it as a process identifier. Now if we distribute this application, a **remote process will not be able to use it** as a process identifier since the **registration process is local to a node**. So keep track of what you pass around: is it a **process identifier (that can be used remotely)**, or is it a name under which a process is registered.
