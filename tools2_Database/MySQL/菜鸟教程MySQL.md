# MySQL 
- [菜鸟教程](https://www.runoob.com/mysql/mysql-connection.html)
- [MySQL安装教程](https://blog.csdn.net/weixin_47406082/article/details/131867849?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522171647672116800225532250%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=171647672116800225532250&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~top_positive~default-2-131867849-null-null.142^v100^pc_search_result_base8&utm_term=MySQL%E5%AE%89%E8%A3%85&spm=1018.2226.3001.4187)
- [navicat安装教程](https://blog.csdn.net/weixin_50670076/article/details/136350060?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522171657178116800182137881%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=171657178116800182137881&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~top_positive~default-1-136350060-null-null.142^v100^pc_search_result_base8&utm_term=navicat&spm=1018.2226.3001.4187)
- [navicat使用教程](https://blog.csdn.net/qq_45069279/article/details/105919312?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522171657178116800182137881%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=171657178116800182137881&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~top_positive~default-2-105919312-null-null.142^v100^pc_search_result_base8&utm_term=navicat&spm=1018.2226.3001.4187)
- [卸载教程](https://blog.csdn.net/m0_52861000/article/details/131354710?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522172110015316800180631045%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=172110015316800180631045&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~top_positive~default-2-131354710-null-null.142^v100^pc_search_result_base8&utm_term=%E5%8D%B8%E8%BD%BDmysql&spm=1018.2226.3001.4187)


## 命令行
- cmd连接mysql： `mysql -u username -p` (如 `mysql -u root -p`)
- 进一步还能指定主机(host)、端口号(port)：  
  - `mysql -u username -p -h myserver -P 9999`  


## 使用
***ps: [] 代表是可选参数***
- `CREATE DATABASE [IF NOT EXISTS] db_name`  创建数据库
  - `CREATE DATABASE demo`
  - `CREATE DATABASE IF NOT IF EXIST demo;`
- `DROP DATABASE [IF EXISTS] db_name`   删除数据库
  - `DROP DATABASE IF EXISTS demo`
  - `DROP DATABASE demo`
- `USE db_name;` : 选择一个数据库
  - `Database changed` 选择成功后（即切换到所选数据库）的显示 
  - `SELECT DATABASE();` 显示当前所在数据库
- `SHOW DATABASES;`显示数据库信息
- `SHOW TABLES;` 返回数据库内的可用列表有哪些
  - `Tables_in_dbname` 返回的显示信息，（列出了 `dbname` 数据库中所包含的数据表）
  - `SHOW COLUMNS FROM table_name` 进一步显示表中的列信息
- 其他 `SHOW` 语句：
  - `SHOW TABLE STATUS LIKE 'table_name'` 注意表明要加单引号
  - `SHOW STATUS`;
  - `SHOW CREATE DATABASE/TABLE`;
  - `SHOW GRANTS`;
  - `SHOW ERRORS/WARNINGS`;

***自动增量***
> CREATE 创建表时，将 AUTO_INCREMENT 定义为表的组成部分
> 从而对应的 COLUMNS在每添加一行数据时候，会自动分配下一个可用编号


***导入sql数据***
> `msql > source D:\...\xxx.sql`
> 在masql中使用 `source`命令，可以读取路径上的sql文件，根据其中sql语句创建对应表并插入数据


## 创建表和操纵表



