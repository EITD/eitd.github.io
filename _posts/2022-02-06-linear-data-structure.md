---
layout: post
section-type: post
has-comments: true
title: "Linear Data Structure"
category: data structure
---
## Array

```
array length: n。
access：O（1）
insert：O（n）
delete：O（n）
```

## LinkedList

```
n elements in linked list.
access：O（n）
insert and delete：O（1）
```

### Applications

- Stack, Queue, binary trees, and graphs are implemented using linked lists.
- Dynamic management for Operating System memory.
- Forward and backward operation in the browser.

## Stack

```
n elements in stack.
access：O（n）
insert and delete：O（1）
```

### Applications

- Redo and Undo operations in doc editors
- Reversing a string
- Function calls order

## Queue

```
n elements in queue.
access：O（n）
insert and delete：O（1）
queue is empty：front == rear
queue is full：（rear+1）% maxsiz == front
```

### Applications

- Breadth-first search algorithm in graphs
- Operating system: job scheduling operations, Disk scheduling, CPU scheduling etc.
- Call management in call centres