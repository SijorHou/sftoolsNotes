## MySQL 
### Reference

- [菜鸟教程](https://www.runoob.com/mysql/mysql-connection.html)
- [MySQL安装教程](https://blog.csdn.net/weixin_47406082/article/details/131867849?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522171647672116800225532250%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=171647672116800225532250&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~top_positive~default-2-131867849-null-null.142^v100^pc_search_result_base8&utm_term=MySQL%E5%AE%89%E8%A3%85&spm=1018.2226.3001.4187)
- [navicat安装教程](https://blog.csdn.net/weixin_50670076/article/details/136350060?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522171657178116800182137881%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=171657178116800182137881&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~top_positive~default-1-136350060-null-null.142^v100^pc_search_result_base8&utm_term=navicat&spm=1018.2226.3001.4187)
- [navicat使用教程](https://blog.csdn.net/qq_45069279/article/details/105919312?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522171657178116800182137881%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=171657178116800182137881&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~top_positive~default-2-105919312-null-null.142^v100^pc_search_result_base8&utm_term=navicat&spm=1018.2226.3001.4187)
- [卸载教程](https://blog.csdn.net/m0_52861000/article/details/131354710?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522172110015316800180631045%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=172110015316800180631045&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~top_positive~default-2-131354710-null-null.142^v100^pc_search_result_base8&utm_term=%E5%8D%B8%E8%BD%BDmysql&spm=1018.2226.3001.4187)

### MySQL 管理

***启动/关闭 MySQL***
- 命令行服务管理
  - 管理员身份打开命令行
  - `NET HELP` 查看 `NET` 命令帮助
  - `NET START /HELP` 查看指定命令 `NET START` 的帮助信息
    - `NET START` 显示当前开启的服务
    - `NET START service` 开启服务
    - `NET START "service1 service2"` 开启多个服务需用双引号指示多个名称
    - `NET STOP service` 关闭服务
- 启动 MySQL 服务
  - 查看开启服务，本地MySQL服务全称为 MySQL90
  - `NET START MySQL90` 开启MySQL服务
  - `NET STOP MySSQL90` 关闭MySQL服务


### MySQL连接
本地MySQL用户名：root
本地MySQL密码：123456

***命令行连接***
- `mysql -u [username:root] -p` 然后键入密码进入 MySQL

***命令实例***
- `SHOW DATABASES;` 列出所有可用数据库
- `SELECT DATABASE();` 显示当前所在数据库
- `USE db_name;` 选择要使用的数据库
- `SHOW TABLES;` 列出当前数据库中所有可用表
- `QUIT;` 退出数据库

### 增删选数据库

***创建数据库***
- `CREATE DATABASE [IF NOT EXISTS] db_name;` 进入MySQL 创建数据库命令, [IF NOT EXISTS]为可选项，避免数据库已经存在时创建报错

- 指定字符集和排序规则等其他可设置的选项
```sql
CREATE DATABASE mydatabase
CHARACTER SET utf8mb4
COLLATE utf8mb4_general_ci
DEFAULT CHARACTER SET utf8mb4
DEFAULT COLLATE utf8mb4_unicode_ci  -- 指定默认的排序规则，这里使用utf8mb4_unicode_ci作为示例
COMMENT = 'My custom database'        -- 为数据库添加注释
ENCRYPTION = 'Y';                    -- 启用加密，适用于MySQL 8.0及以上版本
```

***删除数据库***
- `DROP DATABASE [IF EXISTS] db_name;` 删除数据库，[IF EXISTS] 可选项，数据库存在才会删除


***选择数据库***
- `mysql -u [username:root] -p -D db_name`  命令行选择数据库（进入MySQL选择数据库命令见前面）

### [MySQL数据类型](https://www.runoob.com/mysql/mysql-data-types.html)

MySQL支持多种类型，大致三类：数值、日期/时间、字符串类型

