---
layout: post
section-type: post
has-comments: true
title: "Render Function"
category: vue
---

Render function is a normal function which receives a `createElement` method as it’s first argument used to **create virtual nodes**. Internally Vue.js' templates actually compile down to render functions at build time. Hence templates are just syntactic sugar of render functions.

```jsx
<template>
  <div :class="{'is-rounded': isRounded}">
    <p>Welcome to Vue render functions</p>
  </div>
</template>
```

and the compiled down or explicit render function would appear as below,

```jsx
render: function (createElement) {
  return createElement('div', {
    'class': {
      'is-rounded': this.isRounded
     }
  }, [
    createElement('p', 'Welcome to Vue render functions')
  ]);
}
```