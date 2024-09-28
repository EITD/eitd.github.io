---
layout: post
section-type: post
has-comments: true
title: "Lifecycle"
category: react
---

1. **Initial Rendering Phase**: This is the phase when the component is about to start its life journey and make its way to the DOM.
2. **Updating Phase**: Once the component gets added to the DOM, it can potentially update and re-render only when a prop or state change occurs. That happens only in this phase.
3. **Unmounting Phase**: This is the final phase of a component’s life cycle in which the component is destroyed and removed from the DOM.

# Methods

1. **componentWillMount()** – Executed just before rendering takes place both on the client as well as server-side.
2. **componentDidMount()** – Executed on the client side only after the first render.
3. **componentWillReceiveProps()** – Invoked as soon as the props are received from the parent class and before another render is called.
4. **shouldComponentUpdate()** – Returns true or false value based on certain conditions. If you want your component to update, return **true** else return **false**. By default, it returns false.
5. **componentWillUpdate()** – Called just before rendering takes place in the DOM.
6. **componentDidUpdate()** – Called immediately after rendering takes place.
7. **componentWillUnmount()** – Called after the component is unmounted from the DOM. It is used to clear up the memory spaces.