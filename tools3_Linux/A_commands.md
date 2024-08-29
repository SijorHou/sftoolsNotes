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