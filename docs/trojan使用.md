
# trojan使用

在浏览`youtube`的时候发现一个视频：[Trojan灭了V2ray？Trojan翻墙速度超乎想象?Trojan V2ray速度对比](https://www.youtube.com/watch?v=zlOTrR1AzpA)。里面比较了`WebSocks+TLS`实现的`V2ray`与`Trojan`，而当前仅使用了基于`V2Mess`协议的`V2ray`，并没有进一步配置`WebSocks+TLS`（*太麻烦了*），发现`Trojan`配置相对简单，果断入手

参考：

[使用 trojan 翻越长城的进阶使用方法](https://www.bennythink.com/trojan.html)

[自建梯子教程 --Trojan版本](https://trojan-tutor.github.io/2019/04/10/p41.html)

## trojan简介

简单的说，`SS/SSR`等工具通过加密数据的方式来进行传输，而[trojan-gfw/trojan](https://github.com/trojan-gfw/trojan)使用的[TroJan协议](https://trojan-gfw.github.io/trojan/protocol)通过模拟正常的`HTTPs`连接的方式进行数据传输

## 完整流程

1. 域名/证书配置
2. 服务端配置（`Ubuntu 18.04`）
3. 客户端配置（`Ubuntu 18.04 + Android`）
4. `Service`实现
5. `Docker`实现

## 域名/证书配置

`trojan`需要配置域名和证书，可以申请免费的域名和证书

* 域名
    * [freenom](https://www.freenom.com/)
    * [dot.tk](http://www.dot.tk/zh/index.html)
* 证书
    * [Let's Encrypt](https://letsencrypt.org/zh-cn/getting-started/)

不过在国外的域名网站申请比较麻烦，我在阿里云上实现了域名申请、`TLS`证书申请和`DNS`解析（将域名和服务器`IP`绑定）

## 服务端配置

当前系统为`Ubuntu 18.04`，下载安装包 - [trojan-1.14.0-linux-amd64.tar.xz](https://github.com/trojan-gfw/trojan/releases)。解压后文件列表如下：

```
├── config.json
├── CONTRIBUTORS.md
├── examples
│   ├── client.json-example
│   ├── forward.json-example
│   ├── nat.json-example
│   ├── server.json-example
│   └── trojan.service-example
├── LICENSE
├── README.md
├── trojan
```

其中`trojan`是已编译好的程序，查看其使用方式

```
# ./trojan --help
Welcome to trojan 1.14.0
usage: ./trojan [-htv] [-l LOG] [-k KEYLOG] [[-c] CONFIG]
options:
  -c [ --config ] CONFIG (=config.json) specify config file
  -h [ --help ]                         print help message
  -k [ --keylog ] KEYLOG                specify keylog file location (OpenSSL 
                                        >= 1.1.1)
  -l [ --log ] LOG                      specify log file location
  -t [ --test ]                         test config file
  -v [ --version ]                      print version and build info
```

默认的`config.json`为服务端配置文件，修改其中的`password/cert/key`字段后，启动服务端

```
# ./trojan -c config.json 
Welcome to trojan 1.14.0
[2019-12-31 19:14:16] [WARN] trojan service (server) started at 0.0.0.0:443
```

##  客户端配置

客户端分两种：桌面端和移动端

### 桌面端配置

当前系统为`Ubuntu 18.04`，同样先下载程序，解压后使用`examples`目录下的`client.json-example`配置文件（修改文件后缀名）。需要修改以下字段：

1. `local_port`：通常设置为`1080`，如果之前已配置其他代理软件，可设置其他端口以避免冲突
2. `remote_addr`：域名
3. `password`：输入在服务端设置的一个密码

完成设置后启动程序

```
$ ./trojan -c client.json 
Welcome to trojan 1.14.0
[2019-12-31 19:19:46] [WARN] trojan service (client) started at 127.0.0.1:10801
```

### 移动端配置

下载`Android apk` - [trojan-gfw/igniter](https://github.com/trojan-gfw/igniter/releases)

安装完成后打开应用，输入域名和密码即可登录

## Service实现

参考：[Systemd 入门教程：实战篇](https://www.ruanyifeng.com/blog/2016/03/systemd-tutorial-part-two.html)

经过上述服务端和客户端的配置后，已经能够实现`VPN`连接。为了进一步持久化运行，创建`service`文件进行配置

在`/etc/systemd/system`下新建`trojan.service`：

```
[Unit]
Description=Trojan
Documentation=https://trojan-gfw.github.io/trojan/

[Service]
ExecStart=/opt/trojan/trojan -c /opt/trojan/client.json -l /opt/trojan/trojan.log
Type=simple
KillMode=process
Restart=no
RestartSec=42s

[Install]
WantedBy=multi-user.target
```

启动服务并设置开机自启动

```
$ systemctl start trojan
$ systemctl enable trojan
Created symlink /etc/systemd/system/multi-user.target.wants/trojan.service → /etc/systemd/system/trojan.service.
$ systemctl status trojan
● trojan.service - Trojan
   Loaded: loaded (/etc/systemd/system/trojan.service; enabled; vendor preset: enabled)
   Active: active (running) since Tue 2019-12-31 19:57:29 CST; 4min 36s ago
     Docs: https://trojan-gfw.github.io/trojan/
 Main PID: 9018 (trojan)
    Tasks: 2 (limit: 4915)
   CGroup: /system.slice/trojan.service
           └─9018 /opt/trojan/trojan -c /opt/trojan/client.json -l /opt/trojan/trojan.log

12月 31 19:57:29 zj-ThinkPad-T470p systemd[1]: Started Trojan.
12月 31 19:57:29 zj-ThinkPad-T470p trojan[9018]: Welcome to trojan 1.14.0
```

*如果之前已配置`service`文件，需要重新加载配置文件 - `systemctl daemon-reload`*