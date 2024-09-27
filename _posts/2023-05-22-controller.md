---
layout: post
section-type: post
has-comments: true
title: "Controller"
category: spring
---

> Each controller class **maps one or more requests** **to methods** that process and execute the requests with provided inputs.
> 

# @RestController

`@RestController` is a class level annotation used to combine the functionality of the `@Controller` and `@ResponseBody` annotations.

- `@Controller` designates the annotated class as a controller
- `@ResponseBody` allows returned objects to be automatically serialized into **JSON** and returned in the **HTTP response body**

# **Deserializing to an Object**

In Spring, applying the `@RequestBody` annotation to a controller’s method enables automatic deserialization of the **HTTP request body** to an **object** bound to the method’s argument.

```java
@GetMapping("/book")
public Book isBookAvailable(@RequestBody Book book) {
  return library.find(book);
}

```