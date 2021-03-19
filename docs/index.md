# 本仓库不再维护，更新的内容前往：[ZJDoc/WallGuide](https://github.com/ZJDoc/WallGuide)

# 引言

这几年随着学习的深入，常常需要搜索国外资源，慢慢的就开始搭建梯子，尝试寻找能够科学上网的方法

目前大致有`2`种模式

1. 购买网站套餐
2. 购买海外服务器自己搭建

## 购买网站套餐

最开始尝试过免费软件（比如[蓝灯](https://www.logcg.com/archives/1276.html)），后来使用付费套餐（`MonoCloud、borderSS`、影梭）

免费软件不稳定，付费套餐同样不稳定，刚开始尝试一两个月没有问题，等到付了`1`年的费用后，没几个月连网站都登不上了

尝试了几次后总觉得不靠谱，所以选择第二种方法

## 购买海外服务器自己搭建

购买海外`VPS`服务器，我使用的是[vultr](https://www.vultr.com/)，类似的还有[linode](https://www.linode.com)、[google cloud](https://cloud.google.com/)、[BandwagonHOST](https://bwh8.net/)

无意间发现[比特熊](https://bitbear.net/)，没有使用过，不过价格很便宜

参考：

[Vultr中文网](https://www.cnvultr.com/)

[搬瓦工VPS教程](https://www.bandwagonhost.net/readme)

## 实现

当前最新的实现流程：

1. 使用`Vultr`服务器
2. 浏览器插件使用`SwitchyOmega`
3. 客户端（`Ubuntu/Android`）/服务器使用`Trojan`
4. 使用`ProxyChains`命令行工具加速