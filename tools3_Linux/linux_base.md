# 遗留问题
## 基础篇： 
### vmtools命令行安装
### 远程登录、文件传输等工具软件的下载
### vim命令学习

# linux 基础篇

## 课程基本内容
<div style="text-align:center">
    <img src="/proj2_linux/pic_source/content.png" alt="图片描述" style="margin-bottom: 1px;">
    <p>linux课程内容</p>
</div>

<div style="text-align:center">
    <img src="/proj2_linux/pic_source/拓展内容.png" alt="图片描述" style="margin-bottom: 1px;">
    <p>拓展内容</p>
</div>

## 虚拟机以及centos安装教程
[VMware虚拟机搭建Linux CentOS7（全网最详细图文讲解）](https://blog.csdn.net/Myx74270512/article/details/127883266?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522171430541616800227423510%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=171430541616800227423510&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduend~default-1-127883266-null-null.142^v100^pc_search_result_base8&utm_term=%E8%99%9A%E6%8B%9F%E6%9C%BAcentos%E5%AE%89%E8%A3%85&spm=1018.2226.3001.4187)

## 网络连接的三种模式
虚拟机中的 ***[NAT](https://www.xiaolincoding.com/network/4_ip/ip_base.html#nat)（Network Address Translation）是一种网络地址转换技术***，*它允许多个设备共享一个单一的公网IP地址来访问互联网*。NAT在虚拟化环境中非常常见，因为它允许虚拟机使用私有IP地址，同时通过宿主机的网络接口连接到外部网络。

网络连接的三种常见模式包括：

1. **桥接模式（Bridged Mode）**：
   - 在桥接模式下，虚拟机被当作网络上的独立设备，拥有自己的MAC地址和IP地址。虚拟机直接连接到物理网络，就像它是网络上的另一台物理机器一样。

2. **NAT模式（NAT Mode）**：
   - 如前所述，NAT模式允许虚拟机共享宿主机的IP地址。虚拟机通过宿主机的网络接口访问外部网络，宿主机负责将虚拟机的私有IP地址转换为公网IP地址。

3. **仅主机模式（Host-Only Mode）**：
   - 仅主机模式创建了一个虚拟的私有网络，只包括宿主机和虚拟机。在这种模式下，虚拟机不能直接访问外部网络，但可以与宿主机进行通信。这通常用于测试或开发环境，其中网络隔离是必需的。


## 虚拟机相关操作
### 虚拟机克隆
（linux本质是文件）
- 1. 方案1：将虚拟机文件夹复制一份，VM中打开
- 2. 方案2：关闭虚拟机，VM中右键克隆：克隆当前状态->创建完整克隆
- PS：虚拟机迁移删除也是如此，直接将整体文件夹进行拷贝和剪切到另外位置即可

### 虚拟机快照
想让虚拟机回到原来的某个正常状态，可以使用VM的虚拟机快照管理功能

- 1. 在执行某个操作前，如果想要保存当前虚拟机状态A，右键虚拟机，点击"快照"
- 2. 当执行若干操作后，可能有了多个快照 A->B->C->...
- 3. 若要回到之前的状态如B，右键虚拟机"快照管理器"，选择快照后，点击"转到"（可以产生新的快照分支）
<div style="text-align:center">
    <img src="/proj2_linux/pic_source/快照管理.png" alt="图片描述" style="margin-bottom: 1px;">
    <p>快照管理</p>
</div>

### vmtools安装
[安装vmtools]((https://blog.csdn.net/weixin_43624626/article/details/123451198?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522171453418416800197045550%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=171453418416800197045550&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~top_click~default-1-123451198-null-null.142^v100^pc_search_result_base8&utm_term=centos%E5%AE%89%E8%A3%85vmtools&spm=1018.2226.3001.4187))可以更好的管理vm虚拟机，如 ***可以设置windows和centos的共享文件夹***

<div style="text-align:center">
    <img src="/proj2_linux/pic_source/vmtools安装.png" alt="图片描述" style="margin-bottom: 1px;">
    <p>vmtools安装</p>
</div>

问题解决:
[centos7安装 VMTools显示灰色正确解决办法](https://blog.csdn.net/hsuehgw/article/details/129482915)

## 目录结构
Linux的目录结构以树形方式呈现，以下是Linux系统中一些常见目录及其作用：

1. **/root**：这是 ***系统管理员（也称为超级权限者）的用户主目录***，也就是root用户的家目录。
2. **/boot**：这个目录存放的是启动Linux时使用的核心文件，包括一些连接文件和镜像文件，如内核文件、引导加载器和启动程序等。
3. **/bin**：这个目录存放所有用户都可以使用的Linux操作命令，包括一些二进制文件。这些命令是系统启动即会用到的程序，不能关联至独立分区。
4. **/sbin**：这个目录保存和系统相关环境设置命令，只有超级用户可以使用这些命令进行系统环境设置，但有些命令可以允许普通用户查看。
5. **/lib** 和 **/lib64**：这两个目录存放了系统所需的一些共享库文件。其中，***/lib目录存放了启动时程序依赖的基本共享库文件以及内核模块文件***，而/lib64目录则是专用于x86_64系统上的辅助共享库文件存放位置。
6. **/etc**：这个目录是系统的配置文件存放目录，包含了许多系统和应用程序的配置文件，这些文件都是纯文本文件。
7. **/home**：这个目录是默认的用户家目录存放目录，每个普通用户都有自己的家目录，通常位于/home/用户名下。
8. **/media** 和 **/mnt**：这两个目录都与设备的挂载有关。/media目录是Linux系统自动识别并挂载一些设备（如U盘、光驱等）的目录，而/mnt目录则是临时文件系统挂载点，通常用于手工挂载设备。
9. **/dev**：这个目录类似于Windows的设备管理器，把所有的硬件用文件的形式存储。通过/dev目录下的文件，可以管理和访问系统中的各种设备。
10. **/opt**：这个目录是用来存放安装的可选软件的目录。一些第三方软件包或应用程序可以选择安装到/opt目录下，以便更好地管理和组织。
11. **/tmp**：这个目录是用来存放临时文件的目录。在Linux系统中，临时文件可能会产生，这些文件通常会被定期自动删除。
12. **/usr**：这个目录是系统软件资源目录，存储了用户环境的设置。根据不同的用户设置，这里会有不同的环境。同时，/usr/local目录是Linux额外的软件安装的目录，一般是通过编译源码的方式安装目录。
13. **/var**：这个目录用于存储额外产生日志的文件和其他动态数据。
14. **/proc** 和 **/sys**：这两个目录都是虚拟文件系统，主要保存系统的内核、进程、外部设备状态和网络设备状态等信息。

<div style="text-align:center">
    <img src="/proj2_linux/pic_source/linux目录结构1.png" alt="图片描述" style="margin-bottom: 1px;">
    <img src="/proj2_linux/pic_source/linux目录结构2.png" alt="图片描述" style="margin-bottom: 1px;">
    <img src="/proj2_linux/pic_source/linux目录结构3.png" alt="图片描述" style="margin-bottom: 1px;">
    <p>linux目录结构</p>
</div>

## 远程登录及文件传输
1. 公司开发的具体场景
    - linux服务器是开发小组共享的
    - 正式上线项目运行在公网
    - 程序员需要远程登录到linux进行项目管理或开发
    - 远程登录客户端有 Xshell6（用于远程登录）、Xftp6（传输文件）


## vi 和 vim 的使用


