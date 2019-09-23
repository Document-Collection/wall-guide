
# v2ray使用

参考： 

[如果使用SS或SSR频繁被墙IP墙端口那么你需要使用v2ray科学上网](https://glorystar.me/archives/v2ray-1.html)

[V2Ray搭建详细图文教程](https://github.com/233boy/v2ray/wiki/V2Ray搭建详细图文教程)

今天翻墙又双叒叕不行了，这次打算使用[v2ray](https://www.v2ray.com)，不过其官网一直打不开，所以主要参考[233boy/v2ray](https://github.com/233boy/v2ray/tree/master)

## 什么是v2ray

`v2ray`是一个代理软件，相比于`shadowsocks`，它实现了更多的代理协议和功能（包括`shadowsocks`）

## 安装

有`2`种方式：

1. 官方脚本
2. 第三方脚本（推荐）

### 官方脚本

`v2ray`提供了一个安装脚本

```
$ bash <(curl -L -s https://install.direct/go.sh)
```

*其仅实现了安装功能，其他操作（管理/卸载等）都很麻烦，不推荐使用*

### 第三方脚本

[233boy]()提供了一个一键安装和管理脚本，参考[V2Ray一键安装脚本](https://github.com/233boy/v2ray/wiki/V2Ray一键安装脚本)，里面不仅集成了安装/卸载功能，还具备配置选项

下载并执行脚本`v2ray.sh`，当前选择默认配置

```
$ bash <(curl -s -L https://git.io/v2ray.sh)
........... V2Ray 一键安装脚本 & 管理脚本 by 233v2.com ..........

帮助说明: https://233v2.com/post/1/

搭建教程: https://233v2.com/post/2/

 1. 安装

 2. 卸载

请选择 [1-2]:1

请选择 V2Ray 传输协议 [1-32]

  1. TCP
  2. TCP_HTTP
  3. WebSocket
  4. WebSocket + TLS
  5. HTTP/2
  6. mKCP
  7. mKCP_utp
  8. mKCP_srtp
  9. mKCP_wechat-video
 10. mKCP_dtls
 11. mKCP_wireguard
 12. QUIC
 13. QUIC_utp
 14. QUIC_srtp
 15. QUIC_wechat-video
 16. QUIC_dtls
 17. QUIC_wireguard
 18. TCP_dynamicPort
 19. TCP_HTTP_dynamicPort
 20. WebSocket_dynamicPort
 21. mKCP_dynamicPort
 22. mKCP_utp_dynamicPort
 23. mKCP_srtp_dynamicPort
 24. mKCP_wechat-video_dynamicPort
 25. mKCP_dtls_dynamicPort
 26. mKCP_wireguard_dynamicPort
 27. QUIC_dynamicPort
 28. QUIC_utp_dynamicPort
 29. QUIC_srtp_dynamicPort
 30. QUIC_wechat-video_dynamicPort
 31. QUIC_dtls_dynamicPort
 32. QUIC_wireguard_dynamicPort

备注1: 含有 [dynamicPort] 的即启用动态端口..
备注2: [utp | srtp | wechat-video | dtls | wireguard] 分别伪装成 [BT下载 | 视频通话 | 微信视频通话 | DTLS 1.2 数据包 | WireGuard 数据包]

(默认协议: TCP):

 V2Ray 传输协议 = TCP
----------------------------------------------------------------

请输入 V2Ray 端口 [1-65535]
(默认端口: 60663):

 V2Ray 端口 = 60663
----------------------------------------------------------------


是否开启广告拦截(会影响性能) [Y/N]
(默认 [N]):

 广告拦截 = 关闭
----------------------------------------------------------------

是否配置 Shadowsocks [Y/N]
(默认 [N]): 


 ....准备安装了咯..看看有毛有配置正确了...

---------- 安装信息 -------------

 V2Ray 传输协议 = TCP

 V2Ray 端口 = 60663

 是否配置 Shadowsocks = 未配置

---------- END -------------

按 Enter 回车键 继续....或按 Ctrl + C 取消.

 extracting: /tmp/v2ray/v2ctl.sig    
  inflating: /tmp/v2ray/v2ray        
 extracting: /tmp/v2ray/v2ray.sig    
  inflating: /tmp/v2ray/vpoint_socks_vmess.json  
  inflating: /tmp/v2ray/vpoint_vmess_freedom.json  

..由于你的 VPS 内核支持开启 BBR ...已经为你启用 BBR 优化....

---------- V2Ray 配置信息 -------------

 地址 (Address) = 207.xx.xx.22

 端口 (Port) = 6xx63

 用户ID (User ID / UUID) = 7ca73c1f-9f46-4bf7-9435-75b26724xxxa2

 额外ID (Alter Id) = 233

 传输协议 (Network) = tcp

 伪装类型 (header type) = none

---------- END -------------

V2Ray 客户端使用教程: https://233v2.com/post/4/

提示: 输入 v2ray url 可生成 vmess URL 链接 / 输入 v2ray qr 可生成二维码链接
```

完成之后如果想要重新配置，直接在命令行输入v2ray即可

```
# v2ray


........... V2Ray 管理脚本 v3.14 by 233v2.com ..........

## V2Ray 版本: v4.20.0  /  V2Ray 状态: 正在运行 ##

帮助说明: https://233v2.com/post/1/

反馈问题: https://github.com/233boy/v2ray/issues

TG 群组: https://t.me/blog233

捐赠脚本作者: https://233v2.com/donate/

捐助 V2Ray: https://www.v2ray.com/chapter_00/02_donate.html

  1. 查看 V2Ray 配置

  2. 修改 V2Ray 配置

  3. 下载 V2Ray 配置 / 生成配置信息链接 / 生成二维码链接

  4. 查看 Shadowsocks 配置 / 生成二维码链接

  5. 修改 Shadowsocks 配置

  6. 查看 MTProto 配置 / 修改 MTProto 配置

  7. 查看 Socks5 配置 / 修改 Socks5 配置

  8. 启动 / 停止 / 重启 / 查看日志

  9. 更新 V2Ray / 更新 V2Ray 管理脚本

 10. 卸载 V2Ray

 11. 其他

温馨提示...如果你不想执行选项...按 Ctrl + C 即可退出

请选择菜单 [1-11]:
```

## 配置文件

...
...

## SS

`v2ray`允许开启`Shadowsocks`功能，在命令行输入`v2ray`，选择`5. 修改 Shadowsocks 配置`即可

```
$ v2ray
...
...
请选择菜单 [1-11]:5


 大佬...你没有配置 Shadowsocks ...不过现在想要配置的话也是可以的 ^_^


是否配置 Shadowsocks [Y/N]
(默认 [N]): Y

请输入 Shadowsocks 端口 [1-65535]，不能和 V2ray 端口相同
(默认端口: 47133): 


 Shadowsocks 端口 = 47133
----------------------------------------------------------------

请输入 Shadowsocks 密码
(默认密码: 233blog.com): zhujian


 Shadowsocks 密码 = zhujian
----------------------------------------------------------------

请选择 Shadowsocks 加密协议 [1-7]

 1. aes-128-cfb

 2. aes-256-cfb

 3. chacha20

 4. chacha20-ietf

 5. aes-128-gcm

 6. aes-256-gcm

 7. chacha20-ietf-poly1305

(默认加密协议: chacha20-ietf-poly1305):2


 Shadowsocks 加密协议 = aes-256-cfb
----------------------------------------------------------------

按 Enter 回车键 继续....或按 Ctrl + C 取消.


---------- Shadowsocks 配置信息 -------------

 服务器地址 = 207.xx.xx.22

 服务器端口 = 4xx33

 密码 = zhujian

 加密协议 = aes-256-cfb

 SS 链接 = ss://YWVzLTI1Ni1jZxxxemh1amlhbkAyMDcuMTQ4LjQuMjI6NDcxMzM=#233v2.com_ss_207.148.4.22

 备注: Shadowsocks Win 4.0.6 客户端可能无法识别该 SS 链接

提示: 输入 v2ray ssqr 可生成 Shadowsocks 二维码链接
```

## 额外

[Just My Socks 详细图文购买教程](https://bwgjms.com/post/how-to-buy-justmysocks/)

[[科普] 为什么你用的VPN网速那么慢？](https://fangeqiang.com/1378.html)