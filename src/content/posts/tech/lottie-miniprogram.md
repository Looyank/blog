---
title: 小程序使用 lottie-miniprogram 问题
published: 2023-11-16
description: 小程序使用 lottie 动画不清晰以及 windows 出现的bug
tags: [miniprogram]
category: 'tech'
draft: false
lang: ''
---

# lottie-miniprogram

在小程序业务中使用 UI 同学给的 json 文件，使用 lottie 做成动画时，遇到两个问题。

- 动画有齿痕，不清晰
- windows 上会报错，`TypeError: Cannot read properties of undefined (reading 'requestAnimationFrame')`

解决方案：

- 不清晰

```js {3-6}
const canvas = res.node;
const context = canvas.getContext('2d');
const { pixelRatio: dpr = 2 } = systemInfo.value;
canvas.width = 56 * dpr;
canvas.height = 56 * dpr;
context.scale(dpr, dpr);
lottie.setup(canvas);
```

- window bug

```js
const myAnim = lottie.loadAnimation({});
// 卸载或者不使用的时候需要暂停
onUnload(() => {
  myAnim?.pause();
});
```
