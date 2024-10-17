---
title: 快捷键打开vscode项目
published: 2023-04-06
description: 尽管有Raycast来快速的搜索打开项目，但是有时候我们还是会需要这种方式
tags: [skills]
image: ''
category: 'tech'
draft: false
lang: ''
---

因为频繁用 vscode 打开文件夹，尽管有 Raycast 直接用快捷命令打开会更加方便许多，不用搜索等等。但是有时候记不起来项目名字，在目录中找到之后，还要拖动到 vscode 中，很是不方便，在 Mac 下，我们可以直接用 Automator 配置 Quick Action 来使用快捷键打开。

1. 先选择 Quick Action 配置来初始化。

![quick action](../images/shortcuts1.png) 2. 按照图上配置

```bash
for f in "$@"
do
     open -a "Visual Studio Code" "$f"
done
```

![quick action](../images/shortcuts2.png)

3. 按照此快捷打开方式就配置好了，可以右键项目在 quick aciton 查看，但是我们还是不想这么麻烦，可以再为此配置一下快捷键的方式。在键盘里面配置一下刚刚做好的 quick action 的打开方式即可

![quick action](../images/shortcuts3.png)

至此，我们就可以选中项目后，使用 `command + G` 来打开项目了。

大多数我们都可以通过 Raycast 的快速搜索打开，这个适用于记不起来名字，选中后直接快捷键打开。
