---
layout: post
section-type: post
has-comments: true
title: "lazy VS lateinit"
category: android
---

1. **lateinit `var` whereas lazy `val`**
    
    A lateinit property can be reinitialized, but lazy property an only be initialized once.
    
2. **lateinit can’t have custome `getter` and `setter` whereas lazy has custom `getter`**
    
    A lazy property has a block executed the first time that property is called.
    
3. **Primitive types**
    
    lateinit properties can’t be of primitive types, but lazy properties can.
    
4. **Thread safety**
    
    We can’t define thread safety in lateinit, but we can define in case of lazy.
    
    ```kotlin
    val lazyUser : User? by lazy(LazyThreadSafetyMode.SYNCHRONIZED) {
            User(id = 1, username = "agrawalsuneet")
        }
    ```
    
5. **Nullable type**
    
    A lazy property can be `null`, but lateinit can’t be `null`.