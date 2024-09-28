---
layout: post
section-type: post
has-comments: true
title: "Sealed Class VS Enum Class"
category: kotlin
---

# **Sealed Class**

> Sealed classes provide a hierarchy of classes that have **subclasses** that we can only declare at compile time.
> 

```kotlin
sealed class OsSealed(val releaseYear: Int = 0, val company: String = "") {
    constructor(company: String) : this(0, company)

    object Linux : OsSealed("Open-Source") {
        fun getText(value: Int): String {
            return "Linux by $company - value=$value"
        }
    }

    object Windows : OsSealed("Microsoft") {
        fun getNumber(value: String): Int {
            return value.length
        }
    }

    object Mac : OsSealed(2001, "Apple") {
        fun doSomething(): String {
            val s = "Mac by $company - released at $releaseYear"
            println(s)
            return s
        }
    }

    object Unknown : OsSealed()

    fun getTextParent(): String {
        return "Called from parent sealed class"
    }
}
```
<br>
# **Enum Class**

> We use an enum class to relate each enum **constant** with its parent.
> 

```kotlin
enum class OsEnum(val releaseYear: Int = 0, val company: String = "") {
    Linux(0, "Open-Source") {
        override fun getText(value: Int): String {
            return "Linux by $company - value=$value"
        }
    },
    Windows(0, "Microsoft") {
        override fun getText(value: Int): String {
            return "Windows by $company - value=$value"
        }
    },
    Mac(2001, "Apple") {
        override fun getText(value: Int): String {
            return "Mac by $company - released at $releaseYear"
        }
    },
    Unknown {
        override fun getText(value: Int): String {
            return ""
        }
    };

    abstract fun getText(value: Int): String

    fun getTextParent(): String {
        return "Called from parent enum class"
    }
}
```
<br>
# **Sealed Class vs Enum**

- **In a sealed class, we can simply add multiple custom constructors depending on what we need.** Furthermore, we can define multiple functions with different names, parameters, and return types.
- **In an enum class, we can’t define different functions in each enum constant.** Therefore, we had to implement a method that we didn’t need for that constant.
