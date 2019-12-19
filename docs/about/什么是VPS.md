
# 什么是VPS

参考：[VPS](https://baike.baidu.com/item/VPS#)

`VPS，Virtual Private Server`，虚拟专用服务器，其是将物理服务器通过虚拟化技术虚拟成为多个虚拟专用服务器

## `VPS`的优点

同一服务器上的多个`VPS`共享硬件、软件许可证以及管理资源，以最大化效率运行

对于用户而言，每个`VPS`平台的管理和运行与独立主机完全相同，有独立的公网`IP`地址、操作系统、磁盘空间、内存、`CPU`资源、进程和系统配置，可以单独安装程序并且单独重启主机

## `VPS`的缺陷

同一台服务器上的某个`VPS`受到攻击或占用过多宽带资源时，其余的`VPS`也会受到影响，所以一台`VPS`被黑客入侵可能造成服务器瘫痪

同时硬件服务器的损坏也会影响到所有`VPS`主机

## `VPS`的实现

实现`VPS`的方式有两种，一种是虚拟化技术，比如`XEN, KVM, OpenVZ`，另一种是容器技术，比如`Docker`

## `VPS vs ECS`

参考：

[云服务器](https://baike.baidu.com/item/%E4%BA%91%E6%9C%8D%E5%8A%A1%E5%99%A8)

[云服务器（ECS）云主机 云虚拟主机 VPS等产品的区别？](https://www.zhihu.com/question/46387307)

[阿里云服务器与VPS和虚拟主机有什么区别？](https://yq.aliyun.com/articles/226730)

`ECS(Elastic Computer Service)`指的是云服务器，其实现是通过服务器集群来虚拟出独立服务器，对服务器的资源扩展有更高的可操作性；同时通过冗余的共享存储和智能备份，单个服务器的故障不影响云服务器的使用，大大提高了安全性和稳定性

## 什么是使用`VPS`以及`ECS`

`VPS`的价格一般比`ECS`低，所以针对小规模并发访问，资源扩展性不大的操作可以使用`VPS`

`VPS`厂商包括：[vultr](https://www.vultr.com/)、[linode](https://www.linode.com)、[BandwagonHOST](https://bwh8.net/)和[google cloud](https://cloud.google.com/)

如果后期可能需要弹性增加资源，同时对安全性和稳定性有更高要求的可以使用`ECS`

`ECS`厂商包括：[阿里云](https://cn.aliyun.com/)、[腾讯云](https://cloud.tencent.com/)、[亚马逊云](https://amazonaws-china.com/cn/?nc2=h_lg)