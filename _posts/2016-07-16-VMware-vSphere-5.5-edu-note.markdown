---
layout: post
title:  "VMware vSphere 5.5培训笔记"
date:   2016-07-16 13:52:59 +0800
categories: Virtualization
---
# 第一章 课程简介
## 1、课程要求

上课时间80%

教材涵盖内容不全，需要看相关文档（白皮书）

## 2、什么是Vsphere

Vsphere是基础架构管理套件

### 管理

管理计算、存储、网络

Vsphere client 直接操作

Vsphere web client 

### vmotion

在线迁移

内存迁移、存储迁移、虚机迁移

无共享存储迁移    迁移主机和存储

## 3、VCP认证
### VCAP 高级认证   
	-dcpa管理方向

	-DCD 设计方向，架构方向

### Vcdx

国内不考
国外论文、答辩

# 第二章 虚拟化
## 1、虚拟化简介
在物理的平台上安装虚拟化平台软件vsphere，在虚拟化平台之上创建虚拟机。
#### 为什么使用虚拟机
资源利用率低

管理不灵活

成本高

### 资源池化
把资源做成一个资源池

虚拟机在管理员角度是一个文件夹

虚拟机，仅仅为逻辑上的计算机。

### CPU虚拟化
调度原理

物理快空闲占用

虚拟CPU没有时间，必须通过占用物理cpu时间获得cpu时间。

物理空闲，虚拟过来调用

cpu就绪时间

40ms  大于40ms就有问题

一个cpu创建3-5个虚拟cpu比较合理

### 内存虚拟化
按需分配

资源充分利用

给你了，你不用我拿过来用

### 网络虚拟化
### 存储虚拟化
Datastore 容器  逻辑单元，把物理设备加进来，自动创建逻辑文件
## 2、ESXI概述
### 虚拟主机
ESXi 作为 NTP 客户端
同步时间准确性
## 3、Vsphere client
Vsphere client5.1开始功能不升级

建议使用web client

### 备注
管理主机不用Root

Vpxuger管理主机，是主机和vcenter协商出来的密钥。

# 实验1  安装vSphere Client 和 vSphere Web Client 
## 实验环境
第一步，
https://182.48.114.3/
组别：20B

Vmware55
abcd1234
# 实验2  配置ESXI主机

# 第三章 创建虚拟机
## 1、虚机概念
 
虚拟机，从内部看，是一对硬件；从EXSi主机看，是一组文件集。

### 模板文件

模板文件不能开机

### 磁盘文件
磁盘描述文件、磁盘数据文件是成对出现

### Vmdk 快照
快照原理

描述、数据为只读，增量使用

两块盘加在一起是当前数据

快照不能备份，每个快照为一个增量

目的为回滚到目前状态

快照坏了，依赖它的不能使用。

### 虚机
虚机可以挂起，相当于虚机关机。

和关机的区别：内存状态保存在vmss

### 交换文件
操作系统交换文件为虚机自己管理，虚机开机时创建

缺省为内存大小

## 2、创建虚机
#### 三种方法
使用向导

克隆

模板部署

### 虚机配置
精简

密集

当主机内存需要时候，虚机内存释放给主机

# 实验3 创建虚机
•	Provisioned Storage ___2.58GB___ 
•	Not Shared Storage __1.85KB____ 
•	Used Storage ____1.85KB__
配置过后：
"•	Provisioned Storage ___2.48GB___ 
•	Not Shared Storage __1.04GB____ 
•	Used Storage ____1.04GB __
# 第四章 VMware vCenter Server
## 1、vCenter Server体系机构
### 管理平台
管理主机、虚机、设置功能

每个vcenter server实例可以管理一个1kESXi主机，1w台虚机。

内置Linux数据库  vhost

内置windows平台数据库    sql server2008 r2

## 2、部署 vCenter Server 虚拟设备
导入设备

导入VOF模板

封装系统、组件。

# 试验4 

## 3、管理 vCenter Server 清单
### 使用文件夹组织清单对象

# 补充 Vsphere 6
Vsphere6把vcentre分成两大块

vsphere5是服务

# 实验5  vCenter Server 清单操作
注意事项

做实验时，这章ha  dns  注意：两人一起做还是

Pin、unpin实现展开于收缩

# 第五章 配置和管理虚拟网络
## vNetwork 标准交换机

虚机设置端口组，譬如DMZ、TestDev

需要配置连接虚机、主机、物理网卡的端口

企业增强版就有分布式交换机

# 实验6

# 实验7
VLAN设置

物理的VLAN的设置1-4096

虚拟化的VLAN的设置0-4095

## 三种设置策略，两种在内部，一种在外部

	虚拟交换机打vlan标签

虚拟机端口组设置vlan，范围是1-4094

虚拟机打标签105vlan

	从虚机出来的包本身带vlanID，操作系统设置

Windows系统设置vlan标签

虚拟交换机的端口设置为4095

	在物理交换机上设置标签

端口组缺省为0

环境：全是生产机

配置标准虚拟交换机策略

## 安全

	promisculus混杂模式

端口组启动混杂模式，进行抓包

	Mac策略更改模式

缺省可进可出

	Forged 传输

从外面来的，进

从虚机到物理网卡，出

流量调整策略
逻辑的调整，物理没法调整
标准交换机只能控制出栈方面的流量
负载平衡方法
	缺省策略
源端口 ID
	源 MAC hash
	Ip哈希
一个虚拟网卡可以对应多个物理网卡，需要做聚合
网络故障检测

实验注意事项
选择网卡1、3，不能选择2、3

两学员必须起名相同:Production.
# 实验8

# 实验9

# 第六章 配置和管理虚拟存储
## 存储协议概述

支持裸设备 映射

把卷映射给虚机

同一个主机不存在vmotion

## 数据存储
整个文件系统最大为64G

创建文件最大可以达到62G

小文件8k来存储

## 配置软件 iSCSI
配置 VMkernel 端口以访问 IP 存储

# 实验9
注意事项

最后一步，端口绑定不要做！

成功可以看到5个lan

尚未完成

FCoE 适配器 

# 实验10

VMware vSphere VMFS 数据存储

一个学员用2个

3、4

# 实验11
Capacity   8.5GB

配置后：

Capacity   19.5GB

# 第七章  虚拟机管理
创建和克隆模板

虚机克隆模板

虚机转成模板

模板克隆模板

新的虚机生成

向导

导入

模板生成

虚机克隆

修改虚机


注意事项

千万不要点击  OK，再最下端进行修改属性

Lan第一个人做完，把他删掉；第二个人做完，把它删掉。

修改VMDK

模式的转换

迁移可以修改部署方式

精简变成全分配
Inflat
虚拟机选项
文件夹位置更改
做vmotion时候可以修改

迁移虚机
冷迁
挂起   实质关机
Vmotion    在线
Stoage  vmotion
Enhanced vMotion               主机存储一起迁
Vmotion迁移工作原理
vmotion网络进行迁移
vkernel port进行地址配置
在线迁内存

存储和主机通过网络路径迁移，不适用
# 实验12

# 实验13
C:1.99G
变化后
C:2.98G
 
# 实验14
迁移6次
创建虚拟机快照
能使用快照做备份
操作不敢保证严重后果，所以caozuo 之前做快照

磁盘状态变为只读

上端删除下端，删除
下端删除上端，合并
创建 vApp
资源池
实现资源的控制
定义开关机顺序、时间
## 实验15
Local-exi02

# 实验16

# 第八章 数据保护

第九章 访问和身份验证控制
配置 ESXi 主机访问权限和身份验证
DCUI界面设置锁定模式
配置角色和权限
什么用户
什么组
具备什么角色进行操作
角色
特殊能力的打包
对象
同级相加、子集覆盖
# 实验17
# 实验18

# 第十章 资源管理和监视
虚拟 CPU 和内存概念
虚拟 SMP
对称多CPU
非一致性内存访问
CPU负载均衡
占用物理CPU方可使用
同时被占用

一个物理CPU   3-5虚拟cpu是合理的
内存
按需分配
分配按照page分配
资源控制
份额、限制和预留
三个参数
Eg：内存2G，当资源出现紧张，预留值500M，当启动时候，还是按照按需分配，资源紧张开始收紧内存，收到500M就停止。
份额：比例，权重。
资源池

# 实验18
 
 
监视资源使用情况
性能调整方法
原则一：CPU、存储数据一套数据，前后做比较
现象：网络慢
原则二：综合分析，虚拟机和主机都需要分析
虚拟化环境
Eg：虚拟机是否受 CPU 限制？
首先，看虚拟机性能图表
接着，看着主机性能图表
# 实验19

## 第5课 使用警报

# 实验20

# 实验21

# 第十一章 高可用性和容错
VMware 为每个级别提供保护 
组件高可用
网卡绑定
存储多路径
服务器
在线迁移
异常保护FT
HA保护
存储

数据
Vmdk复制到远程
站点
SRAM
vCenter Server 高可用
可以冷备
可以服务级别的高可用
应用程序的HA
高可用
99.999%
高可用的能力
监控主机，保护虚机
监控虚机，保护虚机
监控应用，保护应用
故障情况 – 主机
只有开启的虚机是受保护的
通过心跳监控
故障情况 – 客户操作系统
当虚拟机停止发 送心跳信号或虚 拟机进程崩溃时 (vmx)，vSphere HA 会重置虚拟机
故障情况 – 应用程序
重启虚机
需要安装 VMware Tools   
高可用体系结构
原理
主机的mosid号作为master，随机分配的
Master通过FDM告诉其他主机，利用心跳进行监控
Center怎么知道有多少虚机
通过maser写在所有共享存储上

网络心跳信号

Master需要两根心跳

出现故障的从属主机

虚机迁走

出现故障的主控主机

迁走并且重新选择master

隔离主机

看网络规划怎么设置

网络分区

脑裂

出现两个集群

一个班级分裂，那么配置一个临时班长

配置高可用

HA为集群的一个服务

接入控制

在三个虚机情况下，当启动第三个虚机时候，接入控制判断能不能启动，有木有资源支持启动

预留足够资源，满足此虚机出现问题，被其他虚机接管。

Eg：3个主机，3*4内存

动态算:所有开启虚机的CPU、内存的预留值的最大值来计算。

# 实验21
 
 

# 实验22

VSphere FT

虚机、内存两份，存储一份

主虚机接收IO请求，备虚机备份内存

# 实验23
 
Secondary Location
 
Joe01-2

vSphere Replication

保护开启虚机的VMDK

Vdp保护虚机

标准的OF模板

SVR的一个功能，独立出来的

# 第十二章可扩展性 
HA

VC

DRS

不是时时刻刻起作用的

手动运行drs

EVC

提高虚拟机性能的方法

# 实验24


考试靠一半

题库
# 第十三章 补丁程序管理

# 第十四章  安装 VMware 组件

认证、授权以及评估

账号

账号：邮箱

证书

电子证书

无纸质

https://mylearn.vmware.com

点击登陆帮助

VCP5-TCV   DIANJI

四个账号