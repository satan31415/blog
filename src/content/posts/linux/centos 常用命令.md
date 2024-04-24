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
# 服务器重启
reboot
# ls 列出文件
ls

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

# 验证代理是否生效
curl ip.gs
curl I google.com

# 文件移动 -i 询问是否覆盖
mv -i file1 file2
# 文件复制 -i 询问是否覆盖
cp -i file1 file2
# 文件删除
rm -rf file
# 文件重命名
mv file1 file2
# 创建文件夹
mkdir folder
# 创建文件
touch file
```