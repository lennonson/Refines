- MyBatis是一款优秀的持久层框架，用于简化JDBC 的开发。
- MyBatis本是 Apache的一个开源项目iBatis，2010年这个项目由apache迁移到了googlecode，并且改名为MyBatis。2013年11月迁移到Github。
- 官网: https://mybatis.org/mybatis-3/zh_CN/index.html

## 入门

1. 准备工作:
	1. 创建SpringBoot工程、引l入Mybatis相关依赖
	2. 准备数据库表user、实体类User
	3. 配置Mybatis（在application.properties中数据库连接信息）
	4. 编写Mybatis程序：编写Mybatis的持久层接口，定义SQL（注解/XML)
```properties
spring.datasource.url = jdbc:mysql://localhost:3306/jdbctest  
spring.datasource.driver-class-name = com.mysql.cj.jdbc.Driver  
spring.datasource.username = root  
spring.datasource.password = root
```
- 默认情况下，在Mybatis中，SQL语句执行时，我们并看不到SQL语句的执行日志。加入如下配置，即可查看日志:
```properties
mybatis.configuration.log-impl=org.apache.ibatis.logging.stdout.StdOutImpl
```

## 数据库连接池
- 数据库连接池是个容器，负责分配、管理数据库连接（Connection）。
- 它允许应用程序重复使用一个现有的数据库连接，而不是再重新建立一个。
- 释放空闲时间超过最大空闲时间的连接，来避免因为没有释放连接而引起的数据库连接遗漏。
- 优势：
	- 资源重用
	- 提升系统响应速度
	- 避免数据库连接遗漏
### 数据库连接池接口
	`datasource`

1. 官方（sun)提供的数据库连接池接口，由第三方组织实现此接口。
2. 功能：获取连接`Connection getConnection() throws SQLException;`
    ![[Pasted image 20250506093617.png|900]]
3. 使用Mybatis的注解，主要是来完成一些简单的增删改查功能。如果需要实现复杂的SQL功能，建议使用XML来配置映
    射语句。

### XML映射文件

1. XML映射文件的定义规则

   - XML文件名称与`Mapper`接口名称一致，并且放置在相同包下（同包同名）
   - XML文件的`namespace`属性为`Mapper`接口全限定名一致。
   - XML文件中sql语句的`id`与`Mapper`接口中的方法名一致。

   ![image](D:\Typora\res\image.png)

   ![1280X1280](D:\Typora\res\1280X1280.PNG)

   ![PixPin_2025-05-10_19-42-36](D:\Typora\res\PixPin_2025-05-10_19-42-36.png)

2. 配置XML映射文件的位置：

```properties
	// application.properties
	mybatis.mapper-locations=classpath:mapper/*.xml
```
   
