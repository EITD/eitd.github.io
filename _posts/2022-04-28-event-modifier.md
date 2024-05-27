---
layout: post
title: "Event Modifier"
category: vue
---

```jsx
<div id="app">
    <div @click="divClick">
        <button @click.stop="btnClick">btn1</button>
    </div>
    <form action="www.baidu.com">
      <button type="submit" @click.prevent="submitClick">submit</button>
    </form>
    <input type="text" @click.enter="keyup">

  </div>
```