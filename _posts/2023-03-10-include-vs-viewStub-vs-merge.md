---
layout: post
section-type: post
has-comments: true
title: "Include VS ViewStub VS Merge"
category: android
---

## <include />

> Reuse other layouts.
> 

## <merge />

> Delete redundant levels and optimize UI.
> 

### Use include

layout1.xml

```xml
<FrameLayout>
   <include layout="@layout/layout2"/>
</FrameLayout>
```

layout2.xml

```xml
<FrameLayout>
   <TextView />
</FrameLayout>
```

It actually looks like:

```xml
<FrameLayout>
   <FrameLayout>
      <TextView />
   </FrameLayout>
</FrameLayout>
```

### Use merge

layout1.xml

```xml
<FrameLayout>
   <include layout="@layout/layout2"/>
</FrameLayout>
```

layout2.xml

```xml
<merge>
   <TextView />
</merge>
```

It actually looks like:

```xml
<FrameLayout>
   <TextView />
</FrameLayout>
```

## <ViewStub />

> An invisible view with 0 height and 0 width. Loading of this view has been delayed to optimize UI rendering. Only take a placeholder when first rendering.
>