---
title: Array reduce 实战
published: 2023-08-11
description: reduce 的方法在实际项目中的作用
tags: [js]
image: ''
category: 'tech'
draft: false
lang: ''
---

## 什么是 reduce

Array 上的原型方法，它接收一个函数作为累加器（accumulator），数组中的每个值（从左到右）开始缩减，最终为一个值。

使用方法就是这样

```js
arr.reduce(callback(previousValue, currentValue, currentIndex, sourceArray), [
  initValue,
]);
```

- **callback**：**reduce** 得回调函数，接收四个参数:
  - **previousValue**：累加器，即上一次回调返回的值，或者提供的初始值(initValue)
  - **currentValue**：数组中当前正在被处理的值
  - **currentIndex**： 数组中当前元素的索引（可选）
  - **sourceArray**：reduce 的源数组（可选）

回调函数第一次执行时，**previousValue** 和 **currentValue** 的取值有两种情况：如果调用 **reduce()** 时提供了 **initValue**，**previousValue** 取值为 **initValue**，**currentValue** 取数组中的第一个值；如果没有提供 **initValue**，那么 **previousValue** 取数组中的第一个值，**currentValue** 取数组中的第二个值

**initValue**：作为第一次调用 **callback** 得第一个参数的初始值。（可选）

返回值
回调函数累计处理的结果

## 举几个例子

### 求和

```js
const arr = [1, 2, 3, 4, 5];
const sum = arr.reduce((acc, cur) => acc + cur, 0);
console.log(sum); // 15
```

### 获取深层次对象

这个还挺实用，并且在一些面试还会问到

```js
const obj = {
  a: {
    b: {
      c: {
        d: '1',
      },
      e: null,
    },
  },
};

function getValue(target, key) {
  try {
    return key.split('.').reduce((r, k) => r[k], target);
  } catch (e) {
    return undefined;
  }
}

getValue(obj, 'a.b.c.d'); // 1
getValue(obj, 'a.b.e'); // null
getValue(obj, 'a.b.e.f'); // undefined
```

### 求元素出现的次数

```js
const nameList = ['张三', '李四', '王五', '王五', '王五', '李四'];
const nameNum = nameList.reduce((pre, cur) => {
  if (cur in pre) {
    pre[cur]++;
  } else {
    pre[cur] = 1;
  }
  return pre;
}, {});
```
