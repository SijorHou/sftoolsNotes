## 查看命令使用方法
- `man command` 查看 command的手册页
- `info command` 没有手册页可以查看 info页
- `command --help` 显示command的基本用法和选项
- `cd ..` 返回上一级目录
  
  <div style="text-align:center">
    <img src="/tools3_Linux/pic_source/返回上级目录.png" alt="返回上级目录" style="margin-bottom: 1px;">
    <p>返回上级目录</p>
</div>


## 文件基本属性
[文档基本属性]((https://www.runoob.com/linux/linux-file-attr-permission.html))

- `ls -l` 长格式显示文件属性信息，列出当前目录中的偶有文件目录

### 更改文件属组、属主

- `chgrp [-R] new_group file` 将 file的 属组修改为 new_group。[] 是可选项，-R 表递归地修改 file中内容的对应属性
- `chown [-R] new_owner file` 将 file的 属主修改为 new_owner
- `chown [-R] new_owner:new_group file` 同时修改

<div style="text-align:center">
    <img src="/tools3_Linux/pic_source/文件属组属主更改.png" height=60% width=60% alt="文件属组属主更改" style="margin-bottom: 1px;">
    <p>文件属组属主更改</p>
</div>

### 更改文件权限属性
- `chmod [-R] xyz file_or_dir`

Linux文件属性有两种设置方法，一种是数字，一种是符号。

**Linux 文件的基本权限就有九个**，分别是 owner/group/others(拥有者/组/其他) 三种身份各有自己的 read/write/execute 权限

***rwxrwx---***  
- 分别代表 owner(rwx)group(rwx)other(---)
- 其中 r:4、w:2、x:1 为各自的分数
- rwxrwx---代表 770，即（rwx = 4 + 2 = 1 = 7）, - 则为0
- 所以，以数字的方式修改权限： `chmod 754 xxx.txt/dir` 即为 修改属性权限为 `-rwxr-xr-- `

***符号类型修改权限***
- user、group、others可以用 u、g、o 代替。（a 为 all）
- 读写权限可以写成 r、w、x
- 例：`chmod 754 xxx.txt/dir` 相当于 `chmod u=rws,g=rx,o=r xxx.txt/dir`



## 文件与目录管理
[文件与目录管理]((https://www.runoob.com/linux/linux-file-content-manage.html)
)


### 常用处理命令
- `pwd [-P]` (print work directory) 显示当前所在目录(`-P` 显示真实目录，而不是链接的目录)
- `ls` (list files) 列出目录及文件
- `cd` (change directory) 切换目录
- `mkdir [-mp]`
  - `mkdir -p xx/xx/` 参数`-p`可以递归创建多层目录
  - `mkdir -m 777 newdir` 参数`-m`可以在创建目录时候设置权限
- `rmdir [-p]` 
  - 删除（递归）目录
  - 先递归到最深删除该层目录，然后一层层返回上级父目录，若为空则删除，否则不删除
- `cp [-adflipusr]` 拷贝文件或目录
  - `cp [-adflipusr] source_file target_dir`
  - `cp [option] src1, src2, src3, ..., dir`
- `rm [-fir]` 移除文件或目录
  - `rm -rf xxx` 强制递归全部删除（慎用）
- `mv`
  - `mv [-fiu] source_file target_dir`
  - `mv [options] src1, src2, src3, ..., dir `

### Linux 文件查看命令
- `cat [-AbnvET] file`
  - `-A` 整合了 `vET` 的选项，列出特殊字符而不只是空白
  - `-b -n` 都是显示行号
- `tac file` 从最后一行开始，倒着显示每行内容
- `nl file` 显示行号，但是有更丰富的行号显示的设置选项
- `head/taiil -n number file` 显示文件的前/后几行
- `more, less [option] file` 文件显示


## Linux 用户和用户组管理
[Linux 用户和用户组管理](https://www.runoob.com/linux/linux-user-manage.html)

### Linux 用户账号管理

***账号管理***
- `useradd [option] username` 添加用户账号
  - `-c -d -g -s` 分别是： 指定一段注释性描述、指定创建目录、指定用户所属的组、指定用户登录的shell
  - PS：在指定目录常见用户时，如 `useradd –d  /home/sam -m sam` sam 是用户 sam 的主目录
  - 如果主目录名字和用户名不同，如何查看现有用户？
    - `cat /etc/passwd` 查看最后面的行，显示现有用户信息

- `userdel [option] username` 删除用户
  - `-r` 连通主目录一起删除
- `usermod [option] username` 修改用户相关属性
  - 如 `usermod -s /bin/ksh -d /home/z –g developer`
  - 此命令将用户sam的登录Shell修改为ksh，主目录改为/home/z，用户组改为developer

***密码口令管理 `passwd`***
- `passwd [option] username` 超级用户可以为自己和其他用户设置 口令，但是普通用户只能为自己设置
- `passwd` 用户为自己设置口令
- `passwd [-ludf] username` 
  - `-l, -u` 分别是锁定用户（无法登录） 、解锁用户
  - `-d` 移除用户口令

### Linux 用户属组管理
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

***批量添加用户***
...

## Linux 磁盘管理
[Linux 磁盘管理](https://www.runoob.com/linux/linux-filesystem.html)


## vim的使用
[vim使用](https://www.runoob.com/linux/linux-vim.html)

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






