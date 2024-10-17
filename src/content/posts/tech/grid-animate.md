---
title: grid-animate
published: 2023-03-26
description: 通过 grid 属性给展开折叠加上动画效果
tags: [css]
author: BlackBerry
category: 'tech'
draft: false
lang: ''
---

# grid-animate

有一次在项目中需要做到展开折叠效果加个动画，内容是自适应的，所以不能通过设置 `height` 实现，可以通过 `max-height` 曲线救国，但是有点瑕疵的。

后来看到了浏览器支持了 `grid` 属性的动画效果，这看起很棒！

<iframe
  height="400"
  width="100%"
  scrolling="no"
  title="grid-template-rows / grid-template-columns animation (Firefox only)"
  src="https://codepen.io/michellebarker/embed/oJmZKK?default-tab=html%2Cresult"
  frameBorder="no"
  loading="lazy"
></frame>

# end

基于此，我们可以通过调整 `grid-template-rows` 来实现展开折叠的动画效果。

```html
<div class="grid">
  <div class="grid-child"></div>
</div>
```

```css
.grid {
  display: grid;
  grid-template-rows: 0fr;
  transition: grid-template-rows 0.5s ease-in-out;
}
.grid.open {
  grid-template-rows: 1fr;
}
.grid-child {
  overflow: hidden;
}
```
