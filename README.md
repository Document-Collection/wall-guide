# 穿墙指南

[![Documentation Status](https://readthedocs.org/projects/wall-guide/badge/?version=latest)](https://wall-guide.readthedocs.io/zh/latest/?badge=latest) [![standard-readme compliant](https://img.shields.io/badge/standard--readme-OK-green.svg?style=flat-square)](https://github.com/RichardLitt/standard-readme) [![Conventional Commits](https://img.shields.io/badge/Conventional%20Commits-1.0.0-yellow.svg)](https://conventionalcommits.org) [![Commitizen friendly](https://img.shields.io/badge/commitizen-friendly-brightgreen.svg)](http://commitizen.github.io/cz-cli/)

> 科学上网相关

完整的境外服务器搭建，本地客户端/浏览器设置教程，实现科学上网

* `VPS`介绍 - [什么是VPS](https://wall-guide.readthedocs.io/zh/latest/什么是VPS.html)
* `ip/`端口查询 - [如何判断ip或端口被封](https://wall-guide.readthedocs.io/zh/latest/如何判断ip或端口被封.html)
* `VULTR`使用 - [VPS服务器部署](https://wall-guide.readthedocs.io/zh/latest/手动翻墙.html)
* 本地设置
    * 全局代理设置 - [Ubuntu全局代理设置](https://wall-guide.readthedocs.io/zh/latest/Ubuntu全局代理设置.html)
    * 浏览器插件设置 - [SwitchyOmega代理设置](https://wall-guide.readthedocs.io/zh/latest/SwitchyOmega代理设置.html)
* 自建服务器
    * `SSR` - [ssr配置](https://wall-guide.readthedocs.io/zh/latest/ssr配置.html)
    * `BOOK` - [[brook]服务端+客户端设置](https://wall-guide.readthedocs.io/zh/latest/[brook]服务端+客户端设置.html)
    * `v2ray` - [v2ray使用](https://wall-guide.readthedocs.io/zh/latest/v2ray使用.html)
* 购买梯子 - [[Google Helper]辅助搜索工具](https://wall-guide.readthedocs.io/zh/latest/[Google%20Helper]辅助搜索工具.html)
* 移动客户端
    * v2ray - [[Android]V2ray使用](https://wall-guide.readthedocs.io/zh/latest/[Android]V2ray使用.html)

## 内容列表

- [背景](#背景)
- [安装](#安装)
- [用法](#用法)
- [主要维护人员](#主要维护人员)
- [参与贡献方式](#参与贡献方式)
- [许可证](#许可证)

## 背景

基于各种原因需要登录外网，之前使用过免费/付费VPN网站，经常断网不能使用，所以萌发了自己搭建境外服务器的念头

# 安装

需要预先安装以下工具：

```
$ pip install -U Sphinx
$ sudo apt-get install make
```

## 用法

有两种使用方式

1. 在线浏览文档：[穿墙指南](https://wall-guide.readthedocs.io/zh/latest/?badge=latest)

2. 本地生成文档，实现如下：

    ```
    $ git clone https://github.com/zjZSTU/wall-guide.git
    $ cd wall-guide/docs
    $ make html
    ```
    编译完成后进入`docs/build/html`目录，打开`index.html`文件

## 主要维护人员

* zhujian - *Initial work* - [zjZSTU](https://github.com/zjZSTU)

## 参与贡献方式

欢迎任何人的参与！打开[issue](https://github.com/zjZSTU/wall-guide/issues)或提交合并请求。

注意:

* `GIT`提交，请遵守[Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0-beta.4/)规范
* 语义版本化，请遵守[Semantic Versioning 2.0.0](https://semver.org)规范
* `README`编写，请遵守[standard-readme](https://github.com/RichardLitt/standard-readme)规范

## 许可证

[Apache License 2.0](LICENSE) © 2019 zjZSTU
