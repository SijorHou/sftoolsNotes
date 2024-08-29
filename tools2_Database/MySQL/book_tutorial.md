## MySQL 必知必会

### 1. 数据库基础

- DBMS(Data Base Manage System) 数据库软件管理系统，是软件系统，如 MySQL等各类我们常称的“数据库”
- DBMS 存放的文件成为 “表（table）”， 结构化的文件，存储某种特定类型的数据
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

### MySQL 简介

- MySQL：开源DBMS，执行快，已安装，易使用
- client-server 软件：DBMS分为两类，一类是 共享文件系统的DBMS；一类则是客服-服务器软件，开发中的是后者

***MySQL工具***

- msql命令行实用程序
  - `;` 结束
  - `help` 或 `\h` 获取帮助，如 `help/HELP SELECT;` 、`\h SELECT`
  - `QUIT/quit/EXIT/exit` 退出数据库

### 使用 MySQL

和任何 DBMS 一样，在执行命令之前需要先登录。MySQL 在内部保存自己的用户列表，并把每个用户与各种权限关联起来。

- `USE db_name;` 选择数据库，返回 `Database changed` 表明选择成功
- `SHOW DATABASES;` 
  - `SHOW COLUNMS FROM tb_name` 给出一个表名，显示该表的所有列名
- 其他 `SHOW` 语句（可以 `\h SHOW`查询使用）
  - `SHOW STATUS`  用于显示广泛的 服务器状态信息
  - `SHOW CREATE DATABASE;`, `SHOW CREATE TABLE;`显示创建数据库或表
  - `SHOW GRANTS;` 显示用户的安全权限 
  - `SHOW ERRORS;`, `SHOW WARNINGS;` 显示服务器的错误或警告信息
