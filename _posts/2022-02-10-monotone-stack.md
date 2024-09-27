---
layout: post
section-type: post
has-comments: true
title: "Monotone Stack"
category: algorithm
---

```java
//stack elements in decrease order
Deque<Integer> stack = new ArrayDeque<Integer>();
for (int i = 0; i < n; i++) {
		//nums[i] is nextBig of some of stack elements ranged top 
		while (!stack.isEmpty() && nums[i] > nums[stack.peek()]) {
				nextBig[stack.pop()] = i;
		}
		//stack contais index of nums[]
		stack.push(i);
}
```