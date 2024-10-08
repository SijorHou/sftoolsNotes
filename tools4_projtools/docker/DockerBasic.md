## reference
[docker 官网](https://docs.docker.com/)

[docker hub](https://hub.docker.com/)

[Bilibili 课程](https://www.bilibili.com/video/BV1gr4y1U7CY/?p=2&spm_id_from=pageDriver&vd_source=d13548dcb8cb26f0b71f3b365ede666f)

[Docker菜鸟教程](https://www.runoob.com/docker/docker-tutorial.html)

## 问题解决
[docker run hello-world 无法从镜像源拉取报错](https://blog.csdn.net/qq_52712971/article/details/141862621?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522C64B1263-50CA-4288-B8E9-ED1B552F555E%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=C64B1263-50CA-4288-B8E9-ED1B552F555E&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~top_positive~default-1-141862621-null-null.142^v100^control&utm_term=docker%3A%20Error%20response%20from%20daemon%3A%20Get%20https%3A%2F%2Fregistry-1.docker.io%2Fv2%2F%3A%20net%2Fhttp%3A%20request%20canceled%20while%20waiting%20for%20connection%20%28Client.Timeout%20exceeded%20while%20awaiting%20headers%29.&spm=1018.2226.3001.4187)

[docker search 报错](https://blog.csdn.net/qq_28908085/article/details/125346981?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522C176DA12-CA3D-48C3-B40B-6F82174DEE2D%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=C176DA12-CA3D-48C3-B40B-6F82174DEE2D&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduend~default-1-125346981-null-null.142^v100^control&utm_term=docker%20search%E5%91%BD%E4%BB%A4%E6%8A%A5%E9%94%99&spm=1018.2226.3001.4187)
问题未来解决

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
安装 Engine 之前，先安装 repository
```bahs
sudo yum install -y yum-utils
sudo yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo

# docker.com 国外网站，容易超时，配置阿里云镜像
sudo yum-config-manager --add-repo https://mirrors.aliyun.com/docker-ce/linux/centos/docker-ce.repo
```

***Ubuntu***
按照官网教程即可

***aliyun mirror configuration***

## hello-world 分析
<div style="text-align:center">
    <img src="/tools4_projtools/pic_src/hello_world过程.png" alt="图片描述" style="margin-bottom: 1px;">
    <p>hello_world过程</p>
</div>

***docker 为什么比虚拟机快***
- docker抽象层更少，CPU、内存利用率都更有效率
  - docker不需要 Hypervisor(虚拟机)实现硬件资源虚拟化
  - 运行在docker容器上的程序直接使用实际物理机的硬件资源
- docker利用宿主机内核，不需要加载 os 内核
  - 新建一个容器时，docker无需像虚拟机那样，重新加载一个 os内核（分钟级）
  - 直接使用宿主机os，新建一个docker容器只需几秒


## 常用 docker 命令

<div style="text-align:center">
    <img src="/tools4_projtools/pic_src/docker结构.png" alt="图片描述" style="margin-bottom: 1px;">
    <p>docker结构</p>
</div>

### 帮助启动类命令
- `systemctl start docker`
- `systemctl stop docker`
- `systemctl restart docker`
- `systemctl status docker`
- `systemctl enable docker` 设置开机自启动
- `systemctl disable docker` 禁用开机自启动
- `docker info` 查看docker概要信息
- `docker version` 查看docker版本
- `docker --help` 总体帮助文件查看命令
- `docker [command] --help` 查看某个命令帮助文件

### 镜像类命令
- `docker images` 列出所有的docker镜像，对应信息标签内容如下：
  - `REPOSITORY` 镜像源的仓库源： ***同一个REPOSITORY可以有多个TAG，代表仓库源中不同版本***
  - `TAG` 镜像的标签**版本号**
  - `IMAGE ID`
  - `CREATED`
  - `SIZE`
- `docker search [option] TERM` 在 docker hub 中搜索镜像
  - `docker search hello-world` 
  - `docker search --limit 5 redis` 限制结果显示数量
- `docker pull [options] NAME[:TAG]` 拉取一个镜像（: 后面跟所需镜像版本号，默认 latest）
- `docker system df` 查看镜像/容器/数据卷所占空间
- `docker rmi [option] NAME` 移除某个镜像
  - `docker rmi -f hello-wordl` 强制移除 hello-world 镜像
  - `docker rmi -f NAME_ID` 删除单个
  - `docker rmi -f NAME:TAG NAME2:TAG` 删除多个
  - `docker rmi -f $(docker images -qa)` 删除全部


### 容器命令
- `docker run [options] IMAGE [COMMAND]` 新建并启动容器 
  - `options`
    - `--name` 为容器分配一个名字
    - `-d` run container in background and print container ID
    - `-i` 以交互式模式运行容器，通常与 `-t` 同时使用
    - `-t` 为容器分配一个伪输入终端，通常与`-i`同时使用
    - `-P` 随机端口映射
    - `-p` 指定端口映射 `-p hostPort:containerPort`
  - `docker run --name=myCentos -it centos /bin/bash` 
- `docker ps [options]` docker container list, 列出容器
  - `-a, docker ps -a` 列出所有容器
  - `-n 3` 显示最近3个容器
  - `-l` 显示最后使用的一个容器
  - `-q` 只显示 container ID `docker -aq`
  - `-s` 显示文件总大小
- `docker start CONTAINER_NAME/ID` 启动已经停止的容器
- `docker stop CONTAINER_NAME/ID` 停止容器
- `docker kill CONTAINER_NAME?ID` 强制停止容器
- `docker rm [options] CONTAINER` 删除一个或多个容器(删除已经停止的容器)
  - `docker rm -f RUNNING_CONTAINER` 可以强制删除一个启用的容器
  - `docker rm -f $(docker ps -aq)` 删除全部容器


***结合shell命令***
在删除全部镜像和全部容器的命令中， `docker images -aq` 和 `docker ps -aq` 是会分别列出所有镜像ID和容器ID的docker命令

然后使用 `${}` 定义那些ID变量，在docker的删除命令中使用，即 `docker rmi -f $(docker images -aq)` 和 `docker rm -f $(docker ps -aq)`

也可以先停止全部容器，然后普通删除： `docker stop ${docker ps -aq}` `docker rm ${docker ps -aq}`


***重要命令***


