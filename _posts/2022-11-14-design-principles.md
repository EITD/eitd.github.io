---
layout: post
section-type: post
has-comments: true
title: "Design Principles - SOLID"
category: design
---

## Single-Responsibility

> A class should only have one job.
> 

## Open-Closed

> Open for extension but close for modification.
> 

## Liskov Substitution

> Every subclass or derived class should be substitutable for their base or parent class.
> 

## Interface Segregation

> A client should never be forced to implement an interface that it doesn’t use or depend on methods they don’t use.
> 

## Dependency Inversion

> Depend on abstractions, not on concretions.
> 

```php
class MySQLConnection
{
    public function connect()
    {
        // handle the database connection
        return 'Database connection';
    }
}

class PasswordReminder
{
    private $dbConnection;

		// depend on MySQLConnection(concrete class)
    public function __construct(MySQLConnection $dbConnection)
    {
        $this->dbConnection = $dbConnection;
    }
}
```

If you change the database engine, you will also have to edit the `PasswordReminder` class.

```php
interface DBConnectionInterface
{
    public function connect();
}

class MySQLConnection implements DBConnectionInterface
{
    public function connect()
    {
        // handle the database connection
        return 'Database connection';
    }
}

class PasswordReminder
{
    private $dbConnection;

		// depend on abstraction
    public function __construct(DBConnectionInterface $dbConnection)
    {
        $this->dbConnection = $dbConnection;
    }
}
```