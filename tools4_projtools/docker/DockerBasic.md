## reference
[docker 官网](https://docs.docker.com/)

[docker hub](https://hub.docker.com/)

[Bilibili 课程](https://www.bilibili.com/video/BV1gr4y1U7CY/?p=2&spm_id_from=pageDriver&vd_source=d13548dcb8cb26f0b71f3b365ede666f)

[Docker菜鸟教程](https://www.runoob.com/docker/docker-tutorial.html)


## 大纲
- 基础
  - 安装
  - 常用命令
  - Docker镜像
  - 本地云发布到阿里云
  - 本地镜像发布到私有库
  - Docker 容器数据卷
- 高级
  - 复杂安装
  - DockerFile解析
  - Docker微服务实战
  - Docker网络
  - Docker-compose容器编排
  - 轻量级可视化工具Portainer
  - 容器监控之 Cadvisor + InfluxDB + Granfana

## Intro
***What is it?***
"搬家 ——> 搬楼 " 的比喻： 即 "软件带环境安装(安装软件的时候，将原始开发环境一模一样地复制过来)"
 
 <div style="text-align:center">
    <img src="/tools4_projtools/pic_src/Docker作用.png" alt="图片描述" style="margin-bottom: 1px;">
    <p>Docker作用</p>
</div>


***docker idea*** ： 解决了运行环境和配置问题的软件容器，方便持续集成并有助于整体发布的容器虚拟化技术
***容器与虚拟机的比较*** ： 

- 虚拟机就是带环境安装的 一种解决方案，如在Windows中安装Linux虚拟机，两者之间毫无影响和关联，Linux用起来和真实系一致，实际上只是底层系统中的一个文件
- LXC Linux发展出的虚拟化技术 Linux Containers， Linux容器是与其他部分隔离开的一系列进程，从另一个镜像运行，该镜像提供支持进程所需的全部文件（应用的依赖项等）
- LXC不是模拟完整的OS，而是对 进程 进行隔离。***有了容器，可已将软件运行所需的所有资源打包到一个隔离的容器中***


***docker elements***

- 镜像 image， docker镜像文件相当于 java类模板
- 容器 container， docker容器实例相当于 java中new出来的实例对象
  - 镜像是静态定义，容器是镜像运行时的实体，***可以被启动、开始、停止、删除***
  - 包含内容：所包含的最小最核心的底层Linux内核文件；运行在其中的应用程序
- 仓库 repository， 集中存放镜像文件的地方（Docker Hub， 国内是 阿里云）

***docker architecture***

 <div style="text-align:center">
    <img src="/tools4_projtools/pic_src/Docker架构.png" alt="图片描述" style="margin-bottom: 1px;">
    <p>Docker架构</p>
</div>

docker client 和 daemon 之间通过 REST API 进行通信
- docker daemon (dockerd)： 守护进程，监听 docker api请求，管理镜像、容器、网络、卷等 docker 对象。守护进程 daemon可以和其他 daemons进行通信来管理docker服务
- docker client (docker)： 使用者与docker 交互的最原始方法就是通过 docker clinet。使用时 docker 将诸如 `docker run` 的命令发送给 dockerd 来执行。docker命令使用 Docker API，可与多个 daemons进行通信
- ...
- docker registries： `docker pull`、`docker run`、`docker push`
- docker objects
  - images:  a read-only template with instructions for creating a Docker container
  - container: a runnable instance of an image


1. users use Dcoker Client to communicate with Docker Daemon, send requests to Daemon
2. Docker Daemon 是架构中的主题··主体， 首先提供 Docker Server功能接受 Docker Client请求
3. Docker Engine 执行 Docker内部一系列工作，每个 工作以 一个 Job 形式存在
4. Job 运行过程，如需要 container 时， 从 Docker Registry 中下载镜像，通过 Graph driver（镜像管理驱动）， 将加载的镜像以 Graph形式 存储
5. 需要为 Docker 创建网络的时候，通过 Network driver （网络管理驱动）创建并配置 Docker容器网络环境
6. 需要限制Docker container运行资源后执行用户命令等操作时， 通过 Exec driver来完成
7. ***Libcontainer ： 一项独立的容器管理包， Network driver 和 Exec driver 都是通过 Libcontainer来实现对具体容器进行的操作的***

## Installation

***Centos***
1. 安装 Engine 之前，先安装 repository
```bahs
sudo yum install -y yum-utils
sudo yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo

# docker.com 国外网站，容易超时，配置阿里云镜像
sudo yum-config-manager --add-repo https://mirrors.aliyun.com/docker-ce/linux/centos/docker-ce.repo
```
2. `yum makecache fast` 更新yum软件包索引
3. 是d
4. 深度
5. 深度
6. 深度
7. 深度
8. 深度

***Ubuntu***