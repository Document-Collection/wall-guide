
# ssr配置

最近这几天经常出现网络断线的问题，重新找了`ssr`(酸酸乳)的服务端设置方法

## ip查找

参考：[怎样检查搬瓦工IP被墙](https://www.banwago.com/1265.html)

使用网址[Ping检测](http://ping.chinaz.com/45.32.46.78)查看外网服务器是否可以连接

使用网址[全方位查询您的IP地址](http://www.ip111.cn)查看自己的`ip`信息

## SSR服务端

文章[正确的翻墙姿势-SS&SSR](http://www.syshy.net/20180519/ssr/)比较详细的讲述了`SS/SSR`的发展历程，并给出了一些配置的建议

文章[记录酸酸乳（SSR）服务器搭建历程，我只是想查个资料](https://www.lurbk.com/lur1084.html)比较详细的讲解了利用`vultr`进行`ssr`服务端搭建的过程，其仓库地址已失效，使用如下地址：

```
# 原来的这个库被作者清空了
git clone https://github.com/Flyzy2005/ss-fly
# 在github上找了一个，自己也备份了一下
git clone https://github.com/zjZSTU/ss-fly.git
```

当前操作

1. 执行`ssr`

```
$ ss-fly/ss-fly.sh -ssr
```

2. 输入密码

```
Please enter password for ShadowsocksR:
(Default password: teddysun.com):
```

3. 输入端口号（默认）

```
Please enter a port for ShadowsocksR [1-65535]
(Default port: 10644):
```

4. 选择流密码（默认）

```
Which cipher you'd select(Default: aes-256-cfb):
```

5. 选择协议：`auth_chain_a`

```
Which protocol you'd select(Default: origin):7
```

6. 选择混淆（默认）

```
Which obfs you'd select(Default: plain):
```

完成服务端配置：

```
Congratulations, ShadowsocksR server install completed!
Your Server IP        :  xx.xx.xx.xx 
Your Server Port      :  xxxxx
Your Password         :  xxxxxx 
Your Protocol         :  auth_chain_a 
Your obfs             :  plain 
Your Encryption Method:  aes-256-cfb 

Welcome to visit:https://shadowsocks.be/9.html
Enjoy it!
```

**注意：配置完成后如果失效，尝试删除已有的进程，再重新配置一遍**

```
$ ps -aux | grep shadowsock
```

## SSR客户端

之前使用`SS`搭梯子的时候使用的是`Shadowsocks-Qt5`，里面没有加密协议的选项，所以参考[在 Ubuntu 上使用 SSR 梯子](https://alanlee.fun/2018/05/18/ubuntu-ssr/)安装[electron-ssr](https://github.com/qingshuisiyuan/electron-ssr-backup/blob/master/Ubuntu.md)

参考：[Debian系列——Ubuntu18.04为例](https://github.com/qingshuisiyuan/electron-ssr-backup/blob/master/Ubuntu.md)

安装`electron-ssr`完成后打开，输入服务器端配置，设置为`PAC`代理即可

关于浏览器配置和系统设置，参考：

[SwitchyOmega代理设置](https://wall-guide.readthedocs.io/zh/latest/SwitchyOmega%E4%BB%A3%E7%90%86%E8%AE%BE%E7%BD%AE.html)

[Ubuntu全局代理设置](https://wall-guide.readthedocs.io/zh/latest/Ubuntu%E5%85%A8%E5%B1%80%E4%BB%A3%E7%90%86%E8%AE%BE%E7%BD%AE.html)