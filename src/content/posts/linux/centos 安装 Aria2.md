---
title: centos 安装 Aria2
published: 2024-05-15
description: "centos 安装 Aria2"
tags: ["linux"]
category: linux
draft: false
---

### Aria2 是啥
- aria2 是一个轻量级的多协议和多来源命令行下载实用程序。它支持 HTTP/HTTPS、FTP、BitTorrent 和 Metalink。aria2 可以通过多个连接下载文件，这样可以提高下载速度。aria2 还支持 HTTP 代理和 SOCKS 代理。

### 安装 Aria2
```bash
yum install aria2
```

### 配置 Aria2
```bash
# 先查看下有没有安装成功
aria2c -v
# 创建下载目录
mkdir /root/Ariadown
# 赋予权限
chmod -R 755 /root/Ariadown
# 创建储存配置文件，以及会话信息文件夹
mkdir /root/Aria2
touch /root/Aria2/aria2.session
vi /root/Aria2/aria2.conf
```

### 配置文件信息
- 就是这个文件 /root/Aria2/aria2.conf, 把下面配置复制进去就好了
- 下面 rpc-secret=改为你的密码, 这个密码是用来连接 Aria2 的密码
- 其他的都不用改
```text
#文件保存路径, 默认为当前启动位置
dir=/root/Ariadown
# 在Aria2退出时保存`错误/未完成`的下载任务到会话文件
input-file=/root/Aria2/aria2s.session
save-session=/root/Aria2/aria2s.session
# RPC监听端口, 端口被占用时可以修改, 默认:6800
rpc-listen-port=6800
# 设置的RPC授权令牌, v1.18.4新增功能, 取代 --rpc-user 和 --rpc-passwd 选项
rpc-secret=改为你的密码
#基本需要修改的结束
# 断点续传
continue=true
# 最大同时下载任务数, 运行时可修改, 默认:5
max-concurrent-downloads=5
# 单个任务最大线程数, 添加时可指定, 默认:5
split=30
# 最小文件分片大小, 添加时可指定, 取值范围1M -1024M, 默认:20M
min-split-size=10M
# 同一服务器连接数, 添加时可指定, 默认:1
max-connection-per-server=16
# 断开速度过慢的连接
lowest-speed-limit=0
# 整体下载速度限制, 运行时可修改, 默认:0
#max-overall-download-limit=0
# 单个任务下载速度限制, 默认:0
#max-download-limit=0
# 整体上传速度限制, 运行时可修改, 默认:0
#max-overall-upload-limit=0
# 单个任务上传速度限制, 默认:0
#max-upload-limit=0
# 禁用IPv6, 默认:false
#disable-ipv6=true
# 当服务器返回503错误时, aria2会尝试重连
# 尝试重连次数, 0代表无限, 默认:5
max-tries=0
# 重连冷却, 默认:0
#retry-wait=0
## 进度保存相关 ##
# 定时保存会话, 0为退出时才保存, 需1.16.1以上版本, 默认:0
save-session-interval=30
# 强制保存会话, 即使任务已经完成, 默认:false
# 较新的版本开启后会在任务完成后依然保留.aria2文件
#force-save=false
## RPC相关设置 ##
# 启用RPC, 默认:false
enable-rpc=true
# 允许所有来源, 默认:false
rpc-allow-origin-all=true
# 允许非外部访问, 默认:false
rpc-listen-all=true
# 事件轮询方式, 取值:[epoll, kqueue, port, poll, select], 不同系统默认值不同
#event-poll=kqueue
# 设置的RPC访问用户名, 此选项新版已废弃, 建议改用 --rpc-secret 选项
#rpc-user=
# 设置的RPC访问密码, 此选项新版已废弃, 建议改用 --rpc-secret 选项
#rpc-passwd=
## BT/PT下载相关 ##
# 当下载的是一个种子(以.torrent结尾)时, 自动开始BT任务, 默认:true
follow-torrent=true
# BT监听端口, 当端口被屏蔽时使用, 默认:6881-6999
listen-port=51413
# 单个种子最大连接数, 默认:55
#bt-max-peers=55
# 打开DHT功能, PT需要禁用, 默认:true
enable-dht=true
# 打开IPv6 DHT功能, PT需要禁用, 默认:true
enable-dht6=true
# DHT网络监听端口, 默认:6881-6999
dht-listen-port=6881-6999
# 本地节点查找, PT需要禁用, 默认:false
bt-enable-lpd=true
# 种子交换, PT需要禁用, 默认:true
enable-peer-exchange=true
# 每个种子限速, 对少种的PT很有用, 默认:50K
#bt-request-peer-speed-limit=50K
# 客户端伪装, PT需要
peer-id-prefix=-TR2770-
user-agent=Transmission/2.77
# 当种子的分享率达到这个数时, 自动停止做种, 0为一直做种, 默认:1.0
#seed-ratio=0.01
# BT校验相关, 默认:true
#bt-hash-check-seed=true
# 继续之前的BT任务时, 无需再次校验, 默认:false
bt-seed-unverified=true
# 保存磁力链接元数据为种子文件(.torrent文件), 默认:false
bt-save-metadata=true
# 强制加密, 防迅雷必备
bt-require-crypto=true
#bt-tracker 下载不能输在起跑线上
bt-tracker=udp://tracker.coppersurfer.tk:6969/announce,udp://tracker.open-internet.nl:6969/announce,udp://exodus.desync.com:6969/announce,udp://tracker.internetwarriors.net:1337/announce,udp://tracker.opentrackr.org:1337/announce,udp://9.rarbg.to:2710/announce,udp://public.popcorn-tracker.org:6969/announce,udp://tracker.vanitycore.co:6969/announce,udp://tracker.mg64.net:6969/announce,udp://mgtracker.org:6969/announce,udp://tracker.tiny-vps.com:6969/announce,udp://bt.xxx-tracker.com:2710/announce,udp://thetracker.org:80/announce,udp://open.demonii.si:1337/announce,udp://tracker.torrent.eu.org:451/announce,udp://tracker.qt.is:6969/announce,udp://tracker.port443.xyz:6969/announce,udp://tracker.ds.is:6969/announce,udp://tracker.cypherpunks.ru:6969/announce,udp://tracker-2.msm8916.com:6969/announce,udp://retracker.lanta-net.ru:2710/announce,udp://open.stealth.si:80/announce,udp://tracker1.itzmx.com:8080/announce,udp://tracker.uw0.xyz:6969/announce,udp://tracker.sandrotracker.biz:6969/announce,udp://tracker.iamhansen.xyz:2000/announce,udp://torr.ws:2710/announce,http://t.nyaatracker.com:80/announce,http://retracker.telecom.by:80/announce,http://open.acgnxtracker.com:80/announce,udp://zephir.monocul.us:6969/announce,udp://tracker4.itzmx.com:2710/announce,udp://tracker.kamigami.org:2710/announce,udp://tracker.cyberia.is:6969/announce,https://evening-badlands-6215.herokuapp.com:443/announce,http://tracker.city9x.com:2710/announce,http://retracker.mgts.by:80/announce,http://open.acgtracker.com:1096/announce,http://nbz.f3322.net:36006/announce,http://0d.kebhana.mx:443/announce,wss://tracker.openwebtorrent.com:443/announce,wss://tracker.iamhansen.xyz:443/announce,wss://tracker.fastcast.nz:443/announce,wss://tracker.btorrent.xyz:443/announce,ws://tracker.btsync.cf:2710/announce,udp://z.crazyhd.com:2710/announce,udp://wambo.club:1337/announce,udp://trackerxyz.tk:1337/announce,udp://tracker1.wasabii.com.tw:6969/announce,udp://tracker.xku.tv:6969/announce,udp://tracker.tvunderground.org.ru:3218/announce,udp://tracker.swateam.org.uk:2710/announce,udp://tracker.skyts.net:6969/announce,udp://tracker.piratepublic.com:1337/announce,udp://tracker.justseed.it:1337/announce,udp://tracker.halfchub.club:6969/announce,udp://tracker.files.fm:6969/announce,udp://tracker.dutchtracking.com:6969/announce,udp://tracker.dler.org:6969/announce,udp://tracker.desu.sh:6969/announce,udp://tracker.bluefrog.pw:2710/announce,udp://t.agx.co:61655/announce,udp://sd-95.allfon.net:2710/announce,udp://santost12.xyz:6969/announce,udp://retracker.nts.su:2710/announce,udp://retracker.coltel.ru:2710/announce,udp://pubt.in:2710/announce,udp://peerfect.org:6969/announce,udp://packages.crunchbangplusplus.org:6969/announce,udp://p4p.arenabg.com:1337/announce,udp://oscar.reyesleon.xyz:6969/announce,udp://open.facedatabg.net:6969/announce,udp://ipv4.tracker.harry.lu:80/announce,udp://inferno.demonoid.pw:3418/announce,udp://explodie.org:6969/announce,https://tracker.torrentsnows.com:443/announce,http://tracker1.itzmx.com:8080/announce,http://tracker.vanitycore.co:6969/announce,http://tracker.torrentyorg.pl:80/announce,http://tracker.tfile.me:80/announce,http://tracker.mg64.net:6881/announce,http://tracker.internetwarriors.net:1337/announce,http://tracker.electro-torrent.pl:80/announce,http://therightsize.net:1337/announce,http://share.camoe.cn:8080/announce,http://retracker.spb.ru:80/announce,http://omg.wtftrackr.pw:1337/announce,http://mgtracker.org:6969/announce,http://agusiq-torrents.pl:6969/announce
## 磁盘相关 ##
#另一种Linux文件缓存方式, 使用前确保您使用的内核支持此选项, 需要1.15及以上版本(?)
enable-mmap=true
# 文件预分配方式, 能有效降低磁盘碎片, 默认:prealloc
# 预分配所需时间: 快none < trunc < falloc < prealloc慢
#file-allocation=trunc
# 启用磁盘缓存, 0为禁用缓存, 需1.16以上版本, 默认:16M
disk-cache=64M
```

### 启动 aria2
```bash
aria2c --conf-path=/root/Aria2/aria2.conf -D
```

### 下载图形界面文件
- [AriaNg](https://objects.githubusercontent.com/github-production-release-asset-2e65be/58753834/a02f200e-6c8f-4549-96e1-a469b6abf533?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=releaseassetproduction%2F20240515%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20240515T081242Z&X-Amz-Expires=300&X-Amz-Signature=a02bdae645189a709fc70a14077c5b64e5ac6a24c7af33acedf5a5c09ce98451&X-Amz-SignedHeaders=host&actor_id=7278892&key_id=0&repo_id=58753834&response-content-disposition=attachment%3B%20filename%3DAriaNg-1.3.7-AllInOne.zip&response-content-type=application%2Foctet-stream)
- 解压出来, 把 `index.html` 放到服务器, 随便找个服务启动即可, 让网页可以访问到这个 `index.html`
- 访问 `index.html` 那个页面
  ![](https://api.onedrive.com/v1.0/shares/s!AmRYeUQXQNkEqhCpTAjOSvfaulmu/root/content)
- 收工
  ![](https://api.onedrive.com/v1.0/shares/s!AmRYeUQXQNkEqhFbY6qHztgipZgH/root/content)
- 这里把下载链接放进去就行了

### 补充说明
- 云服务器下载虽然速度很快, 但是如果服务器的带宽很慢的话, 下到服务器, 再从服务器下载到本地, 还是很慢的