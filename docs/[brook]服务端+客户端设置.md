
# [brook]服务端+客户端设置

最近用`ssr`搭建的梯子经常会被封掉，打算换一种代理工具 - [brook](https://github.com/txthinking/brook/wiki)

## 介绍

`brook`是一个跨平台的代理/`VPN`软件，支持`Windows/Linux/Android/IOS`环境

其主要是通过命令行进行客户端和服务器的配置，网上说用的人还不多

## 下载

下载[Linux brook](https://github.com/txthinking/brook/releases/download/v20190601/brook)

```
$ wget https://github.com/txthinking/brook/releases/download/v20190601/brook
```

赋值可执行权限：

```
$ chmod +x brook
```

其他版本参考[Download](https://github.com/txthinking/brook#download)

## 服务器设置

启动服务器：

```
# ./brook server -l :port -p passwd
```

自定义端口号`port`和密码`passwd`

## 客户端设置

```
$ ./brook client -l 127.0.0.1:1080 -i 127.0.0.1 -s server_ip:port -p passwd
```

`1080`是`sock5`协议默认端口号，依次修改服务器`IP`（`server_ip`）、端口号（`port`）和密码（`passwd`）

*在浏览器和全局设置参考之前文章即可*

## 优化

可以将命令行设置为后台运行或启动服务运行

### 后台运行

参考：

[ubuntu 后台运行的几种方法！](https://blog.csdn.net/qq_29663071/article/details/80528829)

[Shell 传递参数](https://www.runoob.com/linux/linux-shell-passing-arguments.html)

格式如下：

```
$ nohup 命令 &
```

可以新建服务端脚本`brook-server.sh`:

```
#!/bin/bash
nohup ./brook server -l :$1 -p $2 &
```

执行脚本命令：

```
$ sh brook-server.sh port passwd
```

**依次输入端口号和密码即可**

同样可以新建客户端脚本`brook-client.sh`:

```
#!/bin/bash
nphup ./brook client -l 127.0.0.1:1080 -i 127.0.0.1 -s server-ip:port -p passwd &
```

执行脚本命令：

```
$ sh brook-client.sh server-ip port passwd
```

**依次输入服务器ip，端口号和密码即可**

### 启动服务运行

参考：[Brook---一款优秀的小众代理软件(酸酸乳和酸酸的完美替代品)](https://www.linuxstudy.cn/archives/35.html)

通过启动服务来运行服务端`brook`。新建文件`brook.service`

```
[Unit]
Description=brook service
After=network.target syslog.target
Wants=network.target

[Service]
Type=simple
ExecStart=/path/to/brook server -l :port -p passwd # 使用绝对路径

[Install]
WantedBy=multi-user.target
```

设置root权限：

```
$ sudo chmod 777 brook.service
```

放置在`/etc/systemd/system`文件夹内，使用工具`systemctl`启动服务

```
systemctl start brook                  # 启动brook
systemctl stop brook                   # 停止brook
systemctl status brook                 # 查看brook服务状态
systemctl restart brook                # 重启brook服务
systemctl enable brook                 # 将brook加入开机启动项
```

## 相关

除了`brook`外，还找到一个代理工具[V2Ray](https://v2ray.com/)

`youtube`上有关翻墙软件的测评：[哪种翻墙软件更隐蔽？！联通后台数据实测SS/SSR/V2Ray/Brook 翻墙APP！请耐心看完本教程，能让你避免被请喝茶！](https://www.youtube.com/watch?v=G-P8eyltc5E)