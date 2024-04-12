---
title: centos 安装 nginx
published: 2024-04-11
description: "centos 安装 nginx"
tags: ["linux"]
category: linux
draft: false
---

### 安装 nginx

```
sudo yum update
sudo yum install nginx

# 启动 nginx
sudo systemctl start nginx

# 开机启动 nginx
sudo systemctl enable nginx

# 查看 nginx 状态
sudo systemctl status nginx

# nginx 常用命令(停止, 重启, 重新加载配置文件)
sudo systemctl stop nginx
sudo systemctl restart nginx
sudo systemctl reload nginx
```