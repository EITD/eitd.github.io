---
layout: post
section-type: post
has-comments: true
title: "Name Services"
category: distributed basic
---

> A service that provides information about remote resources given a name.
> 

# Terminology

1. Pure names:						
 **pure** - no internal information
**non-pure** - contains information

> IP address is non-pure name because it contains a location information (class, net id and host id)
> 

2. Flat or hierarchical
**flat** - all names directly comparable
**hierarchical** - names interpreted in an environment

# File systems

The **inode** is a data structure used to represent a filesystem object. **Each inode stores the attributes and disk block location(s) of the filesystem object's data.**

- A **hard link** to a file will point to the place where the file is stored or the inode of that file.
- A **symbolic (soft) link** will point to the actual file itself. Because file “soft.txt" points to file “foo.txt" itself, if file "foo.txt" is deleted, then file “soft.txt" will have nothing to point to; it is also deleted.

# DNS - Domain Name Service

> The Domain Name System is a name service design whose central naming database is used across the Internet.
> 

A DNS name consist of:

- a top-level domain: se
- a sequence of subdomains: kth
- possibly a host name: www

## DNS architecture

Each server is an authoritative server for a zone; it holds the master record for the nodes below it. Authoritative servers also work as slave servers for other zones to provide redundancy.
