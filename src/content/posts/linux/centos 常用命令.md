---
title: centos 常用命令
published: 2024-04-16
description: "centos 常用命令"
tags: ["linux"]
category: linux
draft: false
---

### 仅限我个人常用
```shell
# 修改 shell 配置文件和编译配置
vim ~/.zshrc
vim ~/.bashrc
source ~/.zshrc
source ~/.bashrc

# 查看当前终端
echo $SHELL
# 查看所有可使用的终端
cat /etc/shells
# 切换终端
chsh -s /bin/zsh

# .gz 解压缩
gzip -d file.gz
```