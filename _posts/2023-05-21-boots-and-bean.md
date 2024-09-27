---
layout: post
section-type: post
has-comments: true
title: "Boots and Bean"
category: spring
---

# Spring Bean

> A *Spring bean* refers to an object that’s **managed by** the Spring Inversion of Control (**IoC**) container.
> 

## Scope

In order to set Spring Bean's scope, we can use `@Scope` annotation or “scope” attribute in XML configuration files. 

| Scope | Description |
| --- | --- |
| singleton | Scopes a single bean definition to a single object instance per Spring IoC container. Not Thread Safe. |
| prototype | Scopes a single bean definition to any number of object instances. |
| request | Scopes a single bean definition to the lifecycle of a single HTTP request; that is, each HTTP request has its own instance of a bean created off the back of a single bean definition. Only valid in the context of a web-aware Spring ApplicationContext. |
| session | Scopes a single bean definition to the lifecycle of an HTTP Session. Only valid in the context of a web-aware Spring ApplicationContext. |
| global session | Scopes a single bean definition to the lifecycle of a global HTTP Session. Typically only valid when used in a portlet context. Only valid in the context of a web-aware Spring ApplicationContext. |

## Life Cycle

# **application context**

> The *application context* serves as a **container** into which Spring can inject beans.
> 

# **Spring Boot**

> Spring Boot extends the Spring framework by enabling the **autoconfiguration** of Spring beans, further simplifying development.
> 

## **@SpringBootApplication**

`@SpringBootApplication` is a compilation of the `@Configuration`,  `@EnableAutoConfiguration`, and `@ComponentScan` annotations.

1. Enables Spring to identify the class as the configuration class that **provides beans** for the Spring application context
2. Enables Spring to **scan** for and **configure** annotated classes as beans
3. Enables Spring to configure beans based on **code** as well as **jar dependencies**