---
layout: post
section-type: post
has-comments: true
title: "Clear Float"
category: css
---

# Float

Floated elements will **affect the positioning** of other elements(e.g. text will flow around floated elements). Unlike absolutely positioned elements which will not affect the position of other elements and other elements will not affect them, whether they touch each other or not.

# Clear float

> An element that has the clear property set on it will **not move up adjacent** to the float like the float desires.
> 


## clear: both

- `none` - The element is **not pushed** below left or right floated elements. This is default
- `left` - The element is pushed **below left** floated elements
- `right` - The element is pushed **below right** floated elements
- `both` - The element is pushed **below both left and right** floated elements
- `inherit` - The element inherits the clear value from its parent

## overflow: hidden

## after pseudo element

```css
.clearfix:after{
  content: "";
  display: block;
  height: 0;
  clear:both;
  visibility: hidden;
}
.clearfix{
  *zoom: 1;
｝
```