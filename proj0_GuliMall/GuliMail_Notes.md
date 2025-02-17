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


