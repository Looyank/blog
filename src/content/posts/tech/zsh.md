---
title: zsh skills
published: 2023-03-25
description: 通过配置一些简单的命令，提升开发体验
image: ''
tags: [git]
category: 'tech'
draft: false
lang: ''
---

# zsh 小技巧

我们先运行 `man zshbuiltins` 查看说明

![manImage](../images/man.png)

通过手册例子，我们可以看到，设置 -s 后缀别名后，会替换为 `value text.name`

还是在实际中我们运用一下，看看能做什么，比如输入文件名称直接查看文件内容，当然你也可以使用 `bat`

```bash
# ./index.html => cat ./index.html
# 直接输入 index.html 就可以查看内容了
alias -s {js,json,env,md,html,css,toml}=cat
```

```bash
alias -s git="git clone --depth 1"
```

这样以后直接复制 ssh git 到终端就可以啦

![clone](../images/clone.png)
