---
layout: post
section-type: post
has-comments: true
title: "Inheritance"
category: javascript
---

# prototypal inheritance

> Use **parent’s instance** as child’s prototype.
> 

```jsx
function Parent () {
    this.name = 'kevin';
}

Parent.prototype.getName = function () {
    console.log(this.name);
}

function Child () {

}

Child.prototype = new Parent();

var child1 = new Child();

console.log(child1.getName()) // kevin
```

Advantages:

- Reuse parent’s methods.

Disadvantages:

- Parent’s reference property is shared by all children.

```jsx
function Parent () {
    this.names = ['kevin', 'daisy'];
}

function Child () {

}

Child.prototype = new Parent();

var child1 = new Child();

child1.names.push('yayu');

console.log(child1.names); // ["kevin", "daisy", "yayu"]

var child2 = new Child();

console.log(child2.names); // ["kevin", "daisy", "yayu"]
```

- Child can’t pass parameters to parent when creating instance.

# constructor inheritance

> **Copy** parent’s constructor to child’s constructor.
> 

```jsx
function Parent () {
    this.names = ['kevin', 'daisy'];
}

function Child (name) {
    Parent.call(this, name);
}

var child1 = new Child('kevin');

child1.names.push('yayu');

console.log(child1.names); // ["kevin", "daisy", "yayu"]

var child2 = new Child('daisy');

console.log(child2.names); // ["kevin", "daisy"]
```

Advantages:

- Parent’s reference property isn’t shared.
- Child can pass parameters to parent when creating instance.

Disadvantages:

- Parent’s methods can’t be reused. Child’s instance methods are created individually every time.

# combination inheritance

> **Combine** prototypal and constructor inheritance.
> 

```jsx
function SuperType() {
   this.name = 'parent';
   this.arr = [1, 2, 3];
}
 
SuperType.prototype.say = function() {
   console.log('this is parent')
}
 
function SubType() {
   SuperType.call(this) 
}
 
SubType.prototype = new SuperType() 
```

Advantages:

- Reuse parent’s methods.
- Parent’s reference property isn’t shared.
- Child can pass parameters to parent when creating instance.

Disadvantages:

- Call parent constructor twice and waste performance.

# **Parasitic Combination Inheritance**

> Retrieve a shallow **copy of target object** and enhance.
> 

```jsx
function inheritPrototype(subType, superType){
 
   var prototype = object(superType.prototype); 
 
   prototype.constructor = subType;             
 
   subType.prototype = prototype;               
 
}
 
function SuperType(name){
 
   this.name = name;
 
   this.colors = ["red", "blue", "green"];
 
}
 
SuperType.prototype.sayName = function(){
 
   alert(this.name);
 
};
 
function SubType(name, age){
 
   SuperType.call(this, name);
 
   this.age = age;
 
}
 
 
inheritPrototype(SubType, SuperType);
 
SubType.prototype.sayAge = function(){
 
   alert(this.age);
 
}
```