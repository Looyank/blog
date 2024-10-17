---
title: git config 配置技巧
published: 2023-03-01
description: 切换分支 push 时，再也不需要使用git push --set-upstream origin <branch>
tags: [git]
image: ''
category: 'tech'
draft: false
lang: ''
---

当我们每次切换新分支时，通常需要执行以下命令：

`git push --set-upstream origin <branch>`

因为本地切换了分支，远程不知道这个变化，所以需要使用

`git push origin <local branch>`

命令将本地分支推送到远程。

也可以关联远程分支，通过如上的 `--set-upstream` 命令进行一次关联，以后就可以使用 `git push` 命令推送了。

按照一般规范，我们本地切换了分支，就会推送同名分支到远程，因此不需要每次都进行关联。

我们可以进行以下设置（二选一）：

1. `git config --global --add push.default current`
2. `git config --global --add push.autoSetupRemote true`

完成设置后，就不需要再执行`git push --set-upstream origin <branch>`命令了。
