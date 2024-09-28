---
layout: post
section-type: post
has-comments: true
title: "StackOverFlow"
category: java
---

## Cause

**Not provided the proper terminating condition** to our recursive function or template, which means it will turn into an infinite loop.
    
When we **invoke a method**, a **new stack frame** is created on the call stack or on the thread stack size. This stack frame holds parameters of the invoked method, mostly the local variables and the return address of the method. The creation of these stack frames will be **iterative** and will be **stopped** only when **the end of the method invokes** is found in the nested methods. If JVM **runs out of space for the new stack frames** which are required to be created, it will throw a `StackOverflowError`.
    

```java
// Java program to demonstrate
// infinite recursion error

public class StackOverflowErrorClass {
	static int i = 0;

	// Method to print numbers
	public static int printNumber(int x)
	{
		i = i + 2;
		System.out.println(i);
		return i + printNumber(i + 2);
	}

	public static void main(String[] args)
	{
		// Recursive call without any
		// terminating condition
		StackOverflowErrorClass.printNumber(i);
	}
}
```
<br>

## Fix

1. **Avoiding repetitive calls**
    
    Try to **introduce a proper terminating condition** or some condition for the recursive calls to ensure that it terminates.
    
2. **Increasing the Stack Size**
If you notice that it’s **implemented correctly** but still we see an error, then we can avoid that only by increasing the Stack Size in order to store the required number of recursive calls. This is achieved by **changing the settings of the compiler**.

3. **Avoid** **Cyclic Relationships between classes**
    
    The relationship caused when two different **classes instantiate each other inside their constructors**.
    
    ```java
    // Java Program to demonstrate
    // cyclic relationship between class
    
    public class A1 {
    	public A2 type2;
    	public A1()
    	{
    		// Constructor of A2 is called
    		// hence object of A2 is created
    		type2 = new A2();
    	}
    
    	public static void main(String[] args)
    	{
    		// Cycle is started by
    		// invoking constructor of class A1
    		A1 type1 = new A1();
    	}
    }
    
    class A2 {
    	public A1 type1;
    	public A2()
    	{
    		// Constructor of A1 is called
    		// hence object of A1 is created
    		type1 = new A1();
    	}
    }
    ```