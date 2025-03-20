# 项目
[2024 尚硅谷java学习路线](https://www.bilibili.com/read/cv5216534/)

[项目资源](E:\010-WORKBENCH\GuliMall)

[java 项目精选](https://javaguide.cn/open-source-project/)

[优秀java开源项目](https://www.zhihu.com/question/58476787/answer/3314350408)


# Guli Mall Course Notes
## Introduction
***了解项目内容:谷粒商城***
- 分布式基础（全栈开发篇），逆向工程，快速打通全站开发能力
  - 技术栈
  - 后端： Spring Boot， Spring Cloud， Docker 
  - 前端： Vue, ElementUI
- 分布式高级（微服务器架构篇）
  - 实现整套商城业务逻辑
  - 会使用 Spring Boot,Cloud, ... 等 分布式高级技术
- 高可用集群（架构提升篇）

***项目中要学的前置知识***
- 技术
  - 前后端开发，基于vue的后台管理系统
  - SpringCloud解决方案
  - 应用监控、限流、网管、熔断降级等分布式方案
  - 分布式事务、分布式所
  - 高并发场景编程方式、线程池、异步编排
  - 压力测试与性能优化
  - 集群技术
  - CI/CD
  - ...
- 前置
  - SpringBoot及常见整合方案
  - SpringCloud
  - git、maven
  - linux、redis、docker 基本操作
  - html, CSS, js, Vue
  - idea开发


***分布式基础概念***
- ***微服务***：
  - 拒绝大型单体应用，基于业务边界进行服务微化查分，各个服务独立部署运行
  - 每个小服务运行在自己的进程中，使用轻量级机制通信（通常是HTTP API）
- ***集群 & 分布式***
  - ***集群是个物理形态***
  - ***分布式是一种工作方式***：将不同业务分布在不同地方
  - 分布式中每个结点都可以是集群
- ***远程调用***：分布式系统中不同主机上的微服务之间需要互相调用，称为`远程调用`
- ***负载均衡***：远程调用中，微服务调用方可以在不同集群上调用同一个所需的微服务，从而平衡不同主机的负载，不会太忙也不会太闲置
- ***服务注册/发现 & 注册中心***： 所有微服务上线运行时都先到注册中心进行注册，这样其他任何微服务都能看到该微服务的状态（集群位置、上线状态...）
- ***配置中心***：
  - 专门的存放不同微服务配置，可以集中管理位于不同主机上的一个微服务的配置并统一更新
  - 如某一个微服务的配置变更，该微服务在很多台主机上都有部署，不可能一一修改，所以`配置中心`集中管理配置信息，所有微服务自动根据配置中心的配置进行配置更新
- ***服务熔断 & 服务降级***
  - 微服务之间通过网络进行通信，彼此之间存在相互依赖，如果某一个服务不可用了，也会阻塞其他服务，因此 ***必须有容错机制***
  - ***服务熔断***：设置服务超时，被调用服务经常调用失败达到某个阈值，可以 ***开启断路保护机制***， 即后来的请求直接返回默认数据，不再调用该服务
  - ***服务降级***：系统高峰期资源紧张，让非核心业务的运行级别降低来运行，即 ***降级：简单处理或不处理某些服务***
- ***API网关***:在微服务架构中充客户端和后端服务端之间的中介，统一管理所有API请求，负责路由、协议转换、安全控制、监控等功能

## Practice
### docker 安装 mysql
[MySQL容器使用](https://hub.docker.com/_/mysql)

***commands***
```bash
# 创建mysql容器
docker run -p 3306:3306 --name sijor_mysql \
-v ~/mydata/mysql/log:/var/log/mysql \
-v ~/mydata/mysql/data:/var/lib/mysql \
-v ~/mydata/mysql/conf:/etc/mysql/conf.d \
-e MYSQL_ROOT_PASSWORD=root \
-d mysql

# 进入
docker exec -it sijor_mysql /bin/bash
```

***配置mysql***
```bash
vim ~/mydata/msql/conf/my.cnf

# 写入如下内容
[client]
default-character-set=utf8
[mysql]
default-character-set=utf8
[mysqld]
init_connect='SET collation_connection = utf8_unicode_ci' init_connect='SET NAMES utf8' character-set-server=utf8
collation-server=utf8_unicode_ci
skip-character-set-client-handshake
skip-name-resolve
```

### docker 安装 redis
[conf文件下载地址](https://raw.githubusercontent.com/antirez/redis/4.0/redis.conf)

```bash
# 先修改并配置 conf 文件 （参考 docker、redis笔记）
# 创建容器，挂载 /mydata/redis/的 data、conf文件
docker run -p 6379:6379 --privileged=true --name=sijor_redis\
-v ~/mydata/redis/data:/data \
-v ~/mydata/redis/conf:/etc/redis/redis.conf \
-d redis:latest \
redis-server /etc/redis/redis.conf

# 连接容器
docker exec -it redis redis-cli [-a 123456 -p 6379]

# redis 内部关闭或外部关闭
127.0.0.1:6379> shutdown

docker exec -it sijor_redis redis-cli shutdown

# 容器中的存储都是存于内存的，需要配置持久化
# redis.conf 中的 appendonly 设置为 yes
```

### 环境-开发工具-环境安装
#### Maven安装
- ***参考Maven 笔记的 settings.xml 的配置，然后配置到 IDEA中去。***
- 使用 IDEA 开发后端微服务，使用 vscode开发前端的后台管理系统 （前后端分离项目）


#### 项目结构创建

1. ***微服务模块创建（以商品服务模块创建为例）***
- `Spring initializer` 创建 module
- 创建服务： 商品服务、仓储服务、订单服务、优惠券服务、用户服务
  - 共同点：
    - 都导入 `web`、 `openfeign`模块
    - 每一个服务，包名为 `com.sijor.guilmall.xxx` (`xxx` 为 `product/order/ware/coupon/member` 等模块)
    - 模块名：`gulimall-coupon`


2. ***使用git远程仓库提交项目代码***
- 创建远程仓库
- 重点是整体项目、子项目模块（各个微服务模块）**只提交 `src`源码目录 和 `pom.xml`文件**
- 了解IDEA的 git分支使用（十分便捷，无需敲命令）

#### 数据库初始化

***Power Designer***

[软件破解下载安装教程](https://blog.csdn.net/WwLK123/article/details/132729462)

[软件使用教程](https://blog.csdn.net/lfdfhl/article/details/131328054?ops_request_misc=%257B%2522request%255Fid%2522%253A%252203f7686afa3d5e82598835f9435200a3%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=03f7686afa3d5e82598835f9435200a3&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~top_positive~default-1-131328054-null-null.142^v102^pc_search_result_base5&utm_term=Power%20Designer&spm=1018.2226.3001.4187)

- 使用 `Power Designer` 查看数据库设计
- 创建对应于模块的数据库，将 .sql 文件中的建表语句执行生成各个数据库的所有表


### 快速开发

后台管理系统：前后端内容的搭建费事，从人人开源获取这类管理系统相关框架，快速搭建
- 了解人人开源项目，快速搭建后台脚手架
- 修改代码调整为我们的业务逻辑
- 创建各个微服务以及数据库

#### Node.js 安装配置
[node.js 卸载教程](https://blog.csdn.net/weixin_43801036/article/details/141487791?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522ef6eacf0c45a10a727f049e75f8b3775%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=ef6eacf0c45a10a727f049e75f8b3775&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~top_click~default-1-141487791-null-null.142^v102^pc_search_result_base5&utm_term=node.js%E5%8D%B8%E8%BD%BD&spm=1018.2226.3001.4187)

- ***Node.js是运行在服务端的JavaScript运行时环境***
  - 官网下载安装 LTS Node.js（这里版本比较老旧，node.js 安装10.x.x 版本，Python 2.7.x，才不会报错）
  - 配置 npm镜像，无需从国外网站下载node.js 的相关包依赖 `npm config set registry http://registry.npm.taobao.org/`
- ***npm是Node.js的默认包管理器，相当于前端中的Maven***
  - 在项目中执行 `npm install` 会解析 `package.json` 中内容并下载所需要的包



















# 补充内容



## Spring initializr

**Spring Initializr 是 Spring 官方提供的一个用于快速创建和初始化 Spring 项目的在线工具**：它可以让开发人员选择所需的 Spring 模块、版本、编程语言等，自动生成项目的基本结构和配置文件，从而简化项目初始化过程

- 视频讲解中，创建 `module` 的时候，选择 `Spring initializr` 的方式，第一个界面的两个内容：`Module SDK 的选择`、`Choose initializr Service URL`
  - `Choose initializr Service URL`： 为 `https://start.spring.io/` 用于输入项目信息、Spring Boot 依赖
  - `Spring initializr` 会生成完整的Spring Boot项目的 zip文件
  - 下载解压zip文件，在 IDEA中打开即可
  - 这些流程都可使用 IDEA中的插件自动完成

***Spring Initializr = 在线 Spring Boot 项目生成器***






