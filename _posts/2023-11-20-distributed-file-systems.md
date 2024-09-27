---
layout: post
section-type: post
has-comments: true
title: "Distributed file systems"
category: distributed basic
---

Functionality:

- persistent storage of files: create and delete
- manipulating a file: read and write operations
- authentication and authorization: who is allowed to do what
- a naming and directory service

# **Descriptors, table entries and i-nodes**

A process holds a set of open ***file descriptors***; each descriptor holds a pointer to an entry in a table of open files.

The file table entry holds a ***position*** and a pointer to an ***inode*** (index node).

The inode holds information about where file blocks are allocated.

# **One-copy semantics**

Most file systems give us a ***one-copy semantics***

- we expect operations to be visible to everyone and that everyone sees the same file
- if I tell you that the file has been modified, the modification should be visible