---
layout: post
section-type: post
has-comments: true
title: "Memory Model"
category: java
---
# Memory Model

> The Java Virtual Machine defines various **run-time data areas** that are used during execution of a program.
> 


### Heap

- Created during the virtual machine **startup**
- Allocated for all **class instances** and **arrays**
- A fixed or dynamic **size**

> Programmer control the max and min size, be careful `OutOfMemory`.

- The memory does **not** need to be **contiguous**
- **Shared** by threads

### Method Area

- Runtime Constant Pool
    - Numerical constant
    - Class attribute reference
    - Method reference
- Field Data: the name, type…of each **class**
- Method Data: the name, return value type, parameter list... of each **method**
- Method Code: bytecode, local variable table... of each **method**
- May be of a fixed **size** or may be expanded
- The memory does **not** need to be **contiguous**

### Stack

- When the thread starts, a **runtime stack** will be assigned to the thread.
- The stack stores **frames**. A frame is used to store **data** and **partial results** and to **return** values for methods, and dispatch **exceptions**.
- May be of a fixed **size** or may be expanded
- The memory does **not** need to be **contiguous**

### **Native method stacks**

- Support **native methods**
    - Methods are written in a language **other than the Java** programming language such as C/C++.
        
        To load native method, we'll use the `System.loadLibrary`.
        
        Place the call in a `static` **block so that it is available in our class:
        
        ```java
        public class DateTimeUtils {
        
        	public native String getSystemTime();
        
        	static {
               System.loadLibrary("nativedatetimeutils");
          }
        }
        ```
        
- Allocated per **each thread** when each thread is created.
- Java Virtual Machine implementations that **cannot load** native methods and that do **not** themselves **rely on stacks** need **not supply** native method stacks.
- **Size** can be either fixed or dynamic.

### P**rogram Counter (**PC) Register

- **Each** of the JVM **threads** has its own pc register
- Save the **non-native** **code address** of the current execution (memory address in the method area) and if the method is **native**, the value of the PC register is **undefined**.