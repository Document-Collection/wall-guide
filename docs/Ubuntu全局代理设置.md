
# Ubuntu全局代理设置

配置[SwitchyOmega代理设置](./SwitchyOmega代理设置.md)仅仅能够实现浏览器代理，还需要设置全局代理才能在命令行访问国外资源

## 生成`pac`文件

参考[Ubuntu代理配置](./Ubuntu代理配置.md)安装`genpac`，参考[ubuntu使用shadowsocks设置全局代理](./Ubuntu代理配置.md)生成配置文件`autoproxy.pac`

```
$ genpac --proxy="SOCKS5 127.0.0.1:1080" --gfwlist-proxy="SOCKS5 127.0.0.1:1080" -o autoproxy.pac --gfwlist-url="https://raw.githubusercontent.com/gfwlist/gfwlist/master/gfwlist.txt"
```

## 系统配置

打开系统设置`->Network->Network proxy`，选择`Method`为`Automatic`，在`Configuration URL`中填入生成的文件路径

```
file://文件路径
# 我的
file:///home/zj/software/vpn/autoproxy.pac
```

点击`Apply system wide`即可生效

## 代理工具设置

代理操作使用`SOCKS5`协议，大多命令行操作使用`HTTP/HTTPS`协议，所以需要使用代理工具进行转换

参考[Ubuntu代理配置](./Ubuntu代理配置.md)安装`ProxyChains`

测试命令

```
$ proxychains curl www.google.com
# 或
$ proxychains wget www.google.com
```