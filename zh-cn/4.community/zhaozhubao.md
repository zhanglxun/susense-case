## 项目背景

> 宝谷电商是一家珠宝行业垂直全产业链B2B平台，致力于提供珠宝、钻石领域的全供应链服务。公司成立于2014年，位于深圳市罗湖区翠竹街道，是中国第一家专注于珠宝现货的B2B交易型电商平台，拥有国内最大的珠宝现货资源。找珠宝网依托网站及移动端的全平台覆盖，打造珠宝行业的“互联网+”开放生态圈，让珠宝供应商、采购商和贸易商均能一站式尊享平台服务。



1. 项目名称：找珠宝网
2. 项目时间：2017年
3. 项目子系统：
   1. 移动端（android，IOS，H5 ，微信公众号）
   2. 数据接口平台
   3. 数据爬虫
   4. web端
   5. 通用化saas平台
   6. 运营管理控制台
   7. 分布式文件系统



> 业务情况

系统上线后的业务情况

- 上游钻石供应商 约 260 多家
- 提供是黄金和钻石SKU 数量，累计约200万+
- 商品数据更新周期，为每天4~5轮轮
- 月交易额约80w~130w，累计交易额约 2500w+
- toB客户数量，月2000+ 



## 系统价值



> 与传统电商相比，需解决垂直领域的特定问题。



- 钻石商品sku的为单SKU，数据量大；
- 数据价格变更频繁，需动态更新库存价格和库存；
- 对性能要求较高，需要进行大量的数据运算比价、更新价格、库存等；



行业特色有多层分销体系，包括供应链，经销商，分销商，采购商，等，需要多层级的价格体系和订单流程控制；在方案设计中，有很多亮点。



## 技术框架

系统采用Dubbo 相关技术栈构建。





<img src="http://img.susense.cn/zhaozhubao14.jpg" style="zoom:50%;" />



## 项目预览

> 垂直电商首页

<img src="http://img.susense.cn/zhaozhubao7.png" style="zoom:30%;" />



> 钻石搜索页

<img src="http://img.susense.cn/zhaozhubao8.png" style="zoom: 30%;" />



> 运营后台

<img src="http://img.susense.cn/zhaozhubao9.png" style="zoom:30%;" />



> 运营后台



<img src="http://img.susense.cn/zhaozhubao10.png" style="zoom:30%;" />



<img src="http://img.susense.cn/zhaozhubao11.png" style="zoom:30%;" />



## 体验地址

体验地址

```html
http://www.zhaozhubao.com/
```

