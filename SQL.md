[[SQL概论]]
[[JDBC]]
# DML

## `DML(Data Munipulation Language)数据操作语言`

1. `insert`
2. `delete`
3. `update`

> 说明：
>  `[]`表示可选语句，实际使用并不用加`[]`。
## INSERT

```sql
 -- 给指定字段添加数据  
 INSERT INTO 表名(字段名1,字段名2,……) VALUES(值1,值2,……);  
 -- 给全部字段添加数据  
 INSERT INTO `表名` VALUES(值1,值2,……);  
 -- 批量添加数据  
 INSERT INTO 表名(字段名1,字段名2,……) VALUES(值1,值2,……)，(值1,值2,……);  
 INSERT INTO 表名(值1,值2,……),(值1,值2,……),(值1,值2,……);
```
注意：

- 插入数据时，指定的字段顺序需要与值的顺序是一一对应的。
	
- 字符串和日期型数据应该包含在单引号中。
	
- 插入的数据大小，应该在字段的规定范围内。
	

## UPDATE

```sql
 UPDATE 表名 SET 字段名1=值1,字段名2=值2,……[WHERE 条件];
```

## DELETE

```sql
DELETE FROM 表名 [WHERE 条件];
```

注意：

- DELETE语句不能删除某一个字段的值(可以使用UPDATE)。



# DQL

 `DQL(Data Query Language)数据查询语言`

```sql
 1. SELECT -- 字段列表  
 2. FROM -- 表名列表  
 3. WHERE -- 条件列表  
 4. GROUP BY -- 分组字段列表  
 5. HAVING -- 分组后条件列表  
 6. ORDER BY -- 排序字段列表  
 7. LIMIT -- 分页参数
```

## SELECT
### 条件查询

```sql
 -- 1.查询多个字段  
 SELECT 字段1,字段2,字段3…… FROM 表名;  
 SELECT * FROM 表名;  
 -- 2.设置别名  
 SELECT 字段1 [AS 别名1],字段2[AS 别名2]…… FROM 表名;  
 -- 3.去除重复记录  
 SELECT DISTINCT 字段列表 FROM 表名;  
 -- 4.条件查询  
 SELECT 字段列表 FROM 表名 WHERE 条件列表;

```
- `WHERE`后可跟的运算符
    ![image-20250314192140325|700](file:///C:/Users/30703/AppData/Roaming/Typora/typora-user-images/image-20250314192140325.png?lastModify=1742114941)
    
    ![image-20250314192155915|700](file:///C:/Users/30703/AppData/Roaming/Typora/typora-user-images/image-20250314192155915.png?lastModify=1742114941)

### 聚合函数

- 将一列数据作为一个整体，进行纵向计算。
  
- `注意：null值不参与所有聚合函数运算。`
  

	![image-20250316130844931|700](file:///C:/Users/30703/AppData/Roaming/Typora/typora-user-images/image-20250316130844931.png?lastModify=1742114941)

 SELECT 聚合函数(字段列表) FROM 表名;

### 分组查询

- 注意
  
    1. 执行顺序:`where > 聚合函数 > having`。
       
    2. 分组之后，查询的字段一般为聚合函数和分组字段，查询其他字段无任何意义。
       

```sql
 SELECT 字段列表 FROM 表名 [WHERE 条件] GROUP BY 分组字段名 [HAVING 分组后过滤条件];
```

- where与having区别
  
    1. 执行时机不同：where是分组之前进行过滤，不满足where条件，不参与分组；而having是分组之后对结果进行过滤。
       
    2. 判断条件不同：where不能对聚合函数进行判断，而having可以。

### 排序查询

```sql
SELECT 字段列表 FROM 表名 ORDER BY 字段1 排序方式1,字段2 排序方式2;
```

#### 排序方式

- ASC: 升序(默认值)
- DESC: 降序

> 注意：如果是多字段排序，当第一个字段值相同时，才会根据第二个字段进行排序。

### 分页查询

```sql
SELECT 字段列表 FROM 表名 LIMIT 起始索引,查询记录数;
```

> 注意> 
>  - 起始索引从0开始，起始索引=（查询页码-1）*每页显示记录数。
>  - 分页查询是数据库的方言，不同的数据库有不同的实现，MySQL中是LIMIT。
>  - 如果查询的是第一页数据，起始索引可以省略，直接简写为limit10。

### 执行顺序

![[Pasted image 20250316184321.png|500]]

# DCL

	Data Control Language(数据控制语言)，用来管理数据库用户、控制数据库的访问权限。

## 管理用户


```sql
-- 1. 查询用户
USE mysql;
SELECT * FROM user;
-- 2. 创建用户 
CREATE USER '用户名'@'主机名' IDENTIFIED BY '密码';
-- 3. 修改用户密码
ALTER USER '用户名'@'主机名' IDENTIFIED WITH mysql_native_password BY '新密码';
-- 4. 删除用户
DROP USER '用户名'@'主机名';
```

> 注意：
	- 主机名可以使用%通配。
	- 这类SQL开发人员操作的比较少，主要是DBA（DatabaseAdministrator数据库管理员）使用。

## 权限控制

![[Pasted image 20250317093922.png|700]]

### 查询权限
```sql
SHOW GRANTS  FOR '用户名'@'主机名';
```
### 授予权限
```sql
GRANT 权限列表 ON 数据库名.表名 TO '用户名'@'主机名';
```
### 撤销权限
```sql
REVOKE 权限列表 ON 数据库名.表名 FROM '用户名'@'主机名';
```

> 注意：
	- 多个权限之间，使用逗号分隔
	- 授权时，娄数据库名和表名可以使用*进行通配，代表所有。

# 函数

## 字符串函数

![[Pasted image 20250320172745.png | 900]]

练习：

> 由于业务需求变更，企业员工的工号，统一为5位数，目前不足5位数的全部在前面补0。比如：1号员
> 工的工号应该为00001。
```sql
update emp set workno = lpad(workno, 5, '0');
```

## 数值函数

![[Pasted image 20250320173936.png | 900]]

练习：

 ![[Pasted image 20250320174740.png|600]]
```sql
select rpad(round(rand() * pow(10, 7), 0), 6, '0');
```

## 日期函数

![[Pasted image 20250320174913.png| 900]]

练习：

![[Pasted image 20250320180048.png| 600]]
```sql
select name '姓名', datediff(curdate(), entryDate) '入职天数' from emp order by '入职天数' desc;
```

## 流程函数

![[Pasted image 20250320180312.png|1200]]

练习：
![[Pasted image 20250320225629.png|600]]
```sql
select  
    name,  
    ( case when age >= 40  then '优秀' when age >= 20 then '及格' else '不及格' end) '评价'  
from emp;
```

# 约束

- 概念：约束是作用于表中字段上的规则，用于限制存储在表中的数据。
- 目的：保证数据库中数据的正确、有效性和完整性。

![[Pasted image 20250320225925.png|1000]]

> 注意：约束是作用于表中字段上的，可以在创建表/修改表的时候添加约束。

## 外键约束

### 添加外键
```sql
CREATE TABLE 表名(
	字段名 数据类型,
	……
	[CONSTRAINT] [外键名称] FOREIGN KEY (外键字段名) REFERENCES 主表 (主表列名)
)
ALTER TABLE 表名 ADD CONSTRAINT 外键名称 FOREIGN KEY (外键字段名) RENFERENCES 主表 (主表列名);
```
### 删除外键
```sql
ALTER TABLE 表名 DROP FOREIGN KEY 外键名称;
```

### 外键约束
![[Pasted image 20250322130629.png|1200]]

```sql
ALTER TABLE 表名 ADD CONSTRAINT 外键名称 FOREIGN KEY (外键字段) REFERENCES 主表名(主表字段名) ON UPDATE CASCADE ON DELETE CASCADE;
```

# 事务

> 默认MySQL的事务是自动提交的，也就是说，当执行一条DML语句，MySQL会立即隐式的提交事务。

## 事务操作

查看/设置事务提交方式
```sql
SELECT @@autocommit;
SET @@AUTOCOMMIT = 0;
```
提交事务
```sql
COMMIT;
```
回滚事务
```sql
ROLLBACK;
```
开启事务
```sql
START TRANSACTION;
BEGIN;
```

## 四大特性(ACID)

1. 原子性（Atomicity）：事务是不可分割的最小操作单元，要么全部成功，要么全部失败。
2. 一致性（Consistency）：事务完成时，必须使所有的数据都保持一致状态。
3. 隔离性（Isolation）：数据库系统提供的隔离机制，保证事务在不受外部并发操作影响的独立环境下运行。
4. 持久性（Durability）：事务一旦提交或回滚，它对数据库中的数据的改变就是永久的。

## 并发事务问题

![[Pasted image 20250322133734.png|1100]]

## 事务隔离级别

![[Pasted image 20250322172911.png|1100]]
- `READ UNCOMMITTED`
	- 性能最好，安全性最差
- `SERIALIZABEL`
	- 安全性最好，性能最差
	- 可以规避所有的并发事务问题
- 从上到下隔离级别逐渐增高
> - 注意：事务隔离级别越高，数据越安全，但是性能越低。

```sql
-- 查看事务隔离级别
SELECT @@TRANSACTION_ISOLATION;
-- 设置事务隔离级别
SET [SESSION | GLOBAL] TRANSACTION ISOLATION LEVEL {READ UNCOMMITTED | READ COMMITTED | REPEATTABLE READ | SERIALIZABLE}
```
- `SESSION`：针对当前会话窗口有效
- `GLOBAL`：对于所有会话窗口有效

### 实践记录 2025年3月22日18点02分
![[Pasted image 20250322180240.png|1100]]
>问题：
   理解数据库幻读问题。
> 当右侧console修改数据后没有提交时，左侧console也插入相同主键数据时，左侧console未响应，
> 只有右侧console提交后左侧console才会报错。
> 这是出现了什么问题
> 注：左右侧isolation level 都为`repeatable read`;

> GPT-4o
> 从截图中的描述以及问题来看，这里涉及到 **事务隔离级别** 和 **锁机制**。

### 问题分析
1. **右侧 Console**：
    - 在事务中更新了 `id = 6` 的数据，但没有提交。
    - 由于事务未提交，变更操作对其他事务不可见。
2. **左侧 Console**：
    - 插入了主键为 `6` 的记录，未报错，表现为等待状态。
    - 然后当右侧 Console 提交事务后，左侧 Console 才报主键冲突错误。
    这是因为：
- **MySQL 的默认事务隔离级别是 `REPEATABLE READ`**，在这个级别下：
    - 事务中查询的数据是一致性快照（读的内容是事务开始时的状态）。
    - 右侧 Console 修改了 `id = 6` 的记录，但未提交，因此左侧 Console 查询时看不到这部分变更的数据。
- **锁机制**：
    - 右侧 Console 修改 `id = 6` 的数据时，MySQL 会对==该记录加上行级排他锁（`X 锁`）==。
    - ==左侧 Console 尝试插入相同主键时，也需要对主键 `6` 加锁，但因为右侧 Console 已经持有锁，左侧 Console 被阻塞，直到右侧 Console 提交事务==。
1. **最终结果**：
    - 当右侧 Console 提交事务后，左侧 Console 的插入操作被执行。
    - 此时发现主键冲突，报错 `ERROR 1062: Duplicate entry '6' for key 'dept.PRIMARY'`。

---
### 总结
  这种情况是由于 MySQL 的 **行锁机制** 和事务的隔离级别共同导致的。具体原因：
- **行锁**：右侧 Console 的未提交事务持有了 `id = 6` 的行级锁。
- **隔离级别**：左侧 Console 查询时看不到右侧的修改，因此尝试插入相同主键。
这种行为是 **锁等待机制** 的体现。

#### 自我总结
- 属于主键冲突引起的锁等待问题
- 上锁与isolation level无关
- **是否会“不上锁”？**
	- **不会完全“不上锁”。**
	- 对于 **插入（`INSERT`）和更新（`UPDATE`）** 操作，不论使用哪种隔离级别，锁机制都会存在。
- 只要涉及主键冲突检查，行锁（`Row Lock`）就无法避免。

## 触发器

- 触发器是与表有关的数据库对象，指在insert/update/delete之前或之后，触发并执行触发器中定义的SQL语句集合。触发器的这种特性可以协助应用在数据库端确保数据的完整性，日志记录，数据校验等操作
- 使用别名OLD 和 NEW来引用触发器中发生变化的记录内容，这与其他的数据库是相似的。现在触发器还`只支持行级触发`，`不支持语句级触发`。

## 语法

1. 创建

   ```sql
   create trigger trgger_name
   before/after insert/update/delete
   on tbl_name for each row 
   begin
   	trigger_stmt;
   end;
   ```

2. 查看

   ```sql
   show triggers;
   ```

3. 删除

   ```sql
   drop trigger [schema_name.]trigger_name;
   ```

   

