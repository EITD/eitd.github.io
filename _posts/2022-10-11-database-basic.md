---
layout: post
section-type: post
has-comments: true
title: "Database Basic"
category: database
---

## DAO

1. The **Data Access Object** is a pattern that allows to **isolate** business/application layer from the persistence layer using an abstract API.
2. **Functionality**: Hide from the application all the **complexities** involved in performing **CRUD** operations in the underlying storage mechanism.

## Connection Pooling

- Open a database connection is **costly**.
- Opened connections are maintained and kept in a cache(”pool”) so that they can be **reused** in the future.
- **Cut down** on the amount of time waiting to establish a connection.

## Drop VS Delete VS Truncate

- `Drop`
    
    Delete all tables directly.
    
- `Truncate`
    
    Only delete the data in the table.
    
- `Delete`
    
    Delete the data of a row.