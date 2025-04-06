# 拓展
1. systemed
   1. [systemctl 命令详解](https://blog.csdn.net/baidu_41553551/article/details/125303909?ops_request_misc=%257B%2522request%255Fid%2522%253A%25229195543C-816D-4D13-BDE6-E2D0D729FFB5%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=9195543C-816D-4D13-BDE6-E2D0D729FFB5&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~top_positive~default-1-125303909-null-null.142^v100^pc_search_result_base5&utm_term=systemctl&spm=1018.2226.3001.4187)
   2. [systemed 官网](https://systemd.io/)
   3. [完全指南：systemctl命令及服务管理技巧](https://blog.csdn.net/qq_41308872/article/details/133743091?ops_request_misc=&request_id=&biz_id=102&utm_term=systemctl&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-1-133743091.nonecase&spm=1018.2226.3001.4187)
2. ps
   1. [ps 命令详解](https://blog.csdn.net/qq_40673786/article/details/135166627?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522935040D8-6D90-483E-B978-0BC8748026F6%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=935040D8-6D90-483E-B978-0BC8748026F6&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-2-135166627-null-null.142^v100^control&utm_term=Linux%E7%9A%84%20ps%E5%91%BD%E4%BB%A4&spm=1018.2226.3001.4187)
3. grep
   1. [grep 命令详解](https://blog.csdn.net/m0_53741670/article/details/129484597?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522E7F25FC7-5E3B-4969-ADDA-2A9372F8E5C5%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=E7F25FC7-5E3B-4969-ADDA-2A9372F8E5C5&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-4-129484597-null-null.142^v100^control&utm_term=Linux%E7%9A%84%20grep%E5%91%BD%E4%BB%A4&spm=1018.2226.3001.4187)



# 问题解决
1. `yum install tree` 安装包的时候报错
[yum命令报错“Could not resolve host: mirrorlist.centos.org； Unknown error“解决办法](https://blog.csdn.net/qq_34585611/article/details/140390894?ops_request_misc=%257B%2522request%255Fid%2522%253A%25225C09FF9F-8CFF-4298-9A8D-C252717F3B7C%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=5C09FF9F-8CFF-4298-9A8D-C252717F3B7C&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduend~default-5-140390894-null-null.142^v100^pc_search_result_base5&utm_term=Could%20not%20resolve%20host%3A%20mirrorlist.centos.org)
    
2. 无ens33无网络问题
[问题解决教程](https://blog.csdn.net/wangning0714/article/details/130841243?ops_request_misc=&request_id=&biz_id=102&utm_term=%E8%99%9A%E6%8B%9F%E6%9C%BALinux%E6%B2%A1%E6%9C%89%E7%BD%91%E7%BB%9Cens33&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-2-130841243.142^v100^pc_search_result_base5&spm=1018.2226.3001.4187)


3. WSL 与 Windows互ping
[WSL ping Windows-防火墙问题](https://blog.csdn.net/Cypher_X/article/details/123011200)
[WSL ping Windows](https://blog.csdn.net/wtl1992/article/details/138133428?ops_request_misc=%257B%2522request%255Fid%2522%253A%252259E1025D-886C-4B7D-9556-D6953E5469A4%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=59E1025D-886C-4B7D-9556-D6953E5469A4&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduend~default-2-138133428-null-null.142^v100^control&utm_term=wsl2%20ping%E4%B8%8D%E9%80%9A%E4%B8%BB%E6%9C%BA&spm=1018.2226.3001.4187)

执行如下命令即可`New-NetFirewallRule -DisplayName "WSL" -Direction Inbound  -InterfaceAlias "vEthernet (WSL (Hyper-V firewall))"  -Action Allow
`

[WSL 镜像共享主机代理](https://blog.csdn.net/weixin_62355896/article/details/134458330?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522D96D92CB-AE8B-468A-8C2F-4D5BF9D06DB7%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=D96D92CB-AE8B-468A-8C2F-4D5BF9D06DB7&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduend~default-2-134458330-null-null.142^v100^control&utm_term=wsl%3A%20%E6%A3%80%E6%B5%8B%E5%88%B0%20localhost%20%E4%BB%A3%E7%90%86%E9%85%8D%E7%BD%AE%EF%BC%8C%E4%BD%86%E6%9C%AA%E9%95%9C%E5%83%8F%E5%88%B0%20WSL%E3%80%82NAT%20%E6%A8%A1%E5%BC%8F%E4%B8%8B%E7%9A%84%20WSL%20%E4%B8%8D%E6%94%AF%E6%8C%81%20localhost%20%E4%BB%A3%E7%90%86%E3%80%82&spm=1018.2226.3001.4187)

4. [开启虚拟机蓝屏问题解决](https://blog.csdn.net/qq_27597629/article/details/136034631?ops_request_misc=&request_id=&biz_id=102&utm_term=vm%20%E8%99%9A%E6%8B%9F%E6%9C%BA%E5%BC%80%E5%90%AF%E8%93%9D%E5%B1%8F&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-0-136034631.142^v100^pc_search_result_base5&spm=1018.2226.3001.4187)

5. WSL 安装相关
[安装教程](https://blog.csdn.net/weixin_57367513/article/details/135001273?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522361806df1bfdc7d547f107797dea931d%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=361806df1bfdc7d547f107797dea931d&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~top_click~default-2-135001273-null-null.142^v102^pc_search_result_base5&utm_term=WSL%E5%AE%89%E8%A3%85%E6%95%99%E7%A8%8B&spm=1018.2226.3001.4187)
[安装出错解决](https://blog.csdn.net/wangaolong0427/article/details/124213873?ops_request_misc=&request_id=&biz_id=102&utm_term=Installing,%20this%20may%20take%20a%20fe&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-6-124213873.142^v102^pc_search_result_base5&spm=1018.2226.3001.4187)

[ssh 连接WSL出错](https://blog.csdn.net/weixin_41642203/article/details/139320483?utm_medium=distribute.pc_relevant.none-task-blog-2~default~baidujs_utm_term~default-0-139320483-blog-119817163.235^v43^pc_blog_bottom_relevance_base7&spm=1001.2101.3001.4242.1&utm_relevant_index=3)

# linux 基础篇

## 课程基本内容
<div style="text-align:center">
    <img src="/tools3_Linux/pic_source/content.png" alt="图片描述" style="margin-bottom: 1px;">
    <p>linux课程内容</p>
</div>

<div style="text-align:center">
    <img src="/tools3_Linux/pic_source/拓展内容.png" alt="图片描述" style="margin-bottom: 1px;">
    <p>拓展内容</p>
</div>

## 虚拟机以及centos安装教程
[VMware虚拟机搭建Linux CentOS7（全网最详细图文讲解）](https://blog.csdn.net/Myx74270512/article/details/127883266?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522171430541616800227423510%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=171430541616800227423510&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduend~default-1-127883266-null-null.142^v100^pc_search_result_base8&utm_term=%E8%99%9A%E6%8B%9F%E6%9C%BAcentos%E5%AE%89%E8%A3%85&spm=1018.2226.3001.4187)

[VM 卸载](https://blog.csdn.net/weixin_55118477/article/details/121078890)

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
    <img src="/tools3_Linux/pic_source/快照管理.png" alt="图片描述" style="margin-bottom: 1px;">
    <p>快照管理</p>
</div>

### vmtools安装
[安装vmtools]((https://blog.csdn.net/weixin_43624626/article/details/123451198?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522171453418416800197045550%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=171453418416800197045550&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~top_click~default-1-123451198-null-null.142^v100^pc_search_result_base8&utm_term=centos%E5%AE%89%E8%A3%85vmtools&spm=1018.2226.3001.4187))可以更好的管理vm虚拟机，如 ***可以设置windows和centos的共享文件夹***
    
<div style="text-align:center">
    <img src="/tools3_Linux/pic_source/vmtools安装.png" alt="图片描述" style="margin-bottom: 1px;">
    <p>vmtools安装</p>
</div>

问题解决:
[centos7安装 VMTools显示灰色正确解决办法](https://blog.csdn.net/hsuehgw/article/details/129482915)
这里实际上在开启虚拟机的时候就点击VMware查看，`重新安装VMware Tools` 会亮起来
注意进入虚拟机后，点击 `单列？` 登录 root 账户进行操作

***安装步骤***
1. `VMwareTools-10.3.22-15902021.tar.gz` 拷贝到 `其他->计算机->opt` 文件夹中去
2. 打开终端
   1. `cd /opt` 进入 opt 目录， `ls` 展示文件夹中内容，可以看到拷贝过来的 `VM...`压缩包
   2. `tar -zxvf VM...` 解压该压缩包，`ls` 查看解压文件夹名字 `vm...`
   3. `cd vm...` 进入解压文件夹，`ls` 查看文件，找到 `vmware-install.pl` 安装文件
   4. `./vmware-install.pl` 执行安装文件（需要有 `gcc` 环境）
   5. 一直回车，最后一步选择 no


<div style="text-align:center">
    <img src="/tools3_Linux/pic_source/vm-tools安装后设置共享文件夹.png" alt="设置共享文件夹" style="margin-bottom: 1px;">
    <p>设置共享文件夹</p>
</div>

***设置共享文件夹***
1. Windows 中新建一个用于共享的文件夹
2. VMware 库中右键虚拟机，`设置 ——> 选项 ——> 共享文件夹 ——> 总是启用 ——> 添加主机路径` 然后确认完成
3. Linux如何访问共享文件夹？

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
    <img src="/tools3_Linux/pic_source/linux目录结构1.png" alt="图片描述" style="margin-bottom: 1px;">
    <img src="/tools3_Linux/pic_source/linux目录结构2.png" alt="图片描述" style="margin-bottom: 1px;">
    <img src="/tools3_Linux/pic_source/linux目录结构3.png" alt="图片描述" style="margin-bottom: 1px;">
    <p>linux目录结构</p>
</div>

## 远程登录及文件传输

### Xshell Xftp 使用
1. 公司开发的具体场景
    - linux服务器是开发小组共享的
    - 正式上线项目运行在公网
    - 程序员需要远程登录到linux进行项目管理或开发
    - 远程登录客户端有 Xshell6（用于远程登录）、Xftp6（传输文件）

2. [Xshell下载远程连接服务器教程](https://blog.csdn.net/qiujicai/article/details/139868155?ops_request_misc=&request_id=&biz_id=102&utm_term=xshell%E4%B8%8B%E8%BD%BD%E6%95%99%E7%A8%8B&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-1-139868155.nonecase&spm=1018.2226.3001.4187)

- `ifconfig` 查看Linuxi 的ip（ens33）
- Xshell中新建会话，设置名字、ssh连接方式、ip、22端口号
- 建立会话后双击会话，填写密码


3. Xftp 下载同理
- Xftp左上角文件-打开，可以新建会话
- 填写名称、ip、SFTP连接方式、22端口号、主机名、密码
- PS：建立会话连接后，Linux中文件乱码：修改会话属性为UTF-8

## vim 使用

三种模式：命令/普通模式、输入/插入模式、命令行模式

***命令/普通模式***
- `vim filename.fmt` 进入vim文本编辑（刚进入是 **普通/命令模式**）
- `iao` 以为不同方式进入插入模式
  - `i` 进入插入模式，从当前光标位置开始插入
  - `a` 进入插入模式，从当前光标的下一个位置开始插入
  - `o` 在当前光标所在行的下方插入空行，从空行开始输入（进入了插入模式）
  - `O` 在当前光标所在行的上方插入空行，从空行开始输入（进入了插入模式）
- `dd` 剪切光标所在行； `5dd` 剪切从光标所在行开始的下面 5行
- `yy` 复制光标所在行； `5yy` 复制从光标所在行开始的下面 5行
- `p` paste 将内容粘贴到光标所在行之下
- `P` paste 将内容粘贴到光标所在行之上
- `u` 撤销上一步操作
- `Ctrl + r` 重新操作一次撤销的内容
- `gg, G` 小写将光标定位到文本首行，大写将光标定位到末行 
- `num + shift g` 输入一个数字`num` 代表行号，按键会快速定位到该行 


***命令行模式***
- `[ESC] :w`  `[ESC]` 表可选，如果在输入/插入模式，按`[ESC]`退出到普通模式，然后进行 `write`写入，即保存
- `[ESC] :q` 退出Vim编辑器
- `[ESC] :wq` 保存并退出
- `[ESC] :q!` 强制退出，不保存
- `/ + keywords + Enter` 在普通模式时，左斜杠进入命令行模式，输入关键字，回车查询关键字
- `[ESC] :set nu` 在文本中设置行号
  - `[ESC] :set nonu` 在文本中取消设置行号


## Linux 关机重启
<div style="text-align:center">
    <img src="/tools3_Linux/pic_source/关机重启.png" alt="关机重启" style="margin-bottom: 1px;">
    <p>关机重启</p>
</div>

## 用户及用户组相关
### 用户登录和注销

- `su user` 登录一个用户（root、user）
- `logout/exit` 注销用户（无UI界面/UI界面），返回上一个登录的用户、退出系统 


### 用户管理

***账号管理***

- `useradd [option] username` 添加用户
  - `-c -d -g -s` 分别是： 指定一段注释性描述、指定创建目录、指定用户所属的组、指定用户登录的shell
  - `useradd -d home-path username` 一般添加用户的时候会指定该用户的家目录，通常是同名，如 `useradd -d /home/tom tom`, 也可以不同名， 不加设置默认同名
  - `useradd -g group_name username` 创建用户时指定属组，否则默认创建一个与username同名的属组
- `userdel [option] username` 删除用户
  - 默认删除，该用户的家目录不会被删除，`/etc/passwd, group, shadow` 中对应的用户的相关信息会删除
  - `userdel -r username` 删除用户时候连通用户的家目录一起删除
- `who am i` 查看当前用户（显示第一次登录的用户信息，避免切换用户造成混淆）
- `usermod [option] [username]` 修改用户相关属性
  - 如 `usermod -s /bin/ksh -d /home/z –g developer sam`,此命令将用户sam的登录Shell修改为ksh，主目录改为/home/z，用户组改为developer
  - `usermod -g new_group username` 修改用户的属组为 new_group
  - `usermod -d new_home_dir username` 修改用户的家目录为 new_home_group
  - `usermod -aG group_name user_name` 将用户加入 group_name 属组当中


***密码口令管理 `passwd`***
- `passwd [option] username` 超级用户可以为自己和其他用户设置 口令，但是普通用户只能为自己设置
- `passwd` 用户为自己设置口令
- `passwd [-ludf] username` 
  - `-l, -u` 分别是锁定用户（无法登录） 、解锁用户
  - `-d` 移除用户口令

### 用户组

***组管理***

- `groupadd [option] groupname` 新增一个用户组
  - `-g`修改组的GID用户标识, 如`groupadd -g 1005 userrr`
  - `-o` 一般与-g选项同时使用，表示新用户组的GID可以与系统已有用户组的GID相同
- `groupdel groupname` 删除用户组
- `groupmod [option] groupname` 修改用户组的属性（GID、名称）
  - `-g, groupmod -g 1002 userrr` 修改用户组 `userrr` 的GID 为 1002
  - `-n, groupmod -n newname userrr` 修改用户组 `userrr` 的名字 为 `newname`
  - `-o` 一般与-g选项同时使用，表示新用户组的GID可以与系统已有用户组的GID相同
- `newgrp othergroup` 一个用户有多个属组，切换到 `othergroup`

***用户账号相关文件***

- 完成用户管理的工作有许多种方法，但是每一种方法实际上都是对有关的系统文件进行修改
- 与用户和用户组相关的信息都存放在一些系统文件中，这些文件包括：
  - `/etc/passwd`
  - `/etc/shadow`
  - `/etc/group`
- 可以使用查看命令查看文件
  - 如 `cat /etc/passwd`，`tail -n 10 /etc/group`
- 用户信息
  - `/etc/passwd`中如 `sijorhou:x:1000:1000:sijorhou:/home/sijorhou:/bin/bash`
  - 含义为：`用户名:口令:用户标识号:组标识号:注释性描述:主目录:登录Shell`

<div style="text-align:center">
    <img src="/tools3_Linux/pic_source/用户和组相关文件.png" alt="用户和组相关文件" style="margin-bottom: 1px;">
    <p>用户和组相关文件</p>
</div>

### 运行级别

***指定运行级别***

- `init [0123456]` 切换不同运行级别
  - 0：停机模式，系统会关闭。
  - 1：单用户模式，用于系统维护。
  - 2：多用户模式，没有网络服务。
  - 3：完全多用户模式，具有网络功能。
  - 4：保留未使用。
  - 5：图形界面模式，具有网络功能。
  - 6：重启模式，系统会重启

常用 3， 5
**init 命令已经被 systemctl 命令取代**

- `systemctl get-default` 查看当前运行级别(target)
  - `graphical.target` 表运行的图形界面 5
  - `multi-user.target` 表多用户模式 3
- `systemctl set-defult xxx.target` 设置当前target
  - 如执行 `systemctl set-defult multi-user.target` 然后重启，则切换到命令行多用户模式


### 找回用户密码
1. 启动系统，进入开机界面，按 'e' 进入编辑界面
2. 进入编辑界面，键盘上下键移动光标向下，找到 'Linux16' 开头内容所在行数，在最后面输入 `init=/bin/sh`
3. 输入后按下 `Ctl + x` 进入单用户模式
4. 光标闪烁位置中输入 `mount -o remount,rw /`
5. 新一行最后输入新的 password，再次输入确认
6. 执行完 5 后进入新状态，在光标闪烁位置中输入 `touch ./autorelabel` 后回车
7. 继续在光标闪烁位置中输入 `exec /sbin/init` 后回车，等待系统自动修改密码并重启


## 帮助指令
- `man command` 查看 command的手册页
- `info command` 没有手册页可以查看 info页
- `command --help` 显示command的基本用法和选项
- `cd ..` 返回上一级目录
  
  <div style="text-align:center">
    <img src="/tools3_Linux/pic_source/返回上级目录.png" alt="返回上级目录" style="margin-bottom: 1px;">
    <p>返回上级目录</p>
</div>



## 文件目录管理
### 常用处理命令
- `pwd [-P]` (print work directory) 显示当前所在目录（绝对路径）(`-P` 显示真实目录，而不是链接的目录)
- `ls` (list files) 列出目录及文件
- `cd` (change directory) 切换目录
  - `cd ~` 回到家目录
  - `cd ../../` 回到上两级目录
- `mkdir [-mp]`
  - `mkdir -p xx/xx/` 参数`-p`可以递归创建多层目录
  - `mkdir -m 777 newdir` 参数`-m`可以在创建目录时候设置权限
- `rmdir [-p]` 
  - 删除（递归）目录
  - 先递归到最深删除该层目录，然后一层层返回上级父目录，若为空则删除，否则不删除
- `rm [-fir]` 移除文件或目录
  - `rm -rf xxx` 强制递归全部删除（慎用）
- `cp [-adflipusr]` 拷贝文件或目录
  - `cp [-adflipusr] source_file target_dir`
  - `\cp ,\cp -r/xxx/yyy /zzz` 将yyy目录连带拷贝到zzz，其中文件强制覆盖不提示
  - `cp [option] src1, src2, src3, ..., dir`
- `mv`
  - `mv [-fiu] source_file target_dir`
  - `mv [options] src1, src2, src3, ..., dir `
  - `mv file_name_a file_name_b` 在当前目录中将 file_name_a 移动到 file_name_b，相当于修改 file_name_a 的名称
  - `mv file_name_a /dir1/dir2/file_name_b` 移动并重命名

- `touch file_name` 顾名思义，“摸了”一下某个文件
  - 对于已经存在的文件，会修改文件时间戳（最后被修改的时间），该文件好像被“摸了”一下
  - 对于不存在的文件，会创建该空文件（无需`vim file_name` 进入然后退出）
- `ln [option] source [dest]` 创建一个原文件的软链接
  - `ln [option] source ... directory`
  - example: `ln -s /root /home/myroot` 在home目录下创建一个软链接（`-s`） myroot，指向 root

`link` 分为 ***软链接*** 和 ***硬链接***：

    Linux 文件系统中每个文件有两个数据结构： 索引节点（inode）和目录项（dentry），索引节点唯一标识一个文件。
    硬链接是指多个目录项都直接指向同一个 inode，当删除所有硬链接和源文件时，才会真正删除该文件。
    软链接是指多个目录项有自己的inode，其中存储的内容均为同一个文件的路径，删除文件后，软连接依然可以存在，只是找不到原文件了


### Linux 文件查看命令
<div style="text-align:center">
    <img src="/tools3_Linux/pic_source/文件目录类-more指令.png" alt="文件目录类-more指令" style="margin-bottom: 1px;">
    <p>文件目录类-more指令</p>
</div>
<div style="text-align:center">
    <img src="/tools3_Linux/pic_source/文件目录类-less指令.png" alt="文件目录类-less指令" style="margin-bottom: 1px;">
    <p>文件目录类-less指令</p>
</div>

***建议查看较大文件时候，直接使用 `less file_name`***
- `more, less [option] file` 文件显示
- `cat [-AbnvET] file`
  - `-A` 整合了 `vET` 的选项，列出特殊字符而不只是空白
  - `-b -n` 都是显示行号
  - `cat file | more` cat只能浏览不能修改文件，为了浏览方便，后接管道命令 `| more`。**管道命令就是将前一个命令的结果交给下一个命令进行处理**
- `tac file` 从最后一行开始，倒着显示每行内容
  - `tail -f file` 会一直循环读取文件末尾内容，即一直监控该文件的内容变化（可能在其他终端中在修改该文件）
- `nl file` 显示行号，但是有更丰富的行号显示的设置选项
- `head/taiil -n number file` 显示文件的前/后几行
  - `tail` 可以实时监控文件内容末尾变化（`-f`参数）
- `echo [option] [output_content]` 输出内容到控制台
  - `echo "hi, sijorhou!"` 控制台会输出 字符串内容
  - `echo $PATH / $HOSTNAME` 控制台会输出 路径 / 主机名
- `>` 输出重定向
  - `echo "xxx" > file_name` 原本命令输出内容到控制台，现在重定向为一个文件，即输出内容到该文件中（覆盖写入）
  - `ls -al > file_name` 将目录行列表内容覆盖写入 file_name 文件
- `>>` 输出内容追加重定向
  - `cat file_name1 >> file_name2` 会将 file_name1 中的内容追加输入到 file_name2 文件的末尾
  - `echo "str content" >> file_name` 将命令行输入内容追加到文件末尾
- 输出重定向、输出内容追加重定向，如果文件不存在则自动创建
- `history` 查看已经执行过的历史命令，也可以执行历史命令
  - `history 10` 查看最近执行的 10 条指令
  - `!num` 再次执行历史记录中编号为 num的指令

## 时间日期类
- `date` 显示当前日期时间
  - `date [option] [format]` 格式就是以 % 开头的多种各类型格式 
  - 格式：
    - `date +%Y` 显示当前年份
    - `date +%m` 显示当前月份
    - `date +%d` 显示当前日期时间
    - `date "+%Y-%m-%d-%H:%M:%S"` 显示当前年月日秒
  - 选项：
    - `-d` 显示 string 表示的时间，如 `date -d "2008-11-13 20:30:30"` 显示 `2008年 11月 13日 星期四 20:30:30 CST`
    - `-s` 根据 string 表示的时间，设定为当前系统时间
- `cal` 显示日历
  - `cal [option: -msy] [month] [year]`
  - `cal / cal -1` 默认显示当前月份日历
  - `cal 11 2023` 显示 2023年 11 月份的日历
  - `cal 2023` 显示2023全年日历
  - `-m -s -y` 分别是：周一作为第一天显示、周日作为第一天显示、显示当前全年的日历


## 查找指令
***find command***
- `find`
  - `find [path...] [expression]` 
  - `[path...]` path是搜索范围，find会从制定目录向下递归遍历各个子目录，将满足条件的文件、目录显示
  - `[expression]` expression 表达式是由 ***选项*** (选项总是影响所有的操作,而不仅仅是一个指定的文件的处理,而且总是返回真值)，***测试*** (测试返回一个真值或一个假值)，还有 ***动作*** (动作有side effects, 返回一个真值或假值)组成。它们 ***都以运算符分开，忽略运算符的时候，默认使用 -and 连接. 如果表达式没有包含 -prune 以外的动作，当表达式为真时会执行 -print 动作。***

- `-name<查询方式>` 按照制定的文件名查找模式查找文件
  - `find /mnt -name *.txt` 查找 mnt 目录下所有名字后缀为 .txt 的文件
- `-user<用户名>` 查找属于制定用户名的所有文件
- `-size<文件大小>` 按照制定的文件大小查找文件
  - `find /mnt -size +-nbk` 在 /mnt 目录下查找 大于（+）或小于（-）或等于 nb 或 nk 大小的文件

***locate, which***
- `locate`
  - `updatedb` 使用 `locate` 之前必须先执行 `updatedb`
  - `locate "*.txt"` 可以快速定位 txt文件 ...
- `which`
  - 可以查看某个指令在哪个目录下， 如 `which ls`

***grep |***
- `grep` 
  - 过滤查找，往往 和管道符 `|` 共同使用，即 `grep` 的处理结果传递给 `|` 后面的命令处理
  - `grep [option] searching-content src-file`
  - `-n` 显示匹配以及行号
  - `-i` 忽略字母大小写
- ***example***
  - `cat /mnt/hgfs/vmshared/test-file.txt | grep -in "re"`
  - 可以观察到，`cat` 输出内容，交给 `grep` 进行过滤查找， 以及两种 参数也起到了 显示匹配行号 以及 忽略大小写查找的作用
  - `grep -i -n "this" /mnt/hgfs/vmshared/test-file.txt` 效果是一样的

<div style="text-align:center">
    <img src="/tools3_Linux/pic_source/grep.png" alt="文件目录类-less指令" style="margin-bottom: 1px;">
    <p>grep</p>
</div>

## 压缩和解压类
***gzip/gunzip***
- `gzip` 是最常用的压缩工具之一，可以压缩文件，减小文件大小，***通常用于文本文档***，压缩比率很高
  - `gzip filename` 会创建一个filename.gz的压缩文件，原始文件会被删除
  - `gzip -c filename > filename.gz ` 会压缩filename并输出到filename.gz，同时保留原始文件
  - `gunzip filename.gz` 会解压缩filename.gz，恢复原始文件

***zip/unzip***
- `zip` 用于压缩文件（目录）， `unzip`用于解压缩
  - `zip [option] filename.zip file1 file2 file3` 创建一个包含 file1、file2 和 file3 的 archivename.zip 归档文件
  - `-r` 递归压缩（压缩目录），如 `zip -r myhome.zip /home/, [将home目录及其包含的文件、目录都压缩]`
- `unzip [option] filename.zip` 解压缩 archivename.zip，恢复所有文件和目录
  - `-d` 指定解压后的文件存放的目录，如 `unzip /opt/tmp /home/myhome.zip, [将 /home/下的myhome.zip 文件解压到 /opt/tmp/目录下]`

  <div style="text-align:center">
    <img src="/tools3_Linux/pic_source/zip-lrn.png" alt="文件目录类-less指令" style="margin-bottom: 1px;">
    <p>zip/unzip的使用</p>
</div>

注意：归档 和 压缩 是相关但不同的概念，前者合并多个文件、目录为一个单一的文件，并不会减小文件大小，而压缩会减小文件大小

- `tar -cvf archivename.tar file1 file2 file3 `创建一个包含 file1、file2 和 file3 的archivename.tar 归档文件
- `tar -czvf archivename.tar.gz file1 file2 file3`  创建一个 gzip 压缩的 archivename.tar.gz 归档文件
- `tar -xvf archivename.tar`解压缩 archivename.tar
- `tar -xzvf archivename.tar.gz` 解压缩 gzip 压缩的 archivename.tar.gz
- 参数：
  - `-c` 产生 .tar 打包文件
  - `-v` 显示详细信息
  - `-f` 指定压缩后的文件名
  - `-z` 打包同时压缩
  - `-x` 解包 .tar 文件
- example：
  - `tar -czvf /home/pig.tar.gz /home/pig.txt /home/cat.txt` 压缩多个文件，将 /home/pig.txt 和 /home/cat.txt 压缩成 pc.tar.gz
  - `tar -czvf myhome.tar.gz /home/` 将 /home 的文件夹 压缩成 myhome.tar.gz
  - `tar -xzvf pc.tra.gc` 将 pc.tar.gz 解压到当前目录
  - `tar -xzvf myhome.tar.gz -C /opt/tmp2` 将 myhome.tar.gz 解压到 /opt/tmp2目录下

## 文件目录类基本属性
[文档基本属性](https://www.runoob.com/linux/linux-file-attr-permission.html)

- `ls -l` 长格式显示文件属性信息，列出当前目录中的所有有文件目录
  - `-a` 显示全部
  - `-s` 显示块大小
  - `-h` 和 `-l` 连用，文件大小以 K M G 的易读格式显示

### 更改文件属组、属主

- `chgrp [-R] new_group file` 将 file的 属组修改为 new_group。[] 是可选项，-R 表递归地修改 file中内容的对应属性
- `chown [-R] new_owner file` 将 file的 属主修改为 new_owner
- `chown [-R] new_owner:new_group file` 同时修改（除此之外上面两命令都只修改一种）

<div style="text-align:center">
    <img src="/tools3_Linux/pic_source/文件属组属主更改.png" height=60% width=60% alt="文件属组属主更改" style="margin-bottom: 1px;">
    <p>文件属组属主更改</p>
</div>

<div style="text-align:center">
    <img src="/tools3_Linux/pic_source/文件属主属组.png"  alt="文件属组属主" style="margin-bottom: 1px;">
    <p>文件属主属组</p>
</div>

- 当在一个用户下创建文件/目录时候，其属主和属组都默认为该用户
- 对于一个文件/目录，不同的用户、不同的组可以设置对该文件的不同权限
- 注意相关命令的区别：
  - `groupmod` 修改属组的属性（-g 修改group的GID， -n 修改group的name）
  - `usermod` 修改用户的属组等属性 （-g newgroup 修改user的group 为 newgroup， -G 添加新属组）
  - `chgrp [-R] new_group file, chown [-R] newuser:newgroup file` 修改 文件/目录 的属组、用户等属性

### 更改文件权限属性
<div style="text-align:center">
    <img src="/tools3_Linux/pic_source/ls-l命令内容结构.png"  alt="ls-l命令内容结构" style="margin-bottom: 1px;">
    <p>ls-l命令内容结构</p>
</div>

- 从前向后看属主、属组、其他对文件的权限（root对任何文件、目录有绝对权限）
  - 属主权限
  - 属组权限：用户是按组分类的，一个用户属于一个或多个组。文件所有者以外的用户又可以分为文件所属组的同组用户和其他用户。如 `drwxr-xr-x 3 mysql mysql 4096 Apr 21  2014 mysql` mysql 文件是一个目录文件，属主和属组都为 mysql，属主有可读、可写、可执行的权限；与属主同组的其他用户有可读和可执行的权限；其他用户也有可读和可执行的权限

<div style="text-align:center">
    <img src="/tools3_Linux/pic_source/文件属性.png"  alt="文件属性" style="margin-bottom: 1px;">
    <p>文件属性</p>
</div>

- `chmod [-R] xyz file_or_dir` 更改文件权限属性

Linux文件属性有两种设置方法，一种是数字，一种是符号。

**Linux 文件的基本权限就有九个**，分别是 owner/group/others(拥有者/组/其他) 三种身份各有自己的 read/write/execute 权限

***rwxrwx---***  
- 分别代表 owner(rwx)group(rwx)other(---)
- 其中 r:4、w:2、x:1 为各自的分数
- rwxrwx---代表 770，即（rwx = 4 + 2 = 1 = 7）, - 则为0
- 所以，以数字的方式修改权限： `chmod 754 xxx.txt/dir` 即为 修改属性权限为 `-rwxr-xr-- `

***实际上使用属组囊括了各种组合关系，本质是二进制***
- 1 `x`
- 2 `w`
- 3 `wx`
- 4 `r`
- 5 `rx`
- 6 `rw`
- 7 `rwx`


***符号类型修改权限***
- user、group、others可以用 u、g、o 代替。（a 为 all）
- 读写权限可以写成 r、w、x
- 例：`chmod 754 xxx.txt/dir` 相当于 `chmod u=rwx,g=rx,o=r xxx.txt/dir`

***案例***
给abc文件的所有者读写执行的权限，给所在组读执行权限，给其它组读执行权限
- `chmod 755 abc`
- `chmod u=rwx, g=rx, o=rx abc`

给abc文件的所有者除去执行的权限，增加组写的权限
- `chmod u-x, g+w abc`

给abc文件的所有用户添加读的权限
- `chmod a+r abc`

## 权限管理应用实例

### SSH-用户连接
***1. 多个用户通过SSH使用相同的IP和端口连接到Linux服务器***

- **可行性**：是的，多个用户可以同时通过SSH使用相同的IP地址和端口（默认是22）连接到Linux服务器。
- **并发连接**：SSH服务设计为可以处理多个并发连接，每个用户可以有自己的独立会话。
- **资源消耗**：多个并发SSH会话会消耗服务器资源，包括CPU和内存，如果连接数过多，可能会影响服务器性能。
- **安全性**：SSH使用加密保护数据传输，确保即使多个用户同时连接，他们之间的数据也是隔离的。

***2. 多个SSH连接访问远程Linux服务器上的同一个用户***

- **并发登录限制**：某些Linux发行版可能通过配置文件限制单个用户同时登录的会话数量。
- **SSH配置**：服务器的SSH配置文件可以设置参数，如 `MaxSessions`，来限制每个用户可以拥有的最大SSH会话数。
- **会话共享**：多个SSH会话是独立的，一个会话中的操作不会影响另一个会话。
- **终端多重性**：可以使用终端复用器如 `tmux` 或 `screen` 来允许多个用户同时在一个SSH会话中工作。
- **权限和安全**：所有通过同一个用户账户的SSH连接将具有该用户的权限，这可能引起安全问题，因此建议每个用户都有自己的账户。
- **资源使用**：多个并发SSH会话会增加服务器资源使用。
- **SSH连接管理**：可以通过 `who` 或 `w` 命令查看活跃的SSH会话，并通过 `ssh -t` 在用户的会话中执行命令。
虽然技术上允许多个用户通过SSH连接到同一个Linux服务器上的同一个用户账户，但出于安全和资源管理的考虑，这种做法并不推荐。最佳实践是为每个用户分配独立的账户，以确保适当的权限控制和安全隔离。


### 最佳实践-警察和土匪游戏
| police | bandit |
|-------------|------------|
| jack   | hong   |
|jerry   | qiang  |

- 创建组、用户
  - `groupadd police, groupadd bandit`
  - `useradd -g police jack/jerry,  useradd -g bandit hong/qiang`
  - `passwd username` 为每个用户设置密码
- jack 创建一个文件，自己可以读写，本组人可以读写，其他任何人没有权限
  - 新建会话登录 jack
  - `vim jackFile.txt`
  - 按要求修改权限：
    - `chmod 640 jackFile.txt`
- jack 修改改文件，其他组人可以读，自己组可以读写
  - `chmod 644 jackFile.txt` 或者 `chmod o+r jackFile.txt` 或者 `chmod u=rw`
- hong 投靠警察， 看看是否可以读写
  - `usermod -g police hong`

在 root 中查看 home下各个用户的权限，可以看到，虽然 jackFile.txt 设置为同组成员可以读，但是因为 jack 本身是只有自身能 rwx 的，所以 同组的 hong jerry 依然看不到jackFile.txt

所以，首先对用户设置权限：同组可访问
- `chmod 770 jack` 或者 `chmod g+rwx jack` root 用户 home 目录下执行对应命令，打开 jack用户权限

***如果要对文件目录内的文件进行操作，要首先拥有对于该目录的相应权限***

```bash
[root@sijorhou /]# ls -l /home
总用量 20
drwx------.  5 hong  police 4096 12月  1 22:02 hong
drwx------.  5 jack  police 4096 12月  1 21:45 jack
drwx------.  5 jerry police 4096 12月  1 22:01 jerry
drwx------.  3 qiang bandit 4096 12月  1 21:29 qiang
drwx------. 17 sjor  sjor   4096 12月  1 21:09 sjor
[root@sijorhou /]# ls -l /home/jack/jackFile.txt 
-rw-r--r--. 1 jack police 336 12月  1 21:45 /home/jack/jackFile.txt
[root@sijorhou /]# 

```

<div style="text-align:center">
    <img src="/tools3_Linux/pic_source/组别权限.png"  alt="组别权限" style="margin-bottom: 1px;">
    <p>组别权限</p>
</div>

**可以看到，hong 可以访问并在 jack 的目录中进行 rwx，但是 jackFile 只能读不能 wx， hong 对于 jack的权限和jerry相同。非同组的 qiang 无法访问 jack目录**



## crond 任务调度
`crond` 是 Linux 系统中的一个守护进程，用于执行定时任务，即在预定的时间自动执行指定的命令或脚本。`crond` 通过读取 `crontab` 文件来获取任务的调度信息。`crontab` 文件中定义了任务的执行时间以及要执行的命令。

### 基本概念

1. **crontab 文件**：存储定时任务的列表，每个用户可以有自己的 `crontab` 文件。
2. **cron 作业**：`crontab` 文件中的一个条目，定义了一个定时任务。
3. **cron 表达式**：用于指定任务执行的时间和频率，由五个或六个字段组成。

### cron 表达式

一个典型的 `cron` 表达式包含以下字段：

- **分钟**（0-59）
- **小时**（0-23）
- **日期**（1-31）
- **月份**（1-12 或 JAN-DEC）
- **星期几**（0-7，0 和 7 都代表星期日，或使用 SUN-SAT）
- **命令**：要执行的命令或脚本


| 特殊符号 | 含义 |
|----------|------|
| *        | 代表任何时间。比如第一个 "*" 就代表一小时中每分钟都执行一次的意思。 |
| ,        | 代表不连续的时间。比如 "0 8,12,16 * * * 命令"，就代表在每天的8点0分，12点0分，16点0分都执行一次命令 |
| -        | 代表连续的时间范围。比如 "0 5 * * 1-6 命令"，代表在周一到周六的凌晨5点0分执行命令 |
| */n      | 代表每隔多久执行一次。比如 "*/10 * * * * 命令"，代表每隔10分钟就执行一遍命令 |

**Examples**
| 时间                | 含义                                                         |
|---------------------|--------------------------------------------------------------|
| 45 22 * * * 命令    | 在22点45分执行命令                                           |
| 0 17 * * 1 命令     | 每周1的17点0分执行命令                                       |
| 0 5 1,15 * * 命令   | 每月1号和15号的凌晨5点0分执行命令                            |
| 40 4 * * 1-5 命令   | 每周一到周五的凌晨4点40分执行命令                            |
| */10 4 * * * 命令   | 每天的凌晨4点，每隔10分钟执行一次命令                        |
| 0 0 1,15 * * 1 命令 | 每月1号和15号，每周1的0点0分都会执行命令。注意：星期几和几号最好不要同时出现，因为他们定义的都是天，非常容易让管理员混乱。 |

### 常用命令

1. **crontab -e**：编辑当前用户的 `crontab` 文件。
2. **crontab -l**：列出当前用户的 `crontab` 文件内容。
3. **crontab -r**：删除当前用户的 `crontab` 文件。
4. **crontab -u username -e**：编辑指定用户的 `crontab` 文件（需要相应权限）。
5. **crontab -u username -l**：列出指定用户的 `crontab` 文件内容（需要相应权限）。

### 使用方法

1. **编辑 `crontab` 文件**：
   - 使用 `crontab -e` 命令打开当前用户的 `crontab` 文件进行编辑。如果是第一次使用，可能会提示选择一个编辑器。

2. **添加定时任务**：
   - 在 `crontab` 文件中添加一行，***格式为 `cron` 表达式后跟要执行的命令***。
   - 例如，要每天中午12点执行 `/usr/bin/backup.sh` 脚本，可以添加以下行：
     ```
     0 12 * * * /usr/bin/backup.sh
     ```

3. **保存并退出**：
   - 在编辑器中保存文件并退出。`crontab` 文件的更改会自动加载。

4. **列出定时任务**：
   - 使用 `crontab -l` 命令查看当前用户的定时任务列表。

5. **删除定时任务**：
   - 使用 `crontab -r` 命令删除当前用户的 `crontab` 文件，这将移除所有定时任务。

6. **管理其他用户的 `crontab`**：
   - 使用 `sudo` 命令来编辑或查看其他用户的 `crontab` 文件，例如 `sudo crontab -u username -e/l`。

### 注意事项

- 确保 `cron` 服务正在运行。可以使用 `systemctl status crond` 检查服务状态。
- 命令的执行环境可能与用户登录时的环境不同，特别是环境变量。在 `cron` 作业中，通常需要显式指定完整的路径。
- `cron` 作业的输出默认会发送到用户的邮箱。如果需要查看输出，可以重定向到文件中。
- 使用 `MAILTO` 变量可以指定输出邮件的接收者，例如 `MAILTO=myemail@example.com`。
- 确保 `crontab` 文件中的命令格式正确，否则 `cron` 可能无法正确解析。

通过 `crond` 和 `crontab`，你可以实现自动化任务调度，这对于系统维护、数据备份、定期报告等场景非常有用。

### 实例
***每隔一分钟，将当前日期信息，追加到 `/tmp/mydate`***
- `crontab -e`
- `*/1 * * * * date >> /tmp/mydate`

***每隔一分钟，将当前日期、日历信息，追加到 `/tmp/mycal`***
两个方案：1. 两条指令 2. 执行shell脚本
- 1. 两条指令
  - 
  - 
2. 执行shell脚本




---- 待完成 ： 
  权限管理应用实例 2， 3， 4； 
  crond调度应用实例



# 杂项

## 程序管理





### 工作管理

- `&` 将命令放入后台执行
  - `ping localhost > ping.log &`
- `Ctrl + Z` 将当前工作“暂停” 运行并放入后台
  - `vi ~/.bashrc` 后执行 `Ctrl + Z`
  - `find / -print` 后执行 `Ctrl + Z`
- `jobs [-lrs]` 查看工作
  - `jobs -l` 查看所有工作（列出进程号PID）
  - `jobs -r` 仅仅查看正在运行的工作
  - `jobs -s` 仅仅查看已经暂停的工作
- `bg %jobnumber` 恢复后台暂停任务（会在后台继续运行）
- `fg %jobnumber` 恢复后台工作到前台
- **终止进程**
  - `kill` 终止后台作业
    - `kill PID/%n` 杀死PID进程
    - `kill -9 PID/%n` 强制杀死任务
    - `kill -15 PID/%n` 以正常方式终止任务
  - `Ctrl + Z` 暂停
  - `Ctrl + C` 终止前台进程

### 进程查看实用命令
在 Linux 中，可以使用 `ps`、`top`、`htop` 等命令来查看进程，并且可以添加不同的 **过滤条件** 进行选择。例如，可以筛选特定用户的进程、特定父进程（PPID）下的进程，或者按照进程名称来查找。

---
#### ps

`ps` 是最基本的进程查看命令，它支持许多选项来筛选特定进程。


- **查看某个用户的进程** `ps -u username`
  - `ps -u root` 查看 `root` 用户的进程
- **按进程名称筛选** 
  - `ps aux | grep process_name` 使用 `grep` 查找特定进程
  - `ps aux | grep nginx` 查找 `nginx` 进程
- **按进程 ID（PID）筛选** `ps -p PID`
  - `ps -p 1234` 查看 PID 为 1234 的进程
- **按父进程 ID（PPID）筛选** 
  - `ps --ppid PPID` 查看某个进程的所有子进程
  - `ps --ppid 5678` 查看父进程 ID 为 5678 的所有子进程
- **按端口筛选（结合 `netstat`）** 
  - `netstat -tulnp | grep port_number` 查找占用特定端口的进程 
  - `netstat -tulnp | grep 8080` 查找占用 8080 端口的进程 

#### top

***动态查看进程的变化***

- **`top` 按用户筛选**
  - `top -u username`
  - `top -u root`  查看 `root` 用户的进程

#### pgrep 和 pkill

**`pgrep` 和 `pkill`（只查找进程）**

- **`pgrep` 根据进程名称查找进程 ID**
  - `pgrep process_name`
  - `pgrep nginx` 查找 `nginx` 的所有进程
- **`pkill` 终止某个进程**
  - `pkill -9 process_name`
  - `pkill -9 nginx` 终止 `nginx` 进程

#### lsof

**`lsof` 查看进程打开的文件**: `lsof`（list open files）可以用于查看某个进程打开的文件，或者查询某个端口的占用情况。

- **查看某个进程打开的所有文件**
  - `lsof -p PID`
  - `lsof -p 1234` 查看 PID 为 1234 的进程打开的文件
- **查看某个端口被哪个进程占用**
 - `lsof -i:port_number`
 - `lsof -i:3306` 查看占用 3306 端口的进程

#### pstree

**`pstree` 查看进程树**: `pstree` 以 **树状结构** 展示进程，方便查看 **父子进程关系**。

- `pstree -p username` 查看某个用户的进程树
- ``


#### 综合示例
- **查看 `root` 用户运行的 `nginx` 进程**
  - `ps aux | grep nginx | grep root`
- **查看 `python` 进程的 PID**
  - `pgrep python`
- **查找并终止占用 8080 端口的进程**
  - `lsof -i:8080`
  - `kill -9 $(lsof -t -i:8080)`
- **示查看进程 ID 为 5678 的所有子进程**
  - `ps --ppid 5678`

---

#### 总结
| 需求 | 命令 |
|------|------|
| 查看某个用户的进程 | `ps -u username` / `top -u username` |
| 查看某个进程的 PID | `pgrep process_name` |
| 查看特定 PID 的进程 | `ps -p PID` |
| 查看某个父进程（PPID）的子进程 | `ps --ppid PPID` |
| 查看占用某个端口的进程 | `lsof -i:port` / `netstat -tulnp | grep port` |
| 以树状结构查看进程 | `pstree -p` |
| 终止某个进程 | `kill -9 PID` / `pkill process_name` |

### 系统资源查看
#### 查看 Linux 系统方面相关信息的命令

了解系统的基本信息，包括**操作系统版本、硬件配置、内核信息、系统负载**等。

- **操作系统和版本信息**
  - **`uname`**：显示系统信息。
  - `uname -a``-a`：显示所有信息，包括内核版本、主机名等。
- **`lsb_release`**：查看 Linux 发行版的详细信息（适用于支持 LSB 的系统）。
  - `lsb_release -a`：显示所有信息，包括发行版名、版本等。
- **`cat /etc/os-release`**：查看操作系统的基本信息。
- **`hostnamectl`**：显示主机名、操作系统版本、内核等信息。

#### 内核信息
- **`uname -r`**：显示当前内核版本。
- **`cat /proc/version`**：显示内核版本、gcc 版本等。
- **`dmesg`**：查看内核和启动时的日志信息。

#### 硬件信息
- **`lscpu`**：显示 CPU 相关的信息。
- **`lsblk`**：显示块设备的信息，通常用于查看硬盘分区。
- **`lspci`**：显示 PCI 总线上的硬件设备信息（适用于 PCI 设备）。
- **`lsusb`**：列出所有 USB 设备。
- **`free -h`**：查看内存的使用情况。
- **`dmidecode`**：获取系统硬件信息（如主板、内存等）。

#### 系统运行时间和负载
- **`uptime`**：显示系统的运行时间、负载信息和登录用户数。
- **`top`**：显示系统运行情况和当前的进程状态。
- **`htop`**：增强版 `top`，支持更多交互操作，显示系统信息和进程信息。
- **`w`**：显示当前登录的用户和他们正在做什么。

#### 硬盘信息
- **`df -h`**：显示文件系统的磁盘空间使用情况。
- **`du -sh /path/to/dir`**：显示指定目录的磁盘空间使用情况。
---

### 查看 Linux 主机资源关信息

监控和查看 Linux 系统的资源使用情况，包括 ***CPU、内存、磁盘 I/O***等。

#### CPU 资源使用情况
- **`top`**：显示 CPU 使用率、内存使用情况、进程信息等。
- **`mpstat`**：显示 CPU 的多核利用率。
- **`sar`**：收集、报告、保存系统活动信息，适用于历史数据查看。
- **`iostat`**：显示 CPU 和 I/O 设备的使用情况。
- **`pidstat`**：显示特定进程的 CPU 使用情况。


#### 内存使用情况
- **`free -h`**：查看内存的使用情况（包括交换空间）。
- **`vmstat`**：查看内存、进程、I/O、系统、CPU 等资源的使用情况。
- **`ps aux`**：查看所有进程的内存和 CPU 使用情况。
- **`top`**：查看内存和交换空间的实时使用情况。

#### 磁盘使用情况
- **`df -h`**：显示文件系统的磁盘空间使用情况。
- **`du -sh /path/to/dir`**：显示指定目录的磁盘空间使用情况。
- **`iostat -x 1`**：查看磁盘 I/O 性能。
- **`iotop`**：实时显示进程的磁盘 I/O 使用情况（需要 root 权限）。

#### 网络使用情况
- **`netstat -tulnp`**：查看所有正在监听的端口及其对应的进程。
- **`ss`**：替代 `netstat`，用于显示更详细的网络连接信息。
- **`iftop`**：实时显示网络流量。
- **`nload`**：实时显示网络带宽的使用情况。
- **`ping`**：测试网络连接是否正常。
- **`traceroute`**：查看数据包到达目标主机的路径。

#### 系统负载
- **`uptime`**：查看系统的负载、运行时间等。
- **`w`**：查看系统的负载和当前登录用户。
- **`load`**：查看系统负载平均值（1 分钟、5 分钟、15 分钟的平均负载）。

---

#### 总结

- **系统信息命令** 主要帮助你了解操作系统、内核、硬件等的基本信息。
- **资源管理命令** 帮助你监控系统资源的使用情况，包括 CPU、内存、磁盘、网络等。
  

## 软件安装
在 Linux 系统中，软件安装是一个重要的管理任务，主要涉及 **RPM**、**SRPM** 和 **YUM** 这三种包管理工具。下面我们详细介绍它们的功能及其使用方法。

---

### RPM（Red Hat Package Manager） 
RPM（Red Hat Package Manager）是一种用于**管理二进制软件包**的工具，最早由 Red Hat 开发，并成为许多 Linux 发行版（如 RHEL、CentOS、Fedora）中的标准软件包管理工具。

#### RPM 主要功能  
- **安装** (`rpm -ivh package.rpm`)
- **升级** (`rpm -Uvh package.rpm`)
- **卸载** (`rpm -e package`)
- **查询** (`rpm -q package`)
- **验证** (`rpm -V package`)
- **列出已安装的软件** (`rpm -qa`)

#### RPM 命令详解
- **安装 RPM 软件包** `rpm -ivh package.rpm`
  - `-i`（install）：安装
  - `-v`（verbose）：详细模式
  - `-h`（hash）：显示进度条

- **升级 RPM 软件包** `rpm -Uvh package.rpm`
  - `-U`（upgrade）：升级（如果软件未安装，则进行安装）

- **删除 RPM 软件包** `rpm -e package_name`
  - `-e`（erase）：删除软件

- **查询已安装的软件** `rpm -q package_name`
  - `-q`（query）：查询软件包是否安装

- **列出所有已安装的软件** `rpm -qa`
  - `-a`（all）：列出所有已安装的软件包

- **检查软件包是否被修改** `rpm -V package_name`
  - `-V`（verify）：验证软件包的完整性

- **查询 RPM 包的信息** `rpm -qi package_name`
  - `-i`（info）：显示软件包详细信息

- **查询 RPM 包包含的文件** `rpm -ql package_name`
  - `-l`（list）：列出软件包中的文件


###  SRPM（Source RPM） 
SRPM（Source RPM）是**源代码格式的 RPM 包**，通常用于构建二进制 RPM 包，适用于开发者和高级用户。

#### SRPM 主要功能 
- **查看 SRPM 里面的文件** `rpm -qpl package.src.rpm`

- **安装 SRPM** `rpm -ivh package.src.rpm`
  - 这不会直接安装软件，而是会解压源码文件到 `/usr/src/redhat/SOURCES/`（旧版路径）或 `/usr/src/packages/`（新版路径）。

- **编译 SRPM** `rpmbuild --rebuild package.src.rpm`
  - 生成 `.rpm` 二进制文件。


---

### YUM（Yellowdog Updater, Modified） 
YUM 是基于 RPM 的包管理工具，支持**自动依赖解析**和**在线仓库管理**，是 Red Hat、CentOS 和 Fedora 等发行版的默认软件管理工具。

#### YUM 主要功能 
- **在线安装、更新、删除软件**
- **自动解决软件包依赖**
- **支持远程和本地 RPM 仓库**

#### YUM 命令详解 
- **安装软件** `yum install package_name`

- **更新软件** `yum update package_name`

- **删除软件** `yum remove package_name`

- **搜索软件** `yum search keyword`

- **查看软件详细信息** `yum info package_name`

- **列出所有可用的软件包** `yum list`

- **清理 YUM 缓存** `yum clean all`


#### YUM 仓库管理 
YUM 的软件源配置文件位于 `/etc/yum.repos.d/` 目录下，你可以手动编辑 `.repo` 文件，或者使用 `yum-config-manager` 来管理仓库。

**添加一个新的 YUM 源：**
```bash
vi /etc/yum.repos.d/custom.repo
```
内容示例：
```
[custom]
name=Custom Repository
baseurl=http://mirror.example.com/custom
enabled=1
gpgcheck=0
```

**启用/禁用特定仓库：**
```bash
yum-config-manager --enable repository_name
yum-config-manager --disable repository_name
```

---

### RPM vs. YUM 的区别 
| 功能 | RPM | YUM |
|------|-----|-----|
| 依赖管理 | 手动安装依赖 | 自动解析依赖 |
| 安装方式 | 只能安装本地 `.rpm` | 可从远程仓库安装 |
| 更新方式 | 需手动下载并安装 | 自动检查并更新 |

---

**总结**
- **RPM** 适用于安装本地 `.rpm` 文件，但不会自动解决依赖问题。
- **SRPM** 适用于从源码构建 RPM 包，适合开发者和自定义构建。
- **YUM** 通过在线仓库自动解决依赖问题，是日常安装和更新软件的最佳选择。

---

### 软件安装Ubuntu对应
在 **Ubuntu** 及其他基于 **Debian** 的 Linux 发行版中，软件管理主要依赖 **dpkg、APT（Advanced Package Tool）和 Snap**，它们对应于 **Red Hat 系的 RPM 和 YUM**，但有一些不同之处。   

---

#### RPM vs. dpkg 
| 特性 | Red Hat 系（CentOS、Fedora） | Debian 系（Ubuntu、Debian） |
|------|----------------------------|-----------------------------|
| **基础包管理工具** | `rpm` | `dpkg` |
| **包格式** | `.rpm` | `.deb` |
| **是否支持依赖管理** | ❌ 不会自动解决依赖 | ❌ 不会自动解决依赖 |
| **主要作用** | 手动安装、卸载、查询 RPM 包 | 手动安装、卸载、查询 DEB 包 |

- **RPM** 是 Red Hat 系的包管理工具，对应 **Ubuntu** 中的 **dpkg**。  
- `rpm -i package.rpm` **≈** `dpkg -i package.deb`  
- 但是 **rpm 和 dpkg 都不会自动解决依赖**，如果缺少依赖，就要手动下载相关的软件包并安装。

---

#### YUM vs. APT（更常用！）
| 特性 | Red Hat 系（CentOS、Fedora） | Debian 系（Ubuntu、Debian） |
|------|----------------------------|-----------------------------|
| **高级包管理工具** | `yum` 或 `dnf`（新版） | `apt` 或 `apt-get` |
| **是否支持依赖管理** | ✅ 自动解决依赖 | ✅ 自动解决依赖 |
| **是否支持在线安装** | ✅ 是 | ✅ 是 |
| **主要作用** | 在线下载、安装、更新 RPM 软件包 | 在线下载、安装、更新 DEB 软件包 |

- **APT（Advanced Package Tool）** 对应于 **YUM**，用于自动解决依赖、安装和管理软件。  
- `yum install package` **≈** `apt install package`  
- `yum remove package` **≈** `apt remove package`  
- `yum update` **≈** `apt update && apt upgrade`  

👉 **APT 是 Ubuntu 中最常用的包管理工具！** 🚀  

---

#### SRPM vs. 源代码包（.dsc + .tar.gz） 
| 特性 | Red Hat 系（CentOS、Fedora） | Debian 系（Ubuntu、Debian） |
|------|----------------------------|-----------------------------|
| **源码包管理** | `.src.rpm`（SRPM） | `.dsc` + `.tar.gz` |
| **编译命令** | `rpmbuild` | `dpkg-buildpackage` |
| **是否可修改源码** | ✅ 是 | ✅ 是 |
| **主要作用** | 重新编译、优化 RPM 包 | 重新编译、优化 DEB 包 |

- **SRPM**（Source RPM）允许开发者修改源码并重新编译 RPM。  
- **Ubuntu** 里类似的做法是下载 `.dsc` 文件和 `.tar.gz` 源码，然后用 `dpkg-buildpackage` 进行编译。  

---

#### 额外：Snap（Ubuntu 特有） 
| 特性 | 传统包管理（APT、dpkg） | Snap（Ubuntu 自带） |
|------|------------------------|---------------------|
| **安装方式** | `.deb` 格式，需要 APT 解决依赖 | `.snap` 格式，**自带依赖** |
| **是否自动更新** | ❌ 需要手动升级 | ✅ **自动更新** |
| **是否可以跨 Linux 发行版** | ❌ 仅限 Debian/Ubuntu | ✅ 可以跨发行版（如 Arch、Fedora） |

- **Snap 是 Ubuntu 独有的包管理系统**，它的主要特点是：
  - **独立于 APT**，不受 `dpkg` 影响。  
  - **自带所有依赖**，不会出现“依赖地狱”问题。  
  - **自动更新**，不像 APT 需要手动 `apt upgrade`。  
  - **可以跨发行版使用**，不像 APT 只能用于 Debian 系。  

👉 但 Snap **体积较大**，因为每个包都带上了所有依赖，所以 **服务器环境更常用 APT**，而 **桌面环境（如 Ubuntu 桌面版）更喜欢 Snap**。  

---

### apt 相关配置文件
在 **Ubuntu**（以及 Debian 系统）中，`apt` 主要依赖以下配置文件进行管理：

---
**1️⃣ APT 相关的配置文件**
| 配置文件 | 作用 |
|---------|------|
| `/etc/apt/sources.list` | **APT 软件源列表**（决定软件的下载地址） |
| `/etc/apt/apt.conf` | **APT 全局配置文件**（如代理、缓存、安装方式等） |
| `/etc/apt/apt.conf.d/` | **APT 额外配置文件目录**（APT 运行时的具体行为） |
| `/etc/apt/preferences` | **APT 软件包优先级**（设置 PPA 或不同版本的软件安装优先级） |
| `/etc/apt/preferences.d/` | **APT 额外优先级配置**（用于管理多个仓库的软件版本） |
| `/var/lib/apt/lists/` | **APT 已下载的软件包列表**（存储已获取的仓库元数据） |
| `/var/cache/apt/archives/` | **APT 下载的软件包缓存**（存储已下载的 `.deb` 文件） |

---

**2️⃣ `/etc/apt/sources.list`（APT 源配置文件）**
该文件列出了 Ubuntu 使用的软件仓库地址，每一行代表一个软件源。例如：
```plaintext
deb http://archive.ubuntu.com/ubuntu focal main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu focal-updates main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu focal-security main restricted universe multiverse
```

| 关键字 | 说明 |
|--------|------|
| `deb` | **二进制软件包源**（用于安装 `.deb` 软件包） |
| `deb-src` | **源码软件包源**（用于获取 `.dsc` + `.tar.gz` 源代码） |
| `main` | **官方支持的免费软件** |
| `restricted` | **受限软件（官方维护，但部分闭源）** |
| `universe` | **社区维护的开源软件** |
| `multiverse` | **非自由软件（专有软件，如 Flash、驱动）** |

👉 **如果要使用第三方 PPA（个人软件源），通常会添加到 `/etc/apt/sources.list.d/` 目录！**

---

**3️⃣ `/etc/apt/apt.conf`（APT 配置文件）**

该文件用于控制 **APT 的全局行为**，例如代理、缓存、安装策略等。

**常见的 APT 配置选项**
```plaintext
// 启用 HTTP 代理
Acquire::http::Proxy "http://proxy.example.com:8080";

// 禁用安装过程中提示用户输入
DPkg::Options {
   "--force-confdef";
   "--force-confold";
};

// 设置软件包安装时的日志记录
APT::Get::Show-Upgraded "true";

// 启用自动清理无用的包
APT::Periodic::AutocleanInterval "7";
```
**要修改 APT 代理，通常会修改这里！**

---

**4️⃣ `/etc/apt/apt.conf.d/`（APT 额外配置目录）**
这个目录存放多个配置文件，每个文件控制 APT 的不同行为。例如：

- `/etc/apt/apt.conf.d/01autoremove` → 配置自动删除无用的软件
- `/etc/apt/apt.conf.d/70debconf` → 配置 `debconf` 交互方式
- `/etc/apt/apt.conf.d/80http` → 配置 HTTP 代理

示例（`/etc/apt/apt.conf.d/80proxy`）：
```plaintext
Acquire::http::Proxy "http://proxy.example.com:8080";
Acquire::https::Proxy "http://proxy.example.com:8080";
```

**这个目录下的文件通常比 `/etc/apt/apt.conf` 优先级更高！**

---

**5️⃣ `/etc/apt/preferences` 和 `/etc/apt/preferences.d/`（APT 软件包优先级）**

APT 允许你指定不同的软件版本优先级。例如，如果你想让 **APT 安装特定版本的软件**，可以这样写：

```plaintext
Package: vim
Pin: version 8.2.1-0ubuntu1
Pin-Priority: 1001
```

| 配置项 | 说明 |
|--------|------|
| `Package:` | **指定软件包** |
| `Pin:` | **指定软件包版本** |
| `Pin-Priority:` | **优先级**（数值越大，优先级越高） |

**优先级规则：**
- `1001` → **强制安装** 指定版本
- `990` → **优先选择** 指定版本
- `500` → **默认值**
- `<100` → 只会安装，如果没有其他可用版本

👉 **如果你安装了多个版本的软件，但希望锁定某个版本，可以修改这里！**

---

**6️⃣ `/var/lib/apt/lists/`（APT 的缓存信息）**
- 这个目录存储了 APT **从服务器下载的索引文件**，包括所有软件包的信息。
- 当你运行 `apt update` 时，APT **会从源服务器拉取最新的软件包列表并存储到这里**。
- 你可以用 `ls /var/lib/apt/lists/` 查看：

```bash
ls /var/lib/apt/lists/
```

**如果 APT 运行异常（如找不到包），可以尝试 `sudo rm -rf /var/lib/apt/lists/* && sudo apt update` 来清除缓存！**

---

**7️⃣ `/var/cache/apt/archives/`（APT 的软件包缓存）**
- 这个目录存放已经下载的 `.deb` 文件（安装包）。
- 例如，`apt install vim` 之后，APT **会将 `vim.deb` 存在这里**，以便以后可以离线安装。
- 如果你要清理旧的软件包，可以运行：

```bash
sudo apt clean
```

**如果磁盘空间不足，可以尝试 `apt clean` 或 `apt autoclean`！**

---

**🔹 总结**
| 目录 / 文件 | 作用 |
|-------------|------|
| `/etc/apt/sources.list` | APT **软件源配置**（决定从哪里下载软件） |
| `/etc/apt/apt.conf` | APT **全局配置**（如代理、缓存策略） |
| `/etc/apt/apt.conf.d/` | 额外的 APT 配置（分模块管理） |
| `/etc/apt/preferences` | APT **软件包优先级管理** |
| `/var/lib/apt/lists/` | APT **已下载的软件包列表** |
| `/var/cache/apt/archives/` | APT **缓存的 `.deb` 安装包** |

**在 Ubuntu 下，如果你遇到软件安装问题，首先检查 `/etc/apt/sources.list` 是否正确，然后运行 `sudo apt update` 更新软件包列表！** 


### 常用命令
#### apt command
`apt [options] [command] [package ...]`
- `sudo apt update` 列出所有可更新的软件清单
  - `sudo apt update <package_name>` 更新指定软件
- `sudo apt upgrade` 升级软件包
  - `sudo apt full-upgrade` 升级软件包之前先删除需要更新软件包
- `sudo apt install <package_name>` 安装指定软件
  - `sudo apt install <package_name1> <package_name2> <package_name3>` 安装多个软件
  - `sudo apt reinstall <package_name>` 重新安装
- `sudo apt show <package_name>` 显示软件包具体信息,例如：版本号，安装大小，依赖关系等等
- `sudo apt remove <package_name` 删除软件包
  - `sudo apt autoremove` 清理不再使用的依赖和库文件
  - `sudo apt purge <package_name>` 移除软件包及配置文件
- `sudo apt search <keyword>` 查找软件包
- `apt list` 
  - `apt list --upgradable` 列出可更新软件包及版本信息
  - `apt list --installed` 列出所有已安装的包
  - `apt list --all-versions` 列出所有已安装的包的版本信息

#### yum command
[Linux yum 命令](https://www.runoob.com/linux/linux-yum.html)


### 总结  
- **RPM** 是 Linux 上的标准软件包管理工具，它管理所有的 RPM 软件包。许多软件包在发行版安装时就已经包含在系统里。  
- **SRPM** 是 RPM 软件包的源码版本，适用于需要自定义编译或修改源码的情况。  
- **安装 RPM 时**，系统会检查本地是否满足依赖项，如果缺失则会报错，要求手动安装依赖。  
- **YUM 是 RPM 的在线依赖解决方案**，它会自动检查并从远程仓库下载所需的依赖项，省去了手动下载安装的麻烦。  

***总结***：

✅ **RPM：只能手动安装、卸载、升级，需要手动解决依赖问题。**  
✅ **SRPM：源码包，需要手动编译。**  
✅ **YUM：自动管理依赖，可以从在线仓库安装软件，推荐使用。**  

  
**RPM** → 手动安装，可能缺依赖，需要自己找补。  
**YUM** → 在线安装，自动解决依赖，一键搞定。  

既然 **YUM** 解决了 RPM 依赖问题，为什么还要 **RPM** 呢？其实，RPM 依然有重要的用途，原因主要包括以下几点：  

1️⃣ **离线安装场景**  
- YUM 依赖网络，如果服务器无法联网（比如在**生产环境、内网环境**下），就无法直接使用 YUM。  
- 这时候，你可以手动下载 RPM 包及其依赖，然后使用 `rpm -ivh` 命令安装。  

2️⃣ **自定义版本**  
- YUM 默认从官方仓库下载软件，而有时你可能需要**特定版本的软件**，但官方仓库没有。  
- 这时候，你可以下载所需版本的 RPM 包，并手动安装，避免被 YUM 自动升级或替换掉。  

3️⃣ **企业环境 & 服务器管理**  
- 企业内部可能搭建了**私有 RPM 仓库**，不会使用外部 YUM 源，管理员会提供 RPM 包供安装。  
- 某些**安全策略严格的服务器**，可能不允许直接用 YUM 自动安装未知的软件，而是要求手动审核 RPM 包后安装。  

4️⃣ **SRPM 适用于源码编译和优化**  
- SRPM（源码 RPM）允许开发者修改源码、优化软件，然后重新编译成适合自己环境的 RPM 包。  
- 例如，你可能需要针对 **特定 CPU 架构**（如 ARM、AMD）优化某个软件，YUM 直接安装的标准 RPM 可能不能满足需求。  

5️⃣ **YUM 本身也是基于 RPM**  
- YUM 只是一个高级的 **包管理工具**，它的底层依赖 RPM！  
- 你可以理解为：**YUM = 自动化的 RPM**，YUM 只是让 RPM 更方便了，但 RPM 依然是 Linux 的基础包管理工具。  

---

**什么时候用 YUM，什么时候用 RPM？**  

| **使用场景** | **使用 RPM** | **使用 YUM** |  
|------------|------------|------------|  
| 服务器无法联网 | ✅ | ❌ |  
| 安装特定版本软件 | ✅ | ❌（YUM 只能装官方库里的版本） |  
| 手动管理软件 | ✅ | ❌ |  
| 自动解决依赖 | ❌（需要手动找依赖） | ✅ |  
| 需要源码编译（SRPM） | ✅ | ❌ |  
| 方便快捷安装软件 | ❌ | ✅ |  

日常用 **YUM**，但在 **离线、特定版本、源码编译、严格管理** 等场景下，仍然需要 **RPM**。  


---

| 功能 | Red Hat（CentOS、Fedora） | Ubuntu（Debian 系） |
|------|----------------------------|---------------------|
| **手动安装单个包** | `rpm -i package.rpm` | `dpkg -i package.deb` |
| **安装并自动解决依赖** | `yum install package` | `apt install package` |
| **卸载软件** | `yum remove package` | `apt remove package` |
| **更新系统** | `yum update` | `apt update && apt upgrade` |
| **源码包管理** | `rpmbuild` | `dpkg-buildpackage` |
| **额外的包管理** | ❌ | `snap install package` |

👉 **在 Ubuntu 上，通常你会用 `apt install package`，如果需要更现代的解决方案，可以用 `snap install package`。但如果你下载了一个 `.deb` 文件，就要用 `dpkg -i package.deb` 手动安装！** 🚀  


## systemctl command detail

语法： ***`systemctl COMMAND name.service`***
用途： 用于控制 systemed系统和服务，***systemed是Linux中用于 初始化系统组件、管理系统进程的 daemon守护进程和服务管理器***

<div style="text-align:center">
    <img src="/tools3_Linux/pic_source/systemed命令.png" alt="systemed命令" style="margin-bottom: 1px;">
    <p>systemed命令</p>
</div>

systemed系统重，服务 service 通常指后台运行的进程，可以是系统服务如网络管理、日志记录、硬件管理等，也可以是用户服务，如web服务、数据库服务等

- 服务： systemed管理的实体，定义了如何启动和管理一个或多个进程
- 进程： os系统执行程序的一个实例


***systemctl list-units***
- `--type=`列出指定类型的单元
  - `systemctl list-units` 默认列出所有服务单元（`.device, .mount, .service, .slice, .target, timer`）
  - `systemctl list-units --type=service`
- `--state=` 列出指定状态的单元
  - `systemctl list-units --state=running`
  - `systemctl list-units --state=running --type=service`


## curl command
- `curl [options] [URL]` 是一个用于传输数据的命令行工具。***常用于测试和调试网络服务，或在命令行中与 Web API 进行交互***
  - `-g` 使用 GET 方法（默认方法） `curl -a https://www.xxx.com`
  - `-d` 发送 POST 数据 `curl -d "param1=value1&param2=value2..." http://www.xxx.com`


## Linux 磁盘管理
[Linux 磁盘管理](https://www.runoob.com/linux/linux-filesystem.html)

# Shell 教程
[shell 编程](https://www.runoob.com/w3cnote/shell-scripting.html)


```bash
#!/bin/bash
echo "hello Sijorhou!"
```
- `#!` 告诉系统使用什么 interpreter 来执行此脚本
  - `/bin/bash` 是要使用的脚本解释器
- `chmod +x ./test.sh`, `./test.sh` 先后用于赋予脚本执行权限，执行脚本
- `sh test.sh` 直接执行脚本

***echo***
echo 命令可以用于显示简单的消息，也可以用来执行变量替换和打印变量的值

- `echo "hello, sijorhou"` 打印字符串
- `echo $variable_name` 打印变量值
- `echo "${my_val}PATH"` 双引号字符串支持变量
- `echo -e "\n \t"`  `-e`双引号字符创支持转移序列
- 

***注释***
`#` 单行注释
`:' ... '` 多行注释
```bash
# 单行注释

:' 这里
可以编辑
多行注释'
```
***长命令续行***
`\` 使用 反斜杠，如下：
```bash
#!/bin/bash

# 定义一个包含所有要卸载的软件包名称的数组
packages=(docker docker-client docker-client-latest docker-common docker-latest      docker-latest-logrotate docker-logrotate docker-engine)

# 使用 for 循环遍历数组并卸载每个软件包
for pkg in "${packages[@]}"; do
    sudo yum remove -y "$pkg"
done

# 或者如下：
sudo yum remove docker \
docker-client \
docker-client-latest \
docker-common \
docker-latest \
docker-latest-logrotate \
docker-logrotate \
docker-engine
```

## Shell 变量
***变量***
- 变量名： 用于存储数据值，不加$, 名称与等号之间无空格，数字字母下划线，不能以数字开头
  - `your_name="sijorhou"`
- 使用变量： 使用一个定义的变量，再起前面加 $ 即可（{可选}）
  - `echo $your_name` `echo ${your_name}` 会打印出对应变量值
- 只读变量：将变量定义为只能读取不可修改的变量
  - `readonly variable_name`
- 删除变量： 删除后的变量不能再次使用，不能删除只读变量
  - `unset variable_name`
- 环境变量：
  - `echo $PATH`
- 变量类型：
  - `my_string='Hello, sijorhou!'` 字符串
  - `declare / typeset` 声明一个变量，大多情况可互换
    - `declare int_val=10` 声明初始化一个整型变量
    - `declare -x variable_name` 将变量导出为环境变量
    - `declare -r variable_name=value` 将变量设置为只读变量
    - `declare -i int_var`
    - `declare -f float_var`
    - `declare -a array_name` 声明一个数组

***字符串***

- 字符串：
  - `str='this a string'` 单引号字符串，原样输出所有字符串，其中变量无效
  - `your_name="sijorhou"` 双引号字符串，可以有变量、转义字符
  - 字符串拼接
  - `echo ${#str} / echo ${#str[0]}` 两者等价，获取字符串长度，即元素个数
  - `echo ${str:1:4}` 从字符串第 2 个字符开始截取 4 个字符

```bash
# 单引号字符串
single_quot='sijorhou'

# 双引号字符串 echo 输出： hello! I know you're "sijorhou"!
your_name="sijorhou"
str="hello! I know you're \"$your_name\"! \n"
echo -e $str


# 单引号字符串拼接
:'
  greeting_1 输出结果： hello, sijorhou !
  greeting_2 输出结果： hello, ${your_name} !
'
greeting_1='hello, '$your_name' !'
greeting_2='hello, ${your_name} !'
echo $greeting_1  $greeting_2

# 双引号拼接
:'
  greeting_3 输出结果： hello, sijorhou !
  greeting_4 输出结果： hello, sijorhou !
'
greeting_3="hello, "$your_name" !"
greeting_4="helllo, ${your_name} !"
echo $greeting_3  $greeting_4
```

***数组***

- 数组
  - `declare -a array_name` 声明一个数组
  - `my_array=(1 2 3 4 5)` 定义一个简单数组
  - `array_name["name"]="sijorhou"` 向数组中添加键值对元素
  - `${array_name[key]}` 访问数组元素
  - `echo ${array_name[@]}` `@` 用于获取所有元素
  - `length=${#array_name[@]}` , `length=${#array_name[*]}` 获取数组元素个数
  - `len_elem=${#array_name[n]}` 获取数组单个元素的长度

```bash
#!/bin/sh

declare -a name_array
declare -a int_array

```

# Linux 命令
## 6. 网络通讯
### ifconfig




