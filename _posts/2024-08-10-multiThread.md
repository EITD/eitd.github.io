---
layout: post
section-type: post
has-comments: true
title: "MultiThread"
category: java
---

## Inherit java.lang.Thread

```java
public class ThreadTest02 {
    public static void main(String[] args) {
        MyThread t = new MyThread();
        t.start();
        for(int i = 0; i < 1000; i++){
            System.out.println("main thread--->" + i);
        }
    }
}

class MyThread extends Thread {
    @Override
    public void run() {
        for(int i = 0; i < 1000; i++){
            System.out.println("sub thread--->" + i);
        }
    }
}
```

### run()

`t.run()` is just an ordinary calling method. **No new branch stack** will be allocated. (This is a single thread.)


### start()

`t.start()` **starts a branch thread** and **open up a new stack** space in the JVM. After the code task is completed, it will end in an instant.

As long as the new stack space is **opened**, the `start()` method will **end**. The thread started successfully and will automatically **call** the `run()` method. `run()` and `main()` are equal level.


## Implement java.lang.Runnable Interface

```java
public class ThreadTest03 {
    public static void main(String[] args) {
        Thread t = new Thread(new MyRunnable()); 
        // 启动线程
        t.start();
        
        for(int i = 0; i < 100; i++){
            System.out.println("main thread--->" + i);
        }
    }
}

class MyRunnable implements Runnable {
    @Override
    public void run() {
        for(int i = 0; i < 100; i++){
            System.out.println("sub thread--->" + i);
        }
    }
}
```

### use Anonymous internal class

```java
public class ThreadTest04 {
    public static void main(String[] args) {
        Thread t = new Thread(new Runnable(){
            @Override
            public void run() {
                for(int i = 0; i < 100; i++){
                    System.out.println("t thread---> " + i);
                }
            }
        });

        t.start();

        for(int i = 0; i < 100; i++){
            System.out.println("main thread---> " + i);
        }
    }
}
```

### Advantage

<aside>
💡 The class implements an interface and it can inherit other class, which is more flexible.

</aside>