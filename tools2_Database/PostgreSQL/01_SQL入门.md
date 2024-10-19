## SQL语法简介
- 语句分类：
  - DQL (data query language): 数据查询语句 ———— 查询
  - DML (data manipulation language): 数据操作语句 ———— 插入更新删除
  - DDL (data definition language): 数据定义语句 ———— 创建、删除（表或行数据）、修改表，索引等

### 语句汇总
```shell
创建数据库：
CREATE DATABASE database_name;
进入数据库：
\c database_name
****************************************************************************************

创建表格（在列定义后面加上 "primary key" 可以指定主键：）：
CREATE TABLE tabale_name(
    column_1_name       data_type primary key,
    column_2_name       data_type,
    column_3_name       data_type
);
显示数据库中表格，后面加表名字，指定表格加以显示
\d table_name

删除表格：  
DROP TABLE tablke_name;
****************************************************************************************

向表格中插入：
INSERT INTO table_name(optional params) VALUES(corresponding value);
INSERT INTO table_name(col_1, col_2, col_3) VALUES(col_1_val, col_2_val, col_2_val);

查询：
SELECT * FROM table_name;
****************************************************************************************

更新 列数据：
UPDATE table_name SET col_name = col_val;
UPDATE table_name SET col_name = col_val WHERE row_name = row_val;

删除行记录
DELETE FROM table_name WHERE row_name = row_val;
****************************************************************************************

查询所有数据：
SELECT * FROM table_name;

查询某几列，某一行的数据：
SELECT col1_name, col2_name, ..., coln_name FROM table_name WHERE row_name = row_val;

排序：
SELECT * FROM table_name ORDER BY row_name1;
SELECT * FROM table_name ORDER BY row_name1, row_name2, ..., row_namen;
SELECT * FROM table_name ORDER BY row_name1 DESC, ..., row_namen;
SELECT * FROM table_name ORDER BY row_name WHERE row_condition;

join关联查询：
隐式：
SELECT table1_col1, tbale2_col1, ... FROM table1 t1, table2 t2, ... WHERE condition;
显示：
SELECT table1_col1, tbale2_col1, ... FROM table1
INNER JOIN table2 ON condeiton_1_2
INNER JOIN table3 ON condition_1_3;


将表table_data数据全部插入表table_empty（列名要相同）
INSERT INTO table_empty SELECT * FROM table_data;

具有相同列名/字段的 表a 表b 中查询到的数据，合并在同一个表中
SELECT ... FROM table_a WHERE ... UNION SELECT ... FROM table_b WHERE ...;

TRUNCATE 删除
TRUNCATE TABLE table_name;
```

### DDL
#### 建表、删表语句
```shell
创建表格（在列定义后面加上 "primary key" 可以指定主键：）：
CREATE TABLE tabale_name(
    column_1_name       data_type primary key,
    column_2_name       data_type,
    column_3_name       data_type
);

显示数据库中表格，后面加表名字，指定表格加以显示
\d table_name

删除表格：  
DROP TABLE tablke_name;

例：

postgres_learning=# CREATE TABLE score (
postgres_learning(# student_name        varchar(40),
postgres_learning(# chinese_score       int,
postgres_learning(# math_score          int,
postgres_learning(# test_date           date);

postgres_learning=# CREATE TABLE student(
postgres_learning(# no          int primary key,
postgres_learning(# student_name        varchar(40),
postgres_learning(# age         int);

```
### DML
DML语句主要用于 插入、更新、删除数据，包括三种语句： `INSERT`、 `UPDATE`、 `DELETE`
#### INSERT
- `INSERT` 语句的语法以 "INSERT INTO" 关键字为首
  - 后跟 table_name及其可选参数列表（选择插入数据包含哪些列数据， 顺序改变， VALUES对应插入顺序也要变）
  - 再后跟 VALUES及其对应值列表
  - 如果table_name后没有插入参数列表，则默认插入数据包含全部列

```shell
向表格中插入：
INSERT INTO table_name(optional params) VALUES(corresponding value);

查询：
SELECT * FROM table_name;

例：

INSERT INTO student(no, student_name, age) VALUES(2, '李四', 13);
INSERT INTO student(no, student_name) VALUES(3, '张三');
```

#### UPDATE and DELETE
- `UPDATE` 以 "UPDATE" 为关键字
  - 后跟 table_name
  - 后跟 "SET" 关键字：表要设置的数据（col_name = value）
  - 后加 "WHERE" 可选择行（row_index = value）
$\space$
- `DELETE` 以 "DELETE FROM" 为关键字
  - 后跟 table_name
  - 后跟 "WHERE" 语句指定要删除的行记录（如果没有则为删除整个表）

```shell
更新 列数据：
UPDATE table_name SET col_name = col_val;

指定某行更新：
UPDATE table_name SET col_name = col_val WHERE row_name = row_val;

删除行记录
DELETE FROM table_name WHERE row_name = row_val;

例：

UPDATE student SET student_name='王五' WHERE no=2;
DELETE FROM student WHERE student_name='sijorhou';
```

### 查询语句
#### 单表查询、过滤条件查询
- `SELECT seg(col),... FROM table_name` 以 "SELECT" 为关键字
  - 后跟 列名 （若不是 * 则为查询所有列）
  - 再跟 "FROM" table_name  
  - 后跟 "WHERE" 语句指定要查询的行记录（如果没有则为查询对应列名的所有数据）

```shell
查询所有数据：
SELECT * FROM table_name;

查询某几列，某一行的数据：
SELECT col1_name, col2_name, ..., coln_name FROM table_name WHERE row_name = row_val;

例：

postgres_learning=# SELECT * FROM student;
 no | student_name | age
----+--------------+-----
  1 | 张三         |  16
  2 | 王五         |  26
  3 | 李四         |  33
(3 行记录)

postgres_learning=# SELECT no, age FROM student WHERE student_name = '李四';
 no | age
----+-----
  3 |  33
(1 行记录)

postgres_learning=# SELECT * FROM student WHERE age > 18;
 no | student_name | age
----+--------------+-----
  2 | 王五         |  26
  3 | 李四         |  33
(2 行记录)
```
#### 排序查询
- `ORDER BY`末尾跟 "ORDER BY"
  - 后跟列名，表按照列数据进行升序排序
  - 可以跟多个列名，表按照多个列数据进行排序
  - 某个列名后面跟 `DESC` 表按此列数据进行 *倒序排序*
- `ORDER BY` 要放在 `WHERE` 后面，否则会报错

```shell
排序：
SELECT * FROM table_name ORDER BY row_name1;
SELECT * FROM table_name ORDER BY row_name1, row_name2, ..., row_namen;
SELECT * FROM table_name ORDER BY row_name1 DESC, ..., row_namen;
SELECT * FROM table_name ORDER BY row_name WHERE row_condition;

例：
postgres_learning=# SELECT * FROM student ORDER BY student_name;
 no | student_name | age
----+--------------+-----
  3 | 李四         |  33
  2 | 王五         |  26
  1 | 张三         |  16
(3 行记录)

postgres_learning=# SELECT * FROM student ORDER BY age WHERE age > 18;
错误:  语法错误 在 "WHERE" 或附近的
第1行SELECT * FROM student ORDER BY age WHERE age > 18;
                                        ^
postgres_learning=# SELECT * FROM student WHERE age > 18 ORDER BY age;
 no | student_name | age
----+--------------+-----
  2 | 王五         |  26
  3 | 李四         |  33
(2 行记录)

postgres_learning=# SELECT * FROM student WHERE age > 18 ORDER BY student_name ,age;
 no | student_name | age
----+--------------+-----
  3 | 李四         |  33
  2 | 王五         |  26
(2 行记录)

postgres_learning=# SELECT * FROM student ORDER BY age DESC, no;
 no | student_name | age
----+--------------+-----
  3 | 李四         |  33
  2 | 王五         |  26
  1 | 张三         |  16
(3 行记录)

```
#### 分组查询
- `GROUP BY` 后跟所需分组查询的列名
```shell
postgres_learning=# select * from student;
 no | student_name | age
----+--------------+-----
  1 | 张三         |  16
  2 | 王五         |  26
  3 | 李四         |  33
  4 | sijorhou     |  26
  5 | WeijieHou    |  16
(5 行记录)


postgres_learning=# SELECT age, count(*) FROM student GROUP BY age;
 age | count
-----+-------
  26 |     2
  16 |     2
  33 |     1
(3 行记录)
```

#### 表 join
也称 ***多表关联查询***

假设有如下两张表
```shell
postgres_learning=# select * from class;
 no | class_name
----+-------------
  1 | 高三（1）班
  2 | 高三（2）班
  3 | 高三（3）班
  4 | 高三（4）班
(4 行记录)

postgres_learning=# select * from student;
 no | student_name | age | class_no
----+--------------+-----+----------
  1 | 张三         |  14 |        1
  2 | 吴二         |  15 |        1
  3 | 李四         |  14 |        2
  4 | 王五         |  15 |        2
  5 | 赵六         |  15 |        3
  6 | 钱七         |  14 |        3
  7 | 吴二         |  15 |        4
  8 | 赵九         |  14 |        4
(8 行记录)
```

若想查询每个学生和班级的关系：
- 关联查询：
  - 两张表 `SELECT` 后跟字段名（不同表的列名，无需考虑和表名的对应顺序关系，因为列名都是唯一的， 如果 不同表有相同列名，则报错不明确）
  - `FROM` 后跟表名
  - 后跟 `WHERE` condition
- 显示内联方式
  - `INNER JOIN ` 前后关联两个表名
  - `ON` 取代 `WHERE` 指定关联查询的条件
- 可以给表取别名，就像定义变量 class_name val_name
- 可以用 `AND` 连接多个条件
```shell
SELECT table1_col1, tbale2_col1, ... FROM table1 t1, table2 t2, ... WHERE condition;
SELECT table1_col1, tbale2_col1, ... FROM table1
INNER JOIN table2 ON condeiton_1_2
INNER JOIN table3 ON condition_1_3;


例：

字段名称顺序不影响查询，但结果显示顺序被影响
postgres_learning=# SELECT student_name, class_name FROM student a, class b WHERE a.class_no = b.no;
 student_name | class_name
--------------+-------------
 张三         | 高三（1）班
 吴二         | 高三（1）班
 李四         | 高三（2）班
 王五         | 高三（2）班
 赵六         | 高三（3）班
 钱七         | 高三（3）班
 吴二         | 高三（4）班
 赵九         | 高三（4）班
(8 行记录)

postgres_learning=# SELECT class_name, student_name FROM student a, class b WHERE a.class_no = b.no;
 class_name  | student_name
-------------+--------------
 高三（1）班 | 张三
 高三（1）班 | 吴二
 高三（2）班 | 李四
 高三（2）班 | 王五
 高三（3）班 | 赵六
 高三（3）班 | 钱七
 高三（4）班 | 吴二
 高三（4）班 | 赵九
(8 行记录)

多个条件关联查询
postgres_learning=# SELECT student_name, class_name FROM student a, class b WHERE a.class_no = b.no AND a.age > 14;
 student_name | class_name
--------------+-------------
 吴二         | 高三（1）班
 王五         | 高三（2）班
 赵六         | 高三（3）班
 吴二         | 高三（4）班
(4 行记录)

显示内连接语法
postgres_learning=# SELECT a.student_name, b.class_name FROM student a INNER JOIN class b ON a.class_no = b.no AND a.age > 14;
 student_name | class_name
--------------+-------------
 吴二         | 高三（1）班
 王五         | 高三（2）班
 赵六         | 高三（3）班
 吴二         | 高三（4）班
(4 行记录)

不明确报错
postgres_learning=# SELECT no, student_name, class_name FROM student s INNER JOIN class c ON s.class_no = c.no;
错误:  字段关联 "no" 是不明确的
第1行SELECT no, student_name, class_name FROM student s INNER JOI...
```

### 其他SQL语句
#### INSERT INTO SELECTFROM 复制语句
将一个表的内容全部插入到另一个具有相同列的表中
- `INSERT INTO ... SELECT FROM ...`
  - `INSERT INTO` 后跟一个表名
  - `SELECT FROM` 后跟被拷贝数据的表名
```shell
INSERT INTO table_empty SELECT * FROM table_data;

例：
student 数据表
postgres_learning=# SELECT * FROM student;
 no | student_name | age | class_no
----+--------------+-----+----------
  1 | 张三         |  14 |        1
  2 | 吴二         |  15 |        1
  3 | 李四         |  14 |        2
  4 | 王五         |  15 |        2
  5 | 赵六         |  15 |        3
  6 | 钱七         |  14 |        3
  7 | 吴二         |  15 |        4
  8 | 赵九         |  14 |        4
(8 行记录)

新建的学生备份空表，列与学生表一致
postgres_learning=# SELECT * FROM stu_backup;
 no | student_name | age | class_no
----+--------------+-----+----------
(0 行记录)

从student全部插入到stu_backup
postgres_learning=# INSERT INTO stu_backup SELECT * FROM student;
INSERT 0 8

stu_backup拷入新数据
postgres_learning=# SELECT * FROM stu_backup;
 no | student_name | age | class_no
----+--------------+-----+----------
  1 | 张三         |  14 |        1
  2 | 吴二         |  15 |        1
  3 | 李四         |  14 |        2
  4 | 王五         |  15 |        2
  5 | 赵六         |  15 |        3
  6 | 钱七         |  14 |        3
  7 | 吴二         |  15 |        4
  8 | 赵九         |  14 |        4
(8 行记录)
```
#### UNION 语句
适用于两个具有相同列名/字段的表之间的数据合并

从 a中查询到的数据 UNION 从b中查询到的数据， 合并在一个数据集之下
- `SELECT` 查询语句2 `UNION` `SELECT`查询语句2
```shell
SELECT ... FROM table_a WHERE ... UNION SELECT ... FROM table_b WHERE ...;

例：
postgres_learning=# SELECT * FROM student WHERE class_no = 4 UNION SELECT * FROM stu_backup WHERE no <= 3;
 no | student_name | age | class_no
----+--------------+-----+----------
  3 | 李四         |  14 |        2
  7 | 吴二         |  15 |        4
  2 | 吴二         |  15 |        1
  8 | 赵九         |  14 |        4
  1 | 张三         |  14 |        1
(5 行记录)
```
#### TRUNCATE 语句
`TRUNCATE TABLE table_name` 和 `DELETE FROM table_name` 实现相同的效果

但内在机制不同：
- `TRUNCATE TABLE table_name`抛弃旧表创建新空表，等效于一次性删除全部数据
- `DELETE FROM table_name` 等效于一条一条删光数据

```shell
postgres_learning=# TRUNCATE TABLE stu_backup;
TRUNCATE TABLE
postgres_learning=# SELECT * FROM stu_backup;
 no | student_name | age | class_no
----+--------------+-----+----------
(0 行记录)
```

