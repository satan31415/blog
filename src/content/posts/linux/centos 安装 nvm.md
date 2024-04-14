---
title: centos 安装 nvm
published: 2024-04-14
description: "centos 安装 nvm"
tags: ["linux"]
category: linux
draft: false
---

### 通过 git 安装
> cd /home

> git clone https://github.com/nvm-sh/nvm.git

> sh ./nvm/install.sh

### 修改配置文件
```shell
# 查看终端
echo $SHELL
# 如果是默认终端
vim ~/.bash_profile
# 或者 zsh
vim ~/.zshrc
# 把环境变量复制进去
export NVM_DIR="$([ -z "${XDG_CONFIG_HOME-}" ] && printf %s "${HOME}/.nvm" || printf %s "${XDG_CONFIG_HOME}/nvm")"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"
# 编译配置文件
source ~/.bash_profile
# zsh 编译配置文件
source ~/.zshrc
```

### nvm 常用命令
```shell
nvm -v
# 查看下载的 node 版本 
nvm ls 
# 查看当前使用的版本
nvm current
# 查看所有 node 版本
nvm list-remote
# 安装指定版本
nvm install 16.18.1
# 删除指定版本
nvm uninstall 16.18.1
# 切换 node 版本
# nvm use 16.18.1
```

