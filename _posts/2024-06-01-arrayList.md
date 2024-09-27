---
layout: post
section-type: post
has-comments: true
title: "ArrayList"
category: java
---

## ArrayList Vs Vector

Use `Object[]` to store data. ArrayList is not thread-safe, while Vector is thread-safe.

## ArrayList Vs LinkedList

1. **Thread safety**
    
    Both are not synchronized ↔ not thread-safe.
    
2. **Bottom data structure**
    
    ArrayList uses an `Object` array, while LinkedList uses a `bi-directional LinkedList` data structure.
    
3. **Insertion and deletion**
    - ArrayList: When executing the `add(E e)` method, ArrayList appends the specified element to the end of this list by default, which is **O(1)**. However, if you insert and delete elements at the specified position i (`add(int index, E element)`), the time complexity is **O(n-i)**, because the (n-i) elements after the i and i elements move one bit back /forward.
    - LinkedList: For the `add(E e)` method, the time complexity is similar to **O(1)**. If you insert and delete elements at the specified position i (`add(int index, E element)`), the time complexity is approximately **O(n)** because it needs to be moved to the specified position before inserted.
4. **Random access**
    
    LinkedList does not support random element access, while ArrayList supports it. 
    
5. **Memory space occupancy**
    
    ArrayList reserves a certain capacity of space at the **end** of the list, while LinkedList's each element needs to consume more space, because `next` , `pre` and data are stored.