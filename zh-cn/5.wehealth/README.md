## 项目背景

> wehealth 是一家专注智慧妇幼健康管理、便携式智能医疗设备 销售与服务为一体的国家级高新技术企业。

具体的相关背景如下：

- 专注于医疗系统的妇幼健康管理，产科信息化，远程监护服务等场景；
- 服务范围包括产前，围产期，产后等几个阶段；
- 提供软件、硬件、服务等整体解决方案；



## 系统方案



### 系统蓝图

> 系统整体蓝图

<img src="http://img.susense.cn/lantu2.png" style="zoom:50%;" />

> 整体产品线包括：

- 门户Portal
- 用户端
  - luckyMom 用户app
  - luckyMom 医生端app
  - luckMom 微信小程序
  - luckMom 公众号
  - luckMom 移动H5 程序
- web 平台
  - 院外SaaS 远程监护平台
  - 产科信息化系统
  - 一体化区域服务管理平台
- 数据集成平台（对接院内各提供商软件系统）
- 终端一体机
- 第三方硬件集成系统（已合作的厂家）
  - 平安医疗
  - 金圣达
  - 水滴医疗
  - 双佳
  - 心脉
  - 安测
- **数据开放平台（区域数据上报、数据开放平台）**

!> 数据检测的设备



![](http://img.susense.cn/20201013173416.png)![](http://img.susense.cn/20201013173805.png)![](http://img.susense.cn/20201013173906.png)![](http://img.susense.cn/20201013173947.png)![](http://img.susense.cn/20201013174038.png)![](http://img.susense.cn/20201013174117.png)

<img src="http://img.susense.cn/1-20031311441DG.jpg" style="zoom:67%;" />

### 版本情况

| 版本   | 时间     | 内容         |
| ------ | -------- | ------------ |
| V2.0.0 | 2020-8-11 | 产科信息系统产检、催检，动态配置系统 |
| V1.9.0 | 2020-7-17 | 消息预警系统，任务调度系统，APP升级 |
| V1.8.0 | 2020-6-7 | 自动评分系统，监测数据升级，app升级 |
| V1.7.0 | 2019-12-2 | 院内系统构建，服务拆分，架构升级 |
| V1.6.0 | 2019-11-1 | 报表统计，订单升级，app 升级 |
| V1.5.0 | 2019-9-20 | 资讯、小工具、提醒等，小程序升级 |
| V1.4.0 | 2019-7-31 | 服务监测，app升级 |
| V1.3.0 | 2019-7-1 | 血压，血糖，体重等监测 |
| V1.2.0 | 2019-6-1 | 院外SaaS系统、APP、小程序 |





## 技术框架



### 基础研发平台（DevOps）


<img src="http://img.susense.cn/devops.jpeg" alt="devops" style="zoom:60%;" />

为提研发协作效率，平台内部提供了一整套实践DevOps 和敏捷化的工具和流程，其中包括：

- 需求及缺陷跟踪JIRA
- 持续集成Jenkins，GitLab CI/CD
- 配置中心，携程Apollo
- 代码仓库 GitLab
- 构建仓库，Maven私服，Sonatype Nexus Repository Manager
- 系统原型及UI 管理
- 代码质量系统SonarQube
- 自动化测试工具 selenium、JMeter
- 日志监控 Nagios、prometheus
- 基于docker 和Kubernetes 的容器化部署



详细内容，可以到 [DevOps](http://doc.susense.cn/#/1.basic/devops/README) 查看。



### 研发平台技术栈

![](http://img.susense.cn/wehealthCh.jpg)



- 技术架构采用分布式框架spring cloud及相关技术栈
  - spring boot
  - Hystrix/Ribon
  - Eureka、Nacos
  - spring cloud zuul、spring cloud gateway
  - spring boot admin
  - 认证授权 shiro ，Jwt
  - 链路监控 Sleuth、zipkin 、Skywalking
- 日志系统
  - ELK （Elasticsearch+Logstash+Kibana）
- 消息队列
  - RabbitMQ
- 定时任务系统
  -  Quartz Job Scheduler
- 数据缓存
  - Redis
- 数据库存储
  - mysql 5.7
- 非关系型数据存储
  - qiniuCloud 文件存储
  - hadoop  3.2
  - Hbase 2.1.7
- 前端负载均衡
  - nginx





### 创新亮点

!>  其中技术上和设计上的创新，部分已申请专利。

- 基于电商模型的商品及服务套包组合设计方案；

- 基于混合云模式的通用客户端接入模式、流程设计方案；

- 基于医疗胎监数据的hadoop+hbase 非关系型数据存储；

- 基于事件驱动的消息模型、预警系统、和通知联动、处置系统；

    | 对比维度   | 常规模式               | 新架构                                             |
    | ---------- | ---------------------- | -------------------------------------------------- |
    | 复杂度支持 | 支持简单消息发送       | 可支持，结合设计模式，消息队列                     |
    | 多场景支持 | 可简单支持，代码中植入 | 可支持，设计模式和策略拆分                         |
    | 业务解耦   | 未能拆分，未解耦       | 架构优化设计，解耦拆分                             |
    | 预警事件   | 不支持                 | 支持                                               |
    | 多角色支持 | 简单支持               | 支持配置                                           |
    | 配置化     | 不完善                 | 支持配置（预警等级、事件类别、业务类型、预警方式） |
    | 可追溯     | 不支持                 | 支持                                               |
    | 预警可处置 | 不支持                 | 支持                                               |
    | 失败补偿   | 不支持                 | 支持                                               |
    | 定时任务   | 简单支持               | 框架支持，独立部署                                 |

- 基于多租户SaaS 平台，可配置化的档案、产检、产筛动态模型

- 基于日历模型的监测视图追踪看板特性；

- 医生端主治医师、院内医生三级推送方案；

- 医生端用户解读报告的抢单锁定方案；



### 业务价值

!> 经过系统改造和中台化建设，产生了良好的业务价值

- 持续交付能力加强。相比以往数月为周期，新技术框架下平均上线周期缩短到两周；
- 系统稳定性大幅提升。线上运维的故障率，连续二十几月系统未出现不可用的情况；
- 用户满意度提升。移动端各项使用，体验大幅提升；
- 业务数据提高。



## 系统预览



### 院内信息化系统



> 院内档案管理、产检项、产检次数的配置

<img src="http://img.susense.cn/wh11.png" style="zoom:50%;" />



> 产检的详细信息

<img src="http://img.susense.cn/wh12.png" style="zoom:50%;" />

### 院外远程监护系统

> 院外远程监护胎心图

<img src="http://img.susense.cn/wh1.png" style="zoom:50%;" />

> 院外远程监护套包可配置化

<img src="http://img.susense.cn/wh2.png" style="zoom:50%;" />

> 院外远程监护基于日历模型的检测追踪看板

<img src="http://img.susense.cn/wh3.png" style="zoom:50%;" />

> 基于事件驱动的消息预警和通知系统

<img src="http://img.susense.cn/wh4.png" style="zoom:50%;" />

> 基于事件驱动的消息预警和通知系统，任务调度系统

<img src="http://img.susense.cn/wh5.png" style="zoom:50%;" />

> 消息预警可配置化

<img src="http://img.susense.cn/wh6.png" style="zoom:51%;" />



### 区域平台(开放平台)



- 基于OAuth2 协议的统一接入授权
- 基于GateWay API 网关
- 基于spring Cloud Alibaba 框架组件



### 移动端



#### 孕妇端

<img src="http://img.susense.cn/%E6%88%91%E7%9A%84.png" alt="我的" style="zoom:50%;"/>
<img src="http://img.susense.cn/%E7%B1%BB%E5%88%AB.png" alt="类别" style="zoom:50%;"/>

#### 医生端

<img src="http://img.susense.cn/%E6%8A%A5%E5%91%8A%E8%A7%A3%E8%AF%BB.png" alt="报告解读" style="zoom:50%;" />


## 体验地址


```
http://183.11.235.36:8000/
```



