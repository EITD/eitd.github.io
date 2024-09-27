---
layout: post
section-type: post
has-comments: true
title: "Overload VS Override"
category: java
---

## Override

```java
class Animal{
   public void move(){
      System.out.println("move");
   }
}
 
class Dog extends Animal{
   public void move(){
      System.out.println("run and walk");
   }
}
```

- Should not change parameters and return type.
- Should change implementation of the method.

## Overload

```java
		public int test(){
        System.out.println("test1");
        return 1;
    }
 
    public void test(int a){
        System.out.println("test2");
    }   

    public String test(int a,String s){
        System.out.println("test3");
        return "returntest3";
    }   
 
    public String test(String s,int a){
        System.out.println("test4");
        return "returntest4";
    }
```

- Should change parameters type, numbers, order.
- Can change access scope.
- Can change return type.