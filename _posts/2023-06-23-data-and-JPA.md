---
layout: post
section-type: post
has-comments: true
title: "Data and JPA"
category: spring
---

# **Spring JPA**

The **Java Persistence AP**I (JPA) is a specification for the set of **interfaces** to store, query, and update **data stored in a database**. JPA can be **implemented** by an Object Relational Mapping (**ORM**) which **maps classes to a database table.** JPA’s use of ORM allows developers to interact with the database without having to write database queries.

## **JPA Repository Injection**

With Spring Data JPA, listing repositories as properties allows them to be made available to other classes. This functionality is facilitated by the repository instance being **injected into the class at runtime**.

```java
@RestController
public class PersonController {
  private final PersonRepository personRepository;
 
  public PersonController(final PersonRepository personRepository) {
    this.personRepository = personRepository;
}
```

# **Spring H2 Database**

H2 is a type of database engine in Java. It is **embedded** into the application and supports in-memory or disk-based persistence.

## **JPA H2 Console**

Spring Boot configures an H2 console that allows developers to **inspect the application’s database**. The console can be accessed via the browser at the URI `/h2-console`.

# JdbcTemplate class

The Spring JDBC template is the primary API through which we can **access database operations logic** that we’re interested in:

- Creation and closing of **connections**
- Executing **statements** and **stored procedure** **calls**
- **Iterating** over the *ResultSet* and returning results

In order to use it, we'll need to define the simple configuration of *DataSource*:

```java
@Configuration
@ComponentScan("org.baeldung.jdbc")
publicclassSpringJdbcConfig {
    @Bean
		public DataSourcemysqlDataSource() {
				DriverManagerDataSource dataSource = newDriverManagerDataSource();
        dataSource.setDriverClassName("com.mysql.jdbc.Driver");
        dataSource.setUrl("jdbc:mysql://localhost:3306/springjdbc");
        dataSource.setUsername("guest_user");
        dataSource.setPassword("guest_password");

				return dataSource;
    }
}
```