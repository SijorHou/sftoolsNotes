# Linux 教程



## 文件基本属性
[文档基本属性](https://www.runoob.com/linux/linux-file-attr-permission.html)

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
 

## Linux 磁盘管理
[Linux 磁盘管理](https://www.runoob.com/linux/linux-filesystem.html)


## apt command
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

## yum command
[Linux yum 命令](https://www.runoob.com/linux/linux-yum.html)



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



