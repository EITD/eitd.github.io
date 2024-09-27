---
layout: post
section-type: post
has-comments: true
title: "RecyclerView"
category: android
---

## As ListView Improvement

1. **Reuses cells while scrolling up/down** - It’s optional to implement `ViewHolder` in the `ListView` adapter, while in the `RecycleView` it's the default way of writing adapter.
2. **Decouples list from its container** - Put list items easily **at run time** in the **different containers** (linearLayout, gridLayout) with setting `LayoutManager`.
    
    *Example:*
    
    ```java
    mRecyclerView = (RecyclerView) findViewById(R.id.my_recycler_view);
    mRecyclerView.setLayoutManager(new LinearLayoutManager(this));
    //or
    mRecyclerView.setLayoutManager(new GridLayoutManager(this, 2));
    ```
    
3. **Animates common list actions** - Animations are decoupled and delegated to `ItemAnimator`.