---
title: structuredClone 用途
published: 2023-03-16
description: ECMAScript 2021 出来的新特性 structuredClone ，就再也不需要使用 JSON.parse(JSON.stringify(obj))
tags: [js]
category: 'tech'
draft: false
lang: ''
---

# structuredClone

`ECMAScript 2021` 出来的新特性 `structuredClone` ，就再也不需要使用`JSON.parse(JSON.stringify(obj)`

## TL;DR;

`structuredClone` 不能克隆以下情况：

- Function
- DOM
- Property description: getter / setter
- Object prototypes

除此之外的克隆需要，都可以用`structuredClone` ，可以覆盖大部分场景了。

## 介绍

`structuredClone` 是内置在 `JavaScript` 中的。功能 ≥ `JSON.parse(JSON.stringify())`

我们先看看在实战中的作用

```jsx
const obj = {
  name: 'demo',
  date: new Date(),
  arr: [{ a: 1 }, { b: 2 }],
  set: new Set([1, 2, 1]),
  map: new Map([[1, 2]]),
  regex: /test/,
  error: new Error('test'),
};

obj.circular = obj;

const clone = structuredClone(obj); //  ✅
```

有了上述明显的代码展示，一下子就能看出来和平常我们用的 `JSON.parse`的区别了。

`struturedClone` 不仅是深度克隆，还可以克隆时间，正则，甚至循环引用！!

## 总结

[structuredClone](https://caniuse.com/?search=structuredClone) 算是一个较新的 API ， 在内部项目或者 side project，我们都可以使用最新的 API 来进行开发，感受一下新技术的便捷。该 API 可以覆盖大部分的场景了，满足日常的克隆需要～ 以后就用它！

> [structuredClone() - Web APIs | MDN](https://developer.mozilla.org/en-US/docs/Web/API/structuredClone)
