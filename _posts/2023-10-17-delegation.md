---
layout: post
section-type: post
has-comments: true
title: "Delegation"
category: javascript
---

# event delegation

> Add event listeners to a **parent** element instead of adding them to the descendant elements.

- Example
    
    ```html
    <ul id="parent-list">
    	<li id="post-1">Item 1</li>
    	<li id="post-2">Item 2</li>
    	<li id="post-3">Item 3</li>
    	<li id="post-4">Item 4</li>
    	<li id="post-5">Item 5</li>
    	<li id="post-6">Item 6</li>
    </ul>
    ```
    
    You could add a separate event listener to each individual `li` element, but what if `li` elements are frequently **added and removed** from the list? The better solution is to add an event listener to the parent `ul` element.
    
    ```jsx
    // Get the element, add a click listener...
    document.getElementById("parent-list").addEventListener("click", function(e) {
    	// e.target is the clicked element!
    	// If it was a list item
    	if(e.target && e.target.nodeName == "LI") {
    		// List item found!  Output the ID!
    		console.log("List item ", e.target.id.replace("post-", ""), " was clicked!");
    	}
    });
    ```
    
    When the event bubbles up to the `ul` element, you check the event object's target property to gain a reference to the actual clicked node.
    

The benefits of this technique are:

- **Memory footprint goes down** because only one single handler is needed on the parent element, rather than having to attach event handlers on each descendant.
- There is **no need to unbind** the handler from elements that are removed and to bind the event for new elements.

# event bubbling

When an event triggers on a DOM element, it will **attempt to handle** the event if there is a listener attached, then the event is **bubbled up to its parent** and the same thing happens. This bubbling occurs up the element’s ancestors all the way to the `document`. 

# prototypal inheritance

All JS objects have a `__proto__` property, **a reference to another object**, which is called the object’s prototype. When a property is accessed on an object and if the property is not found on that object, the JS engine looks at the object’s `__proto__`, and the `__proto__`'s `__proto__` and so on, until it finds the property defined on one of the `__proto__` or until it reaches the end of the **prototype chain**. 

- Example
    
    ```jsx
    function Parent() {
      this.name = 'Parent';
    }
    
    Parent.prototype.greet = function () {
      console.log('Hello from ' + this.name);
    };
    
    const child = Object.create(Parent.prototype);
    
    child.cry = function () {
      console.log('waaaaaahhhh!');
    };
    
    child.cry();
    // waaaaaahhhh!
    
    child.greet();
    // hello from Parent
    
    child.constructor;
    // ƒ Parent() {
    //   this.name = 'Parent';
    // }
    
    child.constructor.name;
    // 'Parent'
    ```
    
    We need to call `Object.create` in one of following ways for the prototype methods to be inherited:
    
    - Object.create(Parent.prototype);
    - Object.create(new Parent(null));
    - Object.create(objLiteral);