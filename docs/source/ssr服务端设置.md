
# ssr服务端设置

最近这几天经常出现网络断线的问题，重新找了`ssr`(酸酸乳)的服务端设置方法

## ip查找

参考：[怎样检查搬瓦工IP被墙](https://www.banwago.com/1265.html)

使用网址[Ping检测](http://ping.chinaz.com/45.32.46.78)查看外网服务器是否可以连接

使用网址[全方位查询您的IP地址](http://www.ip111.cn)查看自己的`ip`信息

## SSR服务端

文章[正确的翻墙姿势-SS&SSR](http://www.syshy.net/20180519/ssr/)比较详细的讲述了SS/SSR的发展历程，并给出了一些配置的建议

文章[记录酸酸乳（SSR）服务器搭建历程，我只是想查个资料](https://www.lurbk.com/lur1084.html)比较详细的讲解了利用`vultr`进行`ssr`服务端搭建的过程，其仓库地址已失效，使用如下地址：

```
# 原来的这个库被作者清空了
git clone https://github.com/Flyzy2005/ss-fly
# 在github上找了一个，自己也备份了一下
git clone https://github.com/zjZSTU/ss-fly.git
```

## SSR客户端

之前使用`SS`搭梯子的时候使用的是`Shadowsocks-Qt5`，里面没有加密协议的选项，所以参考[在 Ubuntu 上使用 SSR 梯子](https://alanlee.fun/2018/05/18/ubuntu-ssr/)安装[electron-ssr](https://github.com/doctor-frankenstein/electron-ssr)

## 当前实现

当前没有使用加密协议，也能够实现连接，所以没有过多设置，还在继续使用`Shadowsocks-Qt5`。到时候真的需要连接之后再详细记录