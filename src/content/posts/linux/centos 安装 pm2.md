---
title: centos 安装 pm2
published: 2024-04-15
description: "centos 安装 pm2"
tags: ["linux"]
category: linux
draft: false
---

### 安装 pm2
> npm install pm2 -g

### 启动 pm2
> pm2 start app.js

### 查看 pm2 运行状态
> pm2 list

> pm2 ls

### 停止 pm2
> pm2 stop app.js

### 删除 pm2
> pm2 delete [appname] | [appid]

> pm2 delete all

### 重启 pm2
> pm2 restart app.js

### pm2 重命名应用加监听
> pm2 start app.js --name my-api

> pm2 start app.js --name my-api --watch

### pm2 开机启动
> pm2 startup

### 查看进程详情
> pm2 describe app

> pm2 show [name]

### 查看内存使用状态
> pm2 monit

### pm2 保存当前进程列表
> pm2 save

### 查看日志
> pm2 log [name]

### 集群启动
> pm2 start app.js -i max