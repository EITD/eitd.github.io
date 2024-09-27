---
layout: post
section-type: post
has-comments: true
title: "Extension"
category: kotlin
---

**Advantages:**

- **No need to inherit** from the class
- **No need to modify** the existing definition of the class
- Can **add functions to an existing** class(e.g. third-party library) without accessing its source code

**Example:**

```kotlin
class Square(val side: Double){
        fun area(): Double{
        return side * side;
    }
}

// Extension function to calculate the perimeter of the square
fun Square.perimeter(): Double{
        return 4 * side;
}

// Usage
fun main(args: Array<String>){
      val square = Square(5.5);
      val perimeterValue = square.perimeter()
      println("Perimeter: $perimeterValue")
      val areaValue = square.area()
      println("Area: $areaValue")
}
```