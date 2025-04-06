
# Reference
[csdn详细笔记](https://blog.csdn.net/qq_41112238/article/details/103595239)

# 1. Preliminary
## 框架概述

***软件架构概述***

<div style="text-align:center">
    <img src="pics/软件架构.png" alt="图片描述" style="margin-bottom: 1px;", width=70%>
    <p>软件架构</p>
</div>


***javaWeb框架概述***
<div style="text-align:center">
    <img src="pics/javaWeb技术框架.png" alt="图片描述" style="margin-bottom: 1px;", width=70%>
    <p>javaWeb技术框架</p>
</div>
 

## JDBC概述
***数据持久化***

如 Java的 I/O流中，内存缓冲buffer就不是持久化保存数据，而文件操作则是真正的数据保存

内存中的数据，不仅能保存到文件，存储介质其实有很多（file, sql, ...），保存到数据库是更加常用的数据持久化选择

***Java中的数据存储技术***

- JDBC 直接访问数据库
- JDO (Java Data Object) 技术
- 第三方 O/R 工具：Hiernate、Mybatis等

**都是 JDBC 的高级封装工具**

***JDBC连接概述***
<div style="text-align:center">
    <img src="pics/JDBC连接概述.png" alt="图片描述" style="margin-bottom: 1px;", width=70%>
    <p>JDBC连接概述</p>
</div>
 

***JDBC 程序编写步骤***
<div style="text-align:center">
    <img src="pics/JDBC程序编写步骤.png" alt="图片描述" style="margin-bottom: 1px;">
    <p>JDBC程序编写步骤</p>
</div>
 



# 2. JDBC 编程技术

***vscode 添加 Java的 mysql驱动（.jar文件）***
[VS code java连接MySQL详解](https://blog.csdn.net/m0_57089822/article/details/122078217)

- `Driver` 每个驱动程序类必须实现的接口 （一些jar包中已经实现，如com.mysql.jdbc.Driver.Driver() 需要关注方法的调用）
    - 如 `Connection connect(String url, Properties info)` 返回一个 Connection对象
- `Connection` 是一个与特定数据库连接的会话（session）对象
- `DriverManager` 用于管理一组 JDBC 驱动程序的服务 的类


## 数据库连接
迭代的5种连接方式

- 从第一种方式不断迭代，开始直接使用 数据库信息、mysql的jar包、mysql的 Driver驱动
- 后续不断抽象
    - 使用反射机制动态 创建驱动实例
    - 使用 DriverManager 这一统一接口来管理不同数据库的驱动程序
    - 资源信息（数据库信息）放入 jdbc.properties
    - ...


### 抽象和封装

JDBC 的设计目标是提供一种与数据库无关的接口，让开发者能够以统一的方式操作不同的数据库。

DriverManager 作为中间层，封装了驱动程序的细节，使得开发者无需直接与驱动程序交互。

如果直接使用 Driver 的实例，代码将与具体的数据库驱动程序紧密耦合，违反了 JDBC 的设计理念。
驱动程序注册机制

### 驱动程序注册机制

在 JDBC 规范中，驱动程序需要通过 DriverManager 进行注册。驱动程序类通常会实现 java.sql.Driver 接口，并在加载时自动注册到 DriverManager 中。

```java
public class MyDriver implements Driver {
    static {
        DriverManager.registerDriver(new MyDriver());
    }
}
```

## CRUD

### 使用PreparedStatement实现CRUD 

- 数据库连接session 被用于**向数据库服务器发送命令和SQL语句**，并接受数据库服务器返回的结果，其实一个数据库连接就是一个 Socket连接
- java.sql包中有3个接口分别定义了对数据库的调用的不同方式
    - ***Statement***: 用于执行静态SQL语句并返回它所生成结果的对象
    - ***PreparedStatement***： `PreparedStatement` 是 `Statement`接口的子接口，SQL语句被预编译并存储在此对象中，可以使用此对象多次高效地执行该语句
    - ***CallableStatement***：用于执行SQL存储过程

<div style="text-align:center">
    <img src="pics/接口交互关系.png" alt="图片描述" style="margin-bottom: 1px;", width=70%>
    <p>接口交互关系</p>
</div>

***直接使用Statement的弊端***
- 需要拼写sql 语句，并且存在SQL注入问题

### Bean
在 Java 编程中，**Bean** 是一个遵循特定编写规范的 Java 类，通常具有以下特点：

1. **可序列化**：Bean 类通常实现 `java.io.Serializable` 接口，这意味着它的实例可以被转换为字节序列，从而可以在网络上传输或者存储到文件中。

2. **无参数构造函数**：Bean 类通常包含一个无参数的构造函数，这样它们就可以在不提供任何初始值的情况下被实例化。

3. **属性访问方法**：Bean 类的属性（字段）通常是私有的（private），并且通过公共的 getter 和 setter 方法来访问和修改这些属性。这种封装方式遵循 Java 的封装原则。

4. **命名规范**：Bean 的属性访问方法遵循特定的命名规范。对于一个名为 `propertyName` 的属性，其 getter 方法命名为 `getPropertyName()`，setter 方法命名为 `setPropertyName()`。

5. **可选地实现事件处理**：在某些情况下，Bean 可以包含事件监听器和通知方法，用于处理事件。

Bean 通常用于以下目的：

- **数据传输**：在应用程序的不同层之间传递数据，例如从表示层（前端）到业务逻辑层，再到数据访问层。
- **配置管理**：存储应用程序的配置信息，如数据库连接信息、文件路径等。
- **数据绑定**：在图形用户界面（GUI）编程中，Bean 可以用于将数据绑定到界面组件上，实现数据和界面的同步更新。

***JavaBean 是一种特殊的 Bean，它遵循 JavaBean 规范，即 JavaBeans 规范。JavaBean 是一种可重用的组件，可以轻松地集成到不同的应用程序中。***

以下是一个简单的 JavaBean 示例：

```java
public class UserBean implements java.io.Serializable {
    private String name;
    private int age;

    // 无参数构造函数
    public UserBean() {
    }

    // 带参数的构造函数
    public UserBean(String name, int age) {
        this.name = name;
        this.age = age;
    }

    // name 属性的 getter 和 setter 方法
    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    // age 属性的 getter 和 setter 方法
    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }
}
```

在这个示例中，`UserBean` 类有两个私有属性 `name` 和 `age`，以及相应的公共 getter 和 setter 方法。这个类还实现了 `Serializable` 接口，使其实例可以被序列化。


### ORM 
#### 什么是ORM思想？

**ORM**（Object-Relational Mapping，对象关系映射）是一种编程技术，用于将面向对象的编程语言中的对象映射到关系型数据库的表格中。ORM 的核心思想是让开发者能够使用面向对象的方式来操作数据库，而不需要编写复杂的 SQL 语句。

ORM 的主要特点包括：

1. **对象和表的映射**：在 ORM 中，数据库中的表通常对应于一个对象模型（即一组 Java 类或 C# 类等），表中的行对应于对象实例。

2. **字段和属性的映射**：数据库表中的列对应于对象的属性，这些属性通常是私有的，并通过 getter 和 setter 方法访问。

3. **关系映射**：数据库中的外键关系、一对多关系、多对多关系等可以通过对象之间的关系来表示。

4. **数据操作**：通过操作对象（如创建、修改、删除对象）来间接操作数据库中的数据。

5. **查询**：ORM 提供了查询接口，可以方便地查询数据库中的数据，而不需要编写 SQL 语句。

#### Bean和ORM的关系

**Bean** 和 **ORM** 之间的关系主要体现在以下几个方面：

1. **数据模型**：Bean 通常用作 ORM 的数据模型。在 ORM 中，Bean 类通常对应于数据库中的一个表，Bean 类的属性对应于表的列。

2. **封装**：Bean 类遵循 JavaBean 规范，具有封装性，其属性通常是私有的，并通过 getter 和 setter 方法访问。这种封装性使得 Bean 类可以方便地与 ORM 框架集成。

3. **序列化**：Bean 类通常实现 `Serializable` 接口，这使得它们可以被序列化和反序列化，这对于 ORM 框架中的数据传输和持久化非常重要。

4. **数据操作**：在 ORM 框架中，开发者可以通过操作 Bean 对象来间接操作数据库中的数据。ORM 框架会自动将对象的操作转换为相应的 SQL 语句。

5. **查询和映射**：ORM 框架通常提供了丰富的查询接口，开发者可以通过这些接口查询数据库中的数据，并将查询结果映射为 Bean 对象。

#### 示例：使用 ORM 框架操作数据库

假设我们使用 Hibernate 作为 ORM 框架，以下是一个简单的示例：

```java
import org.hibernate.Session;
import org.hibernate.SessionFactory;
import org.hibernate.cfg.Configuration;
import org.hibernate.Transaction;

public class Main {
    public static void main(String[] args) {
        // 配置 Hibernate
        SessionFactory factory = new Configuration().configure().buildSessionFactory();
        Session session = factory.openSession();

        try {
            Transaction tx = session.beginTransaction();

            // 创建一个 Bean 对象
            Customer customer = new Customer();
            customer.setName("John Doe");
            customer.setEmail("john.doe@example.com");

            // 保存 Bean 对象到数据库
            session.save(customer);

            tx.commit();
        } catch (Exception e) {
            e.printStackTrace();
        } finally {
            session.close();
        }
    }
}
```

在这个示例中，我们创建了一个 `Customer` 类，它是一个 Bean 类，对应于数据库中的 `customers` 表。我们使用 Hibernate 来操作数据库，通过创建 `Customer` 对象并调用 `session.save()` 方法，将对象保存到数据库中。Hibernate 会自动将对象的操作转换为相应的 SQL 语句。

总之，Bean 是 ORM 的数据模型，ORM 框架通过操作 Bean 对象来间接操作数据库中的数据，从而简化了数据库操作的复杂性。

## 25-28练习待完成

## 命令行验证MySQL事务的隔离性
***为什么在代码中，setAutoCommit(false)代表开启事务***
```
事务的原子性要求要么全部提交要么全部回滚
关闭自动提交可以保证出现异常情况下还能回滚已经执行但未提交的部分
```

- ***首先新增一个用户，让其对 数据库中的一个表具有操作权限***
    - `CREATE USER sijor IDENTIFIED BY 'sijor123456';`
    - `SELECT Host, User FROM mysql.user;`
- **为新用户赋予对root中某个作为公共表的操作权限**
    - `SHOW GRANTS FOR sijor;`
    - ` GRANT SELECT,INSERT,DELETE,UPDATE ON jdbctest.user_table TO 'sijor'@'%';`
- **查看隔离级别**
    - `SELECT @@transaction_isolation;`


用户查看命令

```sql
-- 登录root用户
-- 1. 查看当前用户
mysql> SELECT Host, User FROM mysql.user;
+-----------+------------------+
| Host      | User             |
+-----------+------------------+
| localhost | mysql.infoschema |
| localhost | mysql.session    |
| localhost | mysql.sys        |
| localhost | root             |
+-----------+------------------+
4 rows in set (0.00 sec)
```


创建新用户命令

```sql
-- 2. 新增用户 sijor
mysql> CREATE USER sijor IDENTIFIED BY 'sijor123456';
Query OK, 0 rows affected (0.03 sec)

mysql> SELECT Host, User FROM mysql.user;
+-----------+------------------+
| Host      | User             |
+-----------+------------------+
| %         | sijor            |
| localhost | mysql.infoschema |
| localhost | mysql.session    |
| localhost | mysql.sys        |
| localhost | root             |
+-----------+------------------+
5 rows in set (0.00 sec)

```

用户权限赋予、查看命令
```sql
-- 3. 新用户操作权限的赋予
mysql> SHOW GRANTS FOR sijor;
+-----------------------------------+
| Grants for sijor@%                |
+-----------------------------------+
| GRANT USAGE ON *.* TO `sijor`@`%` |
+-----------------------------------+
1 row in set (0.00 sec)

mysql> GRANT SELECT,INSERT,DELETE,UPDATE ON jdbctest.user_table TO 'sijor'@'%';
Query OK, 0 rows affected (0.01 sec)

mysql> SHOW GRANTS FOR sijor;
+--------------------------------------------------------------------------------+
| Grants for sijor@%                                                             |
+--------------------------------------------------------------------------------+
| GRANT USAGE ON *.* TO `sijor`@`%`                                              |
| GRANT SELECT, INSERT, UPDATE, DELETE ON `jdbctest`.`user_table` TO `sijor`@`%` |
+--------------------------------------------------------------------------------+
2 rows in set (0.00 sec)

-- 4. 此时登录sijor发现可以看到 user_table表
mysql> SHOW DATABASES;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| jdbctest           |
| performance_schema |
+--------------------+
3 rows in set (0.00 sec)

mysql> USE jdbctest;
Database changed
mysql> SHOW TABLES;
+--------------------+
| Tables_in_jdbctest |
+--------------------+
| user_table         |
+--------------------+
1 row in set (0.00 sec)

```

查看隔离级别
```sql
mysql> SELECT @@transaction_isolation;
+-------------------------+
| @@transaction_isolation |
+-------------------------+
| REPEATABLE-READ         |
+-------------------------+
1 row in set (0.00 sec)
```

## DAO (Data Access Object)

数据访问对象

***针对具体的数据库表可以有具体的 DAO，即继承一个带有通用操作的 BaseDAO，实现一个针对表的DAO接口***

***规范实现：使用接口，即 TableNameDAO，然后再实现该接口，即实现类 TableNameDAOImpl （Impl是 Implement的 简写）***


