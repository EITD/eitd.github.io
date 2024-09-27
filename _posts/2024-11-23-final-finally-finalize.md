---
layout: post
section-type: post
has-comments: true
title: "Final, Finally, Finalize"
category: java
---

## **Final**

> **Inheritance** of a final class and **overriding** of a final method is **restricted** and the variable value becomes **fixed**.
> 

```java
final int a = 100;
a = 0;  // error
```

## **Finally**

> It is the block where all the codes written inside it **get executed** irrespective of handling of exceptions.
> 

```java
try {
	int variable = 5;
}
catch (Exception exception) {
	System.out.println("Exception occurred");
}
finally {
	System.out.println("Execution of finally block");
}
```

### Possibly not executed

1. Suppose we use `System.exit()` in the above statement.
2. If there are **fatal errors** like Stack overflow, Memory access error.

## **Finalize**

> **Prior to the garbage collection** of an object.
> 

```java
public static void main(String[] args) {
	String example =new String("InterviewBit");
	example =null;
	System.gc(); // Garbage collector called
}
public void finalize() {
	// Finalize called
}
```