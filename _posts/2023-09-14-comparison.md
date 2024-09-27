---
layout: post
section-type: post
has-comments: true
title: "Comparison"
category: javascript
---

# == Vs ===

```jsx
1 == '1'; // true
1 == [1]; // true
1 == true; // true
0 == ''; // true
0 == '0'; // true
0 == false; // true

1 === 1   //true
1 === '1'   // false
```

# **function Person(){}, var person = Person(), var person = new Person()**

- `function Person(){}` is just a normal function declaration.
- `var person = Person()` invokes the `Person` as a function, and not as a constructor. Invoking the constructor like a normal function will return `undefined`.
- `var person = new Person()` creates an instance of the `Person` object using the `new` operator.

```jsx
function Person(name) {
  this.name = name;
}

var person = Person('John');
console.log(person); // undefined
console.log(person.name); // Uncaught TypeError: Cannot read property 'name' of undefined

var person = new Person('John');
console.log(person); // Person { name: "John" }
console.log(person.name); // "john"
```

# .forEach Vs .map

```jsx
const a = [1, 2, 3];
const doubled = a.forEach((num, index) => {
  // Do something with num and/or index.
});

// doubled = undefined
```

```jsx
const a = [1, 2, 3];
const doubled = a.map((num) => {
  return num * 2;
});

// doubled = [2, 4, 6]
```

The main difference between `.forEach` and `.map()` is that `.map()` returns a **new array**. If you need the result, but do not wish to mutate the original array, `.map()` is the clear choice. If you simply need to iterate over an array, `forEach` is a fine choice.

# **.call Vs .apply Vs .bind**

## bind()

> Enables calling a **function** with a specified “this” value.
> 

```jsx
var car = { 
    registrationNumber: "GA12345",
    brand: "Toyota",

    displayDetails: function(){
        console.log(this.registrationNumber + " " + this.brand);
    }
}
car.displayDetails(); // GA12345 Toyota

var myCarDetails =  car.displayDetails;
myCarDetails();

var myCarDetails = car.displayDetails.bind(car); 
myCarDetails(); // GA12345 Toyota
```

## call() and apply()

> Using `apply()` function, the parameter must be placed in an **array**. `call()` accepts both an array of parameters and a parameter itself.
> 

```jsx
var car = { 
    registrationNumber: "GA12345",
    brand: "Toyota"
}

function displayDetails(ownerName) {
    console.log(ownerName + ", this is your car: " + this.registrationNumber + " " + this.brand);
}

displayDetails.apply(car, ["Vivian"]); // Vivian, this is your car: GA12345 Toyota

displayDetails.call(car, "Vivian"); // Vivian, this is your car: GA12345 Toyota
```

# **load Vs DOMContentLoaded**

- `DOMContentLoaded` event is fired when the **initial HTML document** has been completely loaded and parsed, **without waiting** for stylesheets, images and subframes to finish loading.
- `window`'s `load` event is only fired after the **DOM** and **all** dependent resources and assets have loaded.

# let Vs var Vs const

- Variables declared using the `var` keyword are **scoped to the function** in which they are created, or if created outside of any function, to the **global object**. `let` and `const` are **block scoped**, meaning they are only accessible within the nearest set of curly braces(function, if-else block or for-loop).
- `var` allows variables to be **hoisted**, meaning they can be referenced in code before they are declared. `let` and `const` will **not allow** this, instead throwing an error.
- `let` and `const` differ in that `let` allows **reassigning** the variable’s value while `const` does not.

# ES6 class Vs ES5 function

```jsx
// ES5 Function Constructor
function Person(name) {
  this.name = name;
}

// ES6 Class
class Person {
  constructor(name) {
    this.name = name;
  }
}
```

The main difference in the constructor comes when using **inheritance**. If we want to create a `Student` class that subclasses `Person` and add a `studentId` field, this is what we have to do in addition to the above.

```jsx
// ES5 Function Constructor
function Student(name, studentId) {
	// Call constructor of superclass to initialize superclass-derived members.
	Person.call(this, name);
	// Initialize subclass's own members.
	this.studentId = studentId;
}

Student.prototype = Object.create(Person.prototype);
Student.prototype.constructor = Student;

// ES6 Class
class Student extends Person {
	constructor(name, studentId) {
		super(name);
		this.studentId = studentId;
	}
}
```

# spread Vs rest syntax

- Spread syntax is very useful as we can easily create **copies of arrays or objects** without resorting to `Object.create`, `slice`, or a library function.

```jsx
function putDookieInAnyArray(arr) {
  return [...arr, 'dookie'];
}

const result = putDookieInAnyArray(['I', 'really', "don't", 'like']); 
// ["I", "really", "don't", "like", "dookie"]
```

- Rest syntax offers a shorthand for i**ncluding an arbitrary number of arguments** to be passed to a function. It is like an **inverse** of the spread syntax, taking data and stuffing it into an array rather than unpacking an array of data, and it works in function arguments, as well as in array and object destructuring assignments.

```jsx
const [a, b, ...rest] = [1, 2, 3, 4]; // a: 1, b: 2, rest: [3, 4]
```