---
title: CRA 已成为历史
published: 2023-04-08
description: cra已经被放弃了，我们该选择什么框架呢
tags: [react]
draft: false
lang: ''
category: 'tech'
---

## TL;DR

### Framework

- [Nextjs](https://nextjs.org/)
- [Remix](https://remix.run/)
- [Gatsby](https://www.gatsbyjs.com/)
- [Expo(mobile)](https://expo.dev/)

### Without Framework

- [Vite](https://vitejs.dev/)
- [Parcel](https://parceljs.org/)

多年来，CRA 一直是 React 官方推荐的脚手架工具。然而，最近@t3dotgg 在 GitHub 的 issue 上提议将 CRA 从官方文档中移除，引起了很多人的讨论。

@Dan 也解释说，最初的 CRA 是因为当时 React 没有很好的工具来连接使用 JSX 必须安装的一大堆工具，而 CRA 出现就是为了解决这个问题。如今已经是 2023 年，有很多新的工具和框架出现了，如 Vite、Next.js 和 Remix，它们可以带来更好的开发体验。

[React 官网](https://react.dev/) 的确取消了对 CRA 的支持，推荐使用 Next.js、Remix 和 Vite 等工具和框架。

CRA 的目标：

- 提供一种无需配置即可开始新的 React 项目的简单方法
- 集成与编译相关的依赖项，使其易于升级
- 让 React 团队尽可能广泛地部署工具更新（例如 Fast Refresh 支持、Hooks lint 规则）

CRA 的缺点：

- 官方没有经常维护，有太多的 issue
- 隐藏了 babel 和 webpack 配置，如果要自定义 webpack，需要额外安装类似于 [carco](https://github.com/dilanx/craco) 或者 [react-app-rewired](https://github.com/timarney/react-app-rewired) 等工具，心智成本太高

现阶段框架的优势：

- 充分利用 Web API，无论应用程序大小是小还是大，都可以提供快速的应用程序和网站
- 充分利用 React 本身及其框架级特性
- 提供路由和数据获取，让开发更为便捷

> [https://github.com/reactjs/reactjs.org/pull/5487#issuecomment-1409720741](https://github.com/reactjs/reactjs.org/pull/5487#issuecomment-1409720741)
