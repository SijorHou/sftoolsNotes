## MySQL
### Reference

- [菜鸟教程](https://www.runoob.com/mysql/mysql-connection.html)
- [MySQL安装教程](https://blog.csdn.net/weixin_47406082/article/details/131867849?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522171647672116800225532250%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=171647672116800225532250&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~top_positive~default-2-131867849-null-null.142^v100^pc_search_result_base8&utm_term=MySQL%E5%AE%89%E8%A3%85&spm=1018.2226.3001.4187)
- [navicat安装教程](https://blog.csdn.net/weixin_50670076/article/details/136350060?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522171657178116800182137881%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=171657178116800182137881&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~top_positive~default-1-136350060-null-null.142^v100^pc_search_result_base8&utm_term=navicat&spm=1018.2226.3001.4187)
- [navicat使用教程](https://blog.csdn.net/qq_45069279/article/details/105919312?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522171657178116800182137881%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=171657178116800182137881&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~top_positive~default-2-105919312-null-null.142^v100^pc_search_result_base8&utm_term=navicat&spm=1018.2226.3001.4187)
- [卸载教程](https://blog.csdn.net/m0_52861000/article/details/131354710?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522172110015316800180631045%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=172110015316800180631045&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~top_positive~default-2-131354710-null-null.142^v100^pc_search_result_base8&utm_term=%E5%8D%B8%E8%BD%BDmysql&spm=1018.2226.3001.4187)
### 数据库基础

- DBMS(Data Base Manage System) 数据库软件管理系统，是软件系统，如 MySQL等各类我们常称的“数据库”
- DBMS 存放的文件成为 “表（table）”， 结构化的文件，存储某种特定类型的数据
  - DBMS(MySQL) 中可以有多个 "库（library）"，每个库中会有多个 "表（table）"
- MySQL：开源DBMS，执行快，已安装，易使用
- client-server 软件：DBMS分为两类，一类是 共享文件系统的DBMS；一类则是客服-服务器软件，开发中的是后者
- ***模式（schema）***，在数据库中非常重要的概念，有不同含义：
  - 模式schema：指的是 数据库的结构设计，包括 tables、views、indexs、store procedures、triggers、constraints等。***schema 描述了数据的组织方式***
  - 数据库实例：有时候指的是一个 Database Instance
  - 命名空间： 某些数据库系统中，schema 也可以看做一个 namespace，用于区分不同的用户或组的对象名称
  - 数据字典： 一些数据库系统中，schema 用以存储数据库原数据的 data dictionary
- 列：记录的某个字段/属性
  - 数据类型
- 行：table中数据是按行存储的，一行就是一个 record
- 主键：每一行中可以唯一标识自己的一列/一组列
  - 就是每行的关键字
- SQL：Structured Query Language
- ***关系型数据库*** 就是使用关系模型（表格模型）的数据库，非关系型数据库则使用其他多种类型的数据模型（MongoDB:Document, redis:key-value, Elasticsearch:search-engine, Neo4J:graph...）

***Design rules of RDBMS***
- (relational data base manage system) ***RDBMS的典型数据结构： 数据表（structred）***，数据-->表-->库，一个数据库中可有多个表，每个表唯一（表名标识唯一）
- 表、记录、字段
  - ***E-R(Entity-relationship) 模型中 3 个主要概念： 实体集、属性、联系集***
    - 实体集：数据库中一个表
    - 实体：数据库表中的一行（row、record）
    - 属性：attribute，对应数据库表中的一列/字段（column、field）
  - 表的关联关系：1v1, 1vm, mvm, slef-reference（一对一、多， 多对多， 自我引用）

### MySQL 管理

#### NET commands
- 命令行服务管理
  - 管理员身份打开命令行
  - `NET HELP` 查看 `NET` 命令帮助（小写也可以）
  - `NET START /HELP` 查看指定命令 `NET START` 的帮助信息
    - `NET START` 显示当前开启的服务
      - `NET START | find "MySQL/service_partial_name"`直接查找相关命令
    - `NET START service` 开启服务
    - `NET START "service1 service2"` 开启多个服务需用双引号指示多个名称
    - `NET STOP service` 关闭服务
- 启动 MySQL 服务
  - 查看开启服务，本地MySQL服务全称为 MySQL90
  - `NET START MySQL90` 开启MySQL服务
  - `NET STOP MySSQL90` 关闭MySQL服务

#### mysqladmin commands
- `mysqladmin -u root -p [check_content]` `-u` 是用户，`-p`是密码
- `mysqladmin -u root -p version` 查看完整的数据库主机信息
- `mysqladmin -u root -p status` 显示MySQL服务器的运行装填
- `mysqladmin -u root -p processlist` 显示MySQL服务器中正在运行的进程列表


***MySQL连接***
本地MySQL用户名：root
本地MySQL密码：123456

#### 命令行连接、退出
- `mysql -u [username(root)] -p` 然后键入密码进入 MySQL
  - `mysql -u root -p 123456 -P 3306 -h localhost` 完整连接命令，如果就是在本机的3306端口，后两个可以省略（参考上面 数据库主机信息查看命令）
- `mysql -V/--version`
- `quit/exit` 退出MySQL
- msql命令行实用程序
  - `;` 结束
  - `help` 或 `\h` 获取帮助，如 `help/HELP SELECT;` 、`\h SELECT`
  - `QUIT/quit/EXIT/exit` 退出数据库

#### 数据导入指令
- `source absolute_path_of_src_file.sql`
  - `source D:\xxx.sql`

### MySQL 操作实例
- `SHOW DATABASES;` 
- `CREATE DATABASE [IF NOT EXISTS] db_name;`
- `USE db_name;`
- `CREATE TABLE table_name(id int, name varchar(15));`
- `SHOW TABLES;`
- `SELECT * FROM table_name;`
- `INSERT INTO table_name VALUES(1001, 'sijorhou');`
  - `SHOW CREATE TABLE table_name` 快速显示常见table_name的完整命令和表结构
  - `SHOW VARIABLES LIKE 'character_%';`  用于显示所有以 character 为前缀的系统变量（显示MySQL服务器使用的字符集，如 `character_set_database：默认数据库的字符集`, `character_set_connection：服务器内部使用的客户与服务器之间的通信字符集`）
  - `SHOW VARIABLES LIKE 'collation_%';` 校对（collation）是指字符数据的比较和排序规则，该命令显示所有校对所依赖的字符集，如`collation_database：默认数据库的校对规则`, `collation_connection：客户与服务器之间通信的校对规则`
  - mysql数据库目录下的 `my.ini` 文件中可以修改默认字符集
- `DROP DATABASE db_name;`

创建数据库时，可以同时配置数据库信息
```sql
CREATE DATABASE [IF NOT EXISTS] mydatabase
CHARACTER SET utf8mb4
COLLATE utf8mb4_general_ci
DEFAULT CHARACTER SET utf8mb4
DEFAULT COLLATE utf8mb4_unicode_ci  -- 指定默认的排序规则，这里使用utf8mb4_unicode_ci作为示例
COMMENT = 'My custom database'        -- 为数据库添加注释
ENCRYPTION = 'Y';                    -- 启用加密，适用于MySQL 8.0及以上版本
```


<div style="text-align:center">
    <img src="../pic/mysql密码重置步骤.png" alt="mysql密码重置步骤" style="margin-bottom: 1px;">
    <p>mysql密码重置步骤</p>
</div>

### SQL 语句
#### SELECT
- `SELECT seg(col),... FROM table_name` 以 "SELECT" 为关键字
  - 后跟 列名 （若不是 * 则为查询所有列），也可以写为列的别名 `SELECT seg seg_alias, ...`
  - 空值 NULL 参与运算， 含NULL运算结果仍为NULL
  - 着重号 ``
  - 查询常数
  - `DESC/DESCRIBE`
  - `WHERE`


```sql
-- 1. 基本查询语句
SELECT * FROM employees;
SELECT employee_id, first_name, emai, job_id FROM employees;

-- 2. 列别名
SELECT employee_id emp_id, first_name fst_name, job_id FROM employees;
SELECT employee_id AS emp_id, first_name AS fst_name, job_id FROM employees;
SELECT employee_id "emp_id", first_name "fst_name", job_id FROM employees;
SELECT employee_id "emp_id", first_name "fst_name", salary * 12 "annual salary" FROM employees; 

-- 3. NULL 参与运算（year salary 中，commission_pact 中为NULL的结果均为NULL）
SELECT employee_id, salary "month salary", salary * (1 + commission_pct) * 12 "year salary", commission_pct FROM employees;

-- 4. 着重号 ``，标注表名避免被识别为关键字
SELECT * FROM `order`;

-- 6. 查询常数，用于在查询结果中返回一个常量值，而无需存储在表中
SELECT 'SIJORHOU', '136315', employee_id, last_name FROM employees;

-- 7. 显示表结构，显示表中各个字段详细信息
DESC regions;
DESCRIBE employees;

-- 8. WHERE 过滤数据，WHERE 必须声明在 FROM 后面
SELECT * FROM employees WHERE department_id = 90;
SELECT * FROM employees WHERE last_name = 'King';
```