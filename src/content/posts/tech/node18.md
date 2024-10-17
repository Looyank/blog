---
title: Node18 都有啥功能
published: 2022-12-08
description: node18 版本已经成为 LTS 了，还在用 node ≤ 16 吗，看看都更新了啥
tags: [node]
image: ''
category: 'tech'
draft: false
lang: ''
---

Node 18 已经成为了 LTS 版本，都更新了啥

## 1.内置了 Fetch Api

在 Node 18 版本之前，我们需要安装 `node-fetch` 或者 `axios` 去发起请求，在 Node 18 中，就不在需要安装这些了。

看下在 Node18 中如何发起请求

```js filename="index.js"
fetch('https://jsonplaceholder.typicode.com/todos/1')
  .then((response) => response.json())
  .then((json) => console.log(json));
```

写完之后我们运行一下

```js
➜ node index.js

(node:30887) ExperimentalWarning: The Fetch API is an experimental feature. This feature could change at any time
(Use `node --trace-warnings ...` to show where the warning was created)
{ userId: 1, id: 1, title: 'delectus aut autem', completed: false }
```

## 2.内置了 test 模块

之前我们要进行单元测试的时候，需要安装 `Jest`、`Mocha`、`Chai` 等等。

现在我们只需要导入自带的 `test` 模块。

接下来看看该如何使用他。

```js filename="index.mjs"
export const sum = (a, b) => a + b;
```

```js filename="test.mjs"
import test from 'node:test';
import assert from 'node:assert/strict';
import { sum } from './index.mjs';

test('sum', async (t) => {
  await t.test('true', () => {
    assert.equal(sum(2, 8), 10);
  });
  await t.test('false', () => {
    assert.notEqual(sum(2, 5), 8);
  });
});
```

运行下看下结果

```js
➜ node test.mjs

TAP version 13
# Subtest: sum
    # Subtest: true
    ok 1 - true
      ---
      duration_ms: 0.621862
      ...
    # Subtest: false
    ok 2 - false
      ---
      duration_ms: 0.135985
      ...
    1..2
ok 1 - sum
  ---
  duration_ms: 3.034993
  ...
1..1
# tests 1
# pass 1
# fail 0
# cancelled 0
# skipped 0
# todo 0
# duration_ms 7.669003
```

## 3.支持 Web Streams API

具体参考[MDN](https://developer.mozilla.org/en-US/docs/Web/API/Streams_API)

## 4.hmr

现在我们不再需要安装 `nodemon` 插件来监听文件变化 hmr 了，可以使用 `--watch` 来监听文件变动

```js
node --watch index.js
```

## 5.支持 import JSON

```js
import json from './package.json' assert { type: 'json' };
console.log(json);
```

> 该实验性功能可能会随时移除

## 参考

> https://nodesource.com/blog/11-features-nodeJS-18-to-try
