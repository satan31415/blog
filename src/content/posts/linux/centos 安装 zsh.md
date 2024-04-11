---
title: centos 安装 zsh
published: 2024-04-11
description: "centos 安装 zsh 和 oh-my-zsh 以及插件"
tags: ["linux"]
category: linux
draft: false
---

### 安装 zsh

```bash
yum install -y zsh
```

### 设置zsh为默认的shell(要确保在root下执行)
```bash
chsh -s /bin/zsh
```

### 安装oh-my-zsh
```
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"

sh -c "$(wget -O- https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

### oh-my-zsh常用插件
```bash
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting

git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions

git clone https://github.com/zsh-users/zsh-completions ${ZSH_CUSTOM:=~/.oh-my-zsh/custom}/plugins/zsh-completions

# 或者国内
git clone https://gitee.com/mo2/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting

git clone https://gitee.com/twd2606/zsh-autosuggestions.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions

git clone https://gitee.com/wangnd/zsh-completions.git ${ZSH_CUSTOM:=~/.oh-my-zsh/custom}/plugins/zsh-completions
```

### 修改配置文件
- `vim ~/.zshrc`
- `source .zshrc`

```
# 取消第二行的注释
export PATH=$HOME/bin:/usr/local/bin:$PATH

plugins=(git zsh-completions zsh-autosuggestions zsh-syntax-highlighting)
autoload -U compinit && compinit
```