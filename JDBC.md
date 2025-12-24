# JDBC

JDBC：（`Java DataBase Connectivity`），就是使用Java语言操作关系型数据库的一套API。

- 本质
  1. sun公司官方定义的一套操作所有关系型数据库的规范，即接口。
  2. 各个数据库厂商去实现这套接口，提供数据库驱动jar包。
  3. 我们可以使用这套接口（JDBC）编程，真正执行的代码是驱动jar包中的实现类。

## 入门

- DML语句：`int rowsAffected = statement.executeUpdate();`
- DQL语句：`ResultSet rs = statement.executeQuery();`

### 结果集对象

- ResultSet（结果集对象）：`ResultSet rs= statement.executeQuery()`
  1. `next()`：将光标从当前位置向前移动一行，并判断当前行是否为有效行，返回值为boolean。
     1. true：有效行，当前行有数据
     2. false：无效行，当前行没有数据
  2. `getXxx(..)`：获取数据，可以根据列的编号获取，也可以根据列名获取（推荐）。

### 预编译SQL

1. 安全

   - 预防SQL注入

     - SQL注入：通过控制输入来修改事先定义好的SQL语句，以达到执行代码对服务器进行攻击的方法。

       ```sql
       select count(*) from user where name = 'dnaiofa' and gender = '' or '1' = '1';
       ```

2. 性能高
   ![image-20250428181115882](C:\Users\30703\AppData\Roaming\Typora\typora-user-images\image-20250428181115882.png)



