---
layout: post
section-type: post
has-comments: true
title: "Spring MVC"
category: spring
---

> MVC stands for Model-View-Controller design pattern which separates the **business** logic, **presentation** logic and **navigation** logic.

- **Model:** is responsible for encapsulating the application data (POJO).
- **View:** is responsible for rendering the model data.
- **Controller:** is responsible for receiving the user request, building model object and passing the model object to the view.

# Execution flow

Spring MVC framework uses the `DispatcherServlet` class as the controller which is responsible for handling all the requests and responses.


1. **Receive** the user **request**.
2. **Choose the `controller`** with the help of `HandlerMapping`.
3. Controller **process the request** by calling the appropriate `Service` method and **returns** a `ModeAndView` object to the `DispatcherServlet` which contains the model data and view name.
4. `DispatcherServlet` sends the view name to `ViewResolver` which sends **the actual view** to the DispatcherServlet.
5. `DispatcherServlet` will pass the model data to the View and **render** response.