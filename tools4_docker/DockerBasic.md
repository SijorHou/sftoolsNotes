## reference
[docker 官网](https://docs.docker.com/)

[docker hub](https://hub.docker.com/)

[Bilibili 课程](https://www.bilibili.com/video/BV1gr4y1U7CY/?p=2&spm_id_from=pageDriver&vd_source=d13548dcb8cb26f0b71f3b365ede666f)

[Docker菜鸟教程](https://www.runoob.com/docker/docker-tutorial.html)

## 问题解决
[docker run hello-world 无法从镜像源拉取报错](https://blog.csdn.net/qq_52712971/article/details/141862621?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522C64B1263-50CA-4288-B8E9-ED1B552F555E%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=C64B1263-50CA-4288-B8E9-ED1B552F555E&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~top_positive~default-1-141862621-null-null.142^v100^control&utm_term=docker%3A%20Error%20response%20from%20daemon%3A%20Get%20https%3A%2F%2Fregistry-1.docker.io%2Fv2%2F%3A%20net%2Fhttp%3A%20request%20canceled%20while%20waiting%20for%20connection%20%28Client.Timeout%20exceeded%20while%20awaiting%20headers%29.&spm=1018.2226.3001.4187)

[docker search 报错](https://blog.csdn.net/qq_28908085/article/details/125346981?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522C176DA12-CA3D-48C3-B40B-6F82174DEE2D%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=C176DA12-CA3D-48C3-B40B-6F82174DEE2D&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduend~default-1-125346981-null-null.142^v100^control&utm_term=docker%20search%E5%91%BD%E4%BB%A4%E6%8A%A5%E9%94%99&spm=1018.2226.3001.4187)


[centos 镜像中无法使用 yum install 问题解决](https://blog.csdn.net/qq_41422009/article/details/122865240)

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
    <img src="/tools4_docker/pic_src/Docker作用.png" alt="图片描述" style="margin-bottom: 1px;">
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
    <img src="/tools4_docker/pic_src/Docker架构.png" alt="图片描述" style="margin-bottom: 1px;">
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
    <img src="/tools4_docker/pic_src/hello_world过程.png" alt="图片描述" style="margin-bottom: 1px;">
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
    <img src="/tools4_docker/pic_src/docker结构.png" alt="图片描述" style="margin-bottom: 1px;">
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

然后使用 `${}` 定义那些ID变量，在docker的删除命令中使用，即 `docker rmi -f $(docker images -aq)` 
和 `docker rm -f $(docker ps -aq)`

也可以先停止全部容器，然后普通删除： `docker stop ${docker ps -aq}` `docker rm ${docker ps -aq}`


***重要命令***
- `docker run -d CONTAINER_NAME`  启动守护式容器（后台服务器， docker服务在后台运行）
  - `docker run -d centos` 命令执行后，会立刻退出该容器，后台centos容器并没有运行，***Docker容器后台运行，必须有一个前台进程***
  - 所以还是使用 `docker run -it ...` 告诉容器不要中断，还有后续交互操作
- `docker logs CONTAINER_NAME/ID` 查看某个容器的日志
- `docker top CONTAINER_NAME/ID` 查看容器内运行的进程
- `docker inspect CONTAINER_NAME/ID` 查看容器内部细节

***重新进入容器***
- `docker exec [options] CONTAINER_NAME/ID COMMAND` 进入**正在运行的容器**并以命令行交互
  - `docker execu -it myCentos /bin/bash` 重新以交互式方式执行容器中的 bash
  - `Ctl + P + Q` 可以从交互式命令行中退出容器 
- `docker attach CONTAINER_NAME/ID`  重新进入容器
- ***两者区别：***
  - `docker exec` 是在容器中打开新的终端，可以启动新的进程，使用 `exit` 退出，不会停止容器
  - `docker attach` 直接进入容器启动命令的终端，不会启动新的进程，使用 `exit` 退出，会停止容器

***文件拷贝、导入导出***
- `docker cp [options] CONTAINER:SRC_PATH DEST_PATH   /   SRC_PATH CONTAINER:DEST_PATH`
  - `docker cp myCentos:/tmp/a.txt /home/sijorhou/Desktop/Docker_learningFile` 将 a.txt 文件从容器中移动到宿主机
- `export`
  - `docker export [options] CONTAINER` 将整个容器的文件系统导入到一个 tar 包中
  - `docker export myCentos > docker_mycCentos.tar` 将docker中的myCentos镜像，导出到宿主机命令执行目录下的 docker_myCentos.tar 文件中去
- `import` 
  - `docker import [option] file/url REPOSITORY:TAG` 导入 tar包中的内容，创建一个 文件系统镜像, 有如下 直接导入 和 标准输入流处理tar并管道传递给import命令 两种方式
  - `docker import xxx.tar repository_name:tag_version`
  - `cat xxx.tar | docker import - repository_name:tag_version`

<div style="text-align:center">
    <img src="/tools4_docker/pic_src/容器导入导出.png" alt="图片描述" style="margin-bottom: 1px;">
    <p>容器导入导出</p>
</div>


## 镜像
### 镜像概念
#### 镜像分层
执行`docker pull IMAGE_NAME` 命令的时候，Docker 会逐层下载镜像，***每一层都是一个 tar 归档文件***
执行`docker push IMAGE_NAME` 命令的时候，Docker 会将镜像分解为多个层并账户层上传

镜像分层允许Docker镜像由多个层组成，每一层代表 Dockerfile中的一个指令，镜像分层技术使得Docker由如下几个优势：
- 可维护性，如果需要更新一个镜像依赖，只需要重构相关层即可
- 共享层，不同镜像可以共享层，减少存储空间，提高了分发效率
- 缓存优化
- 安全性
  
#### UnionFS 联合文件系统
UnionFS 是一种分层、轻量级并且高性能的文件系统，***支持对文件系统的修改作为一次提交来一层层叠加***，同时可以将不同目录挂载到同一个虚拟文件系统下

***UnionFS 是Docker镜像的基础，镜像可以通过分层来进行集成，基于基础镜像可以制作各种具体的应用镜像***

<div style="text-align:center">
    <img src="/tools4_docker/pic_src/Docker镜像加载原理.png" alt="图片描述" style="margin-bottom: 1px;">
    <p>Docker镜像加载原理</p>
</div>

#### 重点理解
Docker 镜像层都是只读的，容器层是可写的

**当容器启动时，一个新的可写层被加载到镜像的顶部**

**这一层通常被称作 “容器层”， “容器层”之下的都叫做镜像层**

- test: Hub 上pull的镜像，如centos，仅仅具有最小系统，很多命令并不包含（vim、clear、tree）
- 在 镜像的一个容器中，如myCentos，下载 vim、clear、tree命令，***并提交容器副本使之成为一个新的镜像***
- 那么， 使用该新镜像生成的容器，一开始就带有上述三个命令

结合上面理解，一开始生成的容器，可以修改（可写入），其下层都是底层基本镜像，当修改后的容器要变为新的镜像时，该容器层也变为 底层镜像层的一部分

再用该新镜像生成容器时候，新容器则包含 下层新镜像（修改后的容器）所具有的特性

***command***
- `docker commit [options] CONINTAINER [REPOSITORY:TAG]` create a new image from a container's changes
  - `-a` autor
  - `-m` 提交的描述信息
  - `docker commit -m="added vim, tree, clear cmds" -a="sijorhou" myCentos centos-with-cmds:1.1`

<div style="text-align:center">
    <img src="/tools4_docker/pic_src/docker-commit定制镜像.png" alt="图片描述" style="margin-bottom: 1px;">
    <p>docker commit定制镜像</p>
</div>

<div style="text-align:center">
    <img src="/tools4_docker/pic_src/定制镜像使用.png" alt="图片描述" style="margin-bottom: 1px;">
    <p>使用定制镜像</p>
</div>

图中可以看到：

执行 `docker commit -m="addex vim, tree, clear cmds" -a="sijorhou" myCentos centos-with-cmds:1.1`命令之后，查看镜像，已经将 根据容器 `myCentos` 生成了 `centos-with-cmds:1.1` 镜像

创建一个 `centos-with-cmds:1.1` 镜像的容器： `docker run -it --name=cmdsCentos centos-with-cmds:1.1 /bin/bash` ，在该容器中使用 `tree` 命令，发现可以使用，并且 tmp中还有之前在 `myCentos` 中创建的测试文本，现在已经成为底层镜像的一部分了


### 本地镜像发布到阿里云
<div style="text-align:center">
    <img src="/tools4_docker/pic_src/本地镜像发布到阿里云流程.png" alt="图片描述" style="margin-bottom: 1px;">
    <p>本地镜像发布到阿里云流程</p>
</div>

***镜像生成方法***

***本地镜像推送到阿里云***

- 阿里云-容器镜像服务-实例列表-个人实例
- 进入个人实例后，先创建`命名空间`， 然后创建`命名空间下的镜像仓库`
- 执行`docker commit -m"changed yum source to aliyun source, added vim, tree, ncurses cmds" -a="sijorhou" aliyun-yumSrc-Centos aliyun-yum-src-centos` 将本地容器
- 执行创建的镜像仓库中的命令（登录、向Registry中 push本地image）
  - `docker login --username=aliyun_username generated_path` 登录阿里云Docker Registry
  - `docker tag [ImageID]/SOURCE_IMAGE_NAME[:TAG] generated_path/my_namespace/my_images:[IMAGE_VERSION]` 创建一个引用源镜像的 标签目标镜像
  - `docker push generated_path/my_namespace/my_images:[IMAGE_VERSION]` 推送到阿里云的仓库；重命名镜像，通过专有网络推送 到 Registry）
  - `docker pull generated_path/my_namespace/my_images:[IMAGE_VERSION]` 拉取镜像


***删除本地镜像后从阿里云镜像仓库下载镜像测试***

### docker私有库构建
- ***Docker Registry***， 一个官方工具，用于搭建私有的镜像仓库
- `docker pull registry` 下载私有仓库工具
- 运行私有库Registry，相当于本地有个私有的 Docker Hub
- `docker run -d -p hostPort:containerPort -v host_dir:container_dir --privileged=true registry`
  - `-d` 后台运行容器，返回容器ID（启动守护式容器）
  - `-p` 指定端口映射，先访问 `hostPort` 主机端口，再访问 `containerPort` 容器端口（实际上含义为：将宿主机的端口映射到容器的端口，使得可以通过宿主机的端口访问容器内部的registry服务）***对于不同私有仓库，意味着不同的registry容器服务，端口号也是不同的***
  - `-v` 绑定挂载一个容器卷， 指定仓库所创建的 registry容器的 `host_dir:container_dir` 目录下（默认是 `var/lib/registry`）
  - `--previleged=true` 给予容器特权模式，***允许容器访问宿主机所有设备，并且可移植性一些通常需要高级权限的操作（长用于需要特殊权限的容器，如运行Docker守护进程的容器）***
- 整个命令就是，创建一个 registry 容器作为私有仓库，私有仓库中存储镜像的位置在 `container_dir`，但是实际上数据的真正存储位置在 `host_dir`，将该宿主机目录挂载于容器目录下，Docker registry 容器会通过 `container_dir` 来操作 宿主机上 `host_dir` 中的数据
  - 这种挂载方式确保了，即使registry容器被删除或重启，存储在宿主机上的镜像数据也不会丢失；通过Docker registry进行访问、推送、拉取镜像时，这些操作实际上通过 registry容器来管理 `host_dir`中的实际数据
  - example（两种等效方式）：
    - `docker run -d -p 5000:5000 -v /private-registries/:/tmp/registry --privileged=true registry`
      - `/sijorhou/myregistry/` 是要挂载到容器中的宿主机资源，是宿主机上的一个目录或文件的绝对路径
      - `:` 分隔符，用于区分宿主机路径和容器内路径
      - `/tmp/registry` 容器内部的目录或文件路径，宿主机资源每挂载到的位置
    - `docker run -d -p 5000:5000 --mount type=bind,src=/private-registries/,dst=/tmp/registry --privileged=true registry`

### docker镜像与私有库的交互
- `curl -X GET http://hostIP:5000/v2/_catalog` 查看私有镜像仓库中的镜像列表
  - `/v2/_catalog` 路径会获取仓库目录，列出所有仓库的名称，并返回JSON格式数据，列出私有仓库中所有镜像的名称
- `docker tag [IMAGEID]/IMAGE_NAME[:TAG] hostIP:5000/IMAGE_NAME[:TAG]` 重建一个目标镜像标签（代表仓库中的标签完整的名称）
- 修改docker配置文件（/etc/docker/daemon.json） 使之支持 http（docker 默认不允许 http 推送镜像）
  - `"insecure-registries": ["hostIP:5000]` 告诉docker 本机IP下5000端口 私服库是安全的，可以接受并支持
- `docker push hostIP:5000/IMAGE_NAME[:TAG]`
- 再次查看私有镜像仓库中的镜像列表
- `docker pull hostIP:5000/IMAGE_NAME[:TAG]` 从私服库中拉取镜像

### 完整过程
<div style="text-align:center">
    <img src="/tools4_docker/pic_src/私有库交互1-tag生成.png" alt="图片描述" style="margin-bottom: 1px;">
    <p>tag生成</p>
</div>

<div style="text-align:center">
    <img src="/tools4_docker/pic_src/私有库交互2-直接push失败.png" alt="图片描述" style="margin-bottom: 1px;">
    <p>直接push失败</p>
</div>

<div style="text-align:center">
    <img src="/tools4_docker/pic_src/私有库交互3-docker配置允许http.png" alt="图片描述" style="margin-bottom: 1px;">
    <p>docker配置允许http</p>
</div>

<div style="text-align:center">
    <img src="/tools4_docker/pic_src/私有库交互4-重启服务后push.png" alt="图片描述" style="margin-bottom: 1px;">
    <p>重启服务后push</p>
</div>

## 容器数据卷

***运行一个带有容器卷存储功能的容器实例***
- `docker run -it/-d -v --mount type=bind,src=/host_dir/,dst=/container_dir/ --privileged=true IMAGE`
- `docker run -it/-d -v /host_dir/:/container_dir/ --privileged=true IMAGE`
 
环境打包成镜像，run后形成容器实例，希望这些数据能够持久化，如果不备份，容器实例删除则数据也消失，为了能保存数据，在 docker中使用 卷

***intro***
- 是什么： 容器数据卷可以将 docker 容器中的数据存储在 宿主机中，实现数据持久化
- 能做什么：
  - 数据卷 可在容器之间共享或重用数据
  - 卷中更改会直接实时生效
  - 数据卷中的更改不会包含在镜像的更新中
  - 数据卷生命周期一直持续到没有容器使用它为止

***examples***
- 宿主机，容器之间映射添加容器卷
  - 直接添加
    - `docker run -it -v /hd/:/cd/ --privileged=true --name=container_name registry` 
    - `docker  IMAGE/CONTAINER_ID` 查看数据卷是否成功挂载
    - 容器和宿主机之间数据共享： docker 和 主机之间，任一方修改数据，另一方都会自动更新获取。若主机在 docker关闭期间修改数据，则重启后 docker容器会进行数据同步
- 读写规则映射添加说明
  - 上述直接添加的命令是默认 `rw`，可读可写
  - **只读**的话需要限制容器实例内部只能读不能写
  - `docker run -it -v /host_dir/:/container_dir:ro/ --privileged=true IMAGE` 其中 `:ro` 声明了该容器实例目录只读（read only）
- 卷的继承
  - container1 完成和 host 的映射（执行上述添加容器卷操作）
  - `--volumes-from` container2 继承容器1 的卷规则 
    - `docker run -it --privileged=true --volumes-from container1 --name=container2 IMAGE`


<div style="text-align:center">
    <img src="/tools4_docker/pic_src/容器卷的继承.png" alt="图片描述" style="margin-bottom: 1px;">
    <p>容器卷的继承</p>
</div>

可以看到 `--volumes-from src_container` 参数，直接从源容器继承过来其所有内容

## Dcoker 常用软件安装
- `docker pull IMAGE_NAME`
- `docker images`
- `docker run images`
  
### docker MySQL 使用

[使用教程](https://hub.docker.com/_/mysql)

***使用MySQL镜像***
- **简单命令**
```shell
# 查看MySQL端口使用情况，如果本地没有MySQL，可以使用 3306 端口
# 运行一个MySQL容器实例
# 交互方式进入MySQL容器
# 执行语句然后输入密码进入 mysql

ps -ef | grep mysql
docker run -it --name=MySQLInstance -p 3306:3306 -e MYSQL_ROOT_PASSWORD=123456 -d mysql:latest
docker exec -it MySQLInstance /bin/bash   
mysql -u root -p
```

- **实战命令**

```shell
# 新建 mysql 容器实例
# 实际执行有三个挂载目录： /ForTest/mysql/log, data, conf/ 
# 分别对应容器目录为 /var/log/mysql, /var/lib/mysql, /etc/mysql/conf.d
# 其中 conf.d 是mysql的配置文件，用于存放 mysql配置信息（如字符配置）

docker run -d --name=MySQLInstance -p 3306:3306 --privileged=true -v /host_dir/:/container_dir/ -e MYSQL_ROOT_PASSWORD=123456 mysql:latest;

docker run -d --name=MySQLInstance -p 3306:3306 --privileged=true -v /ForTest/mysql/log/:/var/log/mysql -v /ForTest/mysql/data/:/var/lib/mysql -v /ForTest/mysql/conf/:/etc/mysql/conf.d -e MYSQL_ROOT_PASSWORD=123456 mysql:latest

# /ForTest/mysql/conf 中新建 my.cnf（内容如下），通过容器卷同步给mysql容器实例
[client]
default_character_set=utf8
[mysqld]
collation_server = utf8_general_ci
character_set_server = utf8

# 在 WSL 中进入 /ForTest/mysql/data/ 目录下，新建atguigudb.sql 并paste代码
# atguigudb.sql 在 mysql中是 /var/lib/mysql/atguigudb.sql
vim atguigudb.sql

# 启动进入mysql并查看配置文件，导入 atguigudb.sql
docker exec -it MySQLInstance
mysql -u root -p
mysql> SHOW VARIABLES LIKE 'character_set_%';
mysql> SOURCE /var/lib/mysql/atguigudb.sql
```
<div style="text-align:center">
    <img src="/tools4_docker/pic_src/docker挂载目录编写mysql配置文件.png" alt="图片描述" style="margin-bottom: 1px;">
    <p>docker挂载目录编写mysql配置文件</p>
</div>



***问题***
- 插入中文字符报错：执行 `SHOW VARIABLES LIKE 'character_set_%';` 发现许多都是 latin 字符编码选项，需要修改（前面创建mysql容器实例时候挂载目录，在host_dir的挂载目录中新建配置文件）
- 删除容器，mysql容器中数据如何备份？
  - 只要设定了容器卷保存数据，即使删除mysql容器，再次新建msyql容器实例，也会具有宿主机中存储的原来数据
  - 或者 commit生成新的镜像，下次直接根据原镜像构造容器







