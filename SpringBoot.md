# Nginx

- location：用于定义匹配路径匹配的规则。

- ^～/api/：表示精确匹配，即只匹配以/api/开头的路径。

- rewrite：该指令用于重写匹配到的路径。

- proxy_pass：该指令用于代理转发，它将匹配到的请求转发给位于后端的指令服务器。

- 反向代理是一种网络架构，通过代理服务器为后端的服务器做代理，客户端的请求直接请求代理服务器，然后转发给后端的服务器。（安全、灵活、负载均衡）

- ```apl
  server{
  	listen 90;
  	#省略...
  	location/api/{
  	rewrite^/api/(.*）$/$1break;
  	proxy_pass http://localhost:8080;
  	}
  }
  ```

# Pieces

1. `ServletRequest`和`HttpServletRequest`

   1. `HttpServletRequest` 是 `ServletRequest` 的子接口，专门为 HTTP 协议准备，功能更强。

   2. | 对比项   | ServletRequest                                               | HttpServletRequest                                           |
      | -------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
      | 所在包   | `javax.servlet`                                              | `javax.servlet.http`                                         |
      | 类型     | 接口                                                         | 接口（集成自ServletRequest）                                 |
      | 面向协议 | 通用的Servlet请求接口，支持多种协议<br/>专门为HTTP请求设计的接口<br/>(如 HTTP、FTP、SMTP 等) | 专门为HTTP请求设计的接口                                     |
      | 功能     | 提供请求参数、输入流、属性等                                 | 提供了更多HTTP特有的方法，<br/>如获取请求方法(GET/POST）、<br/>头信息、Cookie、Session 等 |

   3. `HttpServletRequest request = (HttpServletRequest) req;`强转

   4. 我们**想用** `HttpServletRequest` 的 **更多 HTTP 方法**（如 `getMethod()`、`getHeader()`、`getSession()` 等），所以需要**强制类型转换**。

# SpringBootWeb

## Web

- 静态资源：服务器上存储的不会改变的数据，通常不会根据用户的请求而变化。比如：HTML、CSS、JS、图片、视频等（负责页面展示）
- 动态资源：服务器端根据用户请求和其他数据动态生成的，内容可能会在每次请求时都发生变化。比如：Servlet、JSP等(负责逻辑处理)Spring框架
- `B/S架构`：Browser/Server，浏览器/服务器架构模式。客户端只需浏览器，应用程序的逻辑和数据都存在服务器端。（维护方便体验一般)
- `C/S 架构`：Client/Server，客户端/服务器架构模式。需要单独开发维护客户端。（体验不错开发维护麻烦)

## Spring

- 官网: spring.io
- Spring发展到今天已经形成了一种开发生态圈，Spring提供了若干个子项目，每个项目用于完成特定的功能。

## SpringBoot

- SpringBoot可以帮助我们非常快速的构建应用程序、简化开发、提高效率。

### 入门

1. 创建springboot工程，并勾选web开发相关依赖。
2. 定义HelloController类，添加方法hello，并添加注解。

- 起步依赖：
  - spring-boot-starter-web：包含了web应用开发所需要的常见依赖
  - Spring-boot-starter-test：包含了单元测试所需要的常见依赖。
```java
@RestController //注解
// 该注解包括@ResponseBody注解
// 作用：将controller返回值直接作为响应体的数据直接响应；返回值是对象/集合->json->响应
```
- @ResponseBody注解的作用
	- 将controller方法的返回值直接写入HTTP响应体
	- 如果是对象或集合，会先转为json，再响应
	- @RestController = @Controller + @ResponseBody
### 分层解耦
#### web开发三层架构
1. `controller`：控制层，接收前端发送的请求，对请求进行处理，并响应数据。
2. `service`：业务逻辑层，处理具体的业务逻辑。
3. `dao`：数据访问层（DataAccessObject）（持久层），负责数据访问操作，包括数据的增、删、改、查。

### 分层解耦

1. 耦合：衡量软件中各个层/各个模块的依赖关联程度。
2. 内聚：软件中各个功能模块内部的功能联系
3. 软件设计原则：高内聚低耦合

1. 控制反转：InversionOfControl，简称`IOC`。对象的创建控制权由程序自身转移到外部（容器），这种思想称为控制反转。
2. 依赖注入：Dependency Injection，简称`DI`。容器为应用程序提供运行时，所依赖的资源，称之为依赖注入。
3. Bean对象：IOC容器中创建、管理的对象，称之为`Bean`。

#### IOC & DI 入门

1. 将Dao及Service层的实现类，交给Ioc容器管理
2. 为Controller 及 Service注入运行时所依赖的对象

```java
// 将该类交给IOC容器处理，负责对象的创建(控制反转)
// @Component(注意：是加在实现类上，而非接口上)
@Component

// 程序从容器中自动寻找Bean对象
@Autowired
```

#### IOC 详解

1. 要把某个对象交给IOC容器管理，需要在对应的类上加上如下注解之一：

   ![image-20250426165953440](C:\Users\30703\AppData\Roaming\Typora\typora-user-images\image-20250426165953440.png)

2. 声明bean的时候，可以通过注解的value属性指定bean的名字，如果没有指定，默认为类名首字母小写。

3. 前面声明bean的四大注解，要想生效，还需要被组件扫描注解`@ComponentScan`扫描。

4. 该注解虽然没有显式配置，但是实际上已经包含在了启动类声明注解`@SpringBootApplication`中，默认扫描的范围是启动类所在包及其子包。

DI 详解

1. 基于`@Autowired`进行依赖注入的常见方式有如下三种：

   1. 属性注入
      1. 优点：代码简洁、方便快速开发
      2. 缺点：隐藏了类之间的依赖关系、可能会破坏类的封装性
   2. 构造函数注入
      1. 优点：能清晰地看到类的依赖关系、提高了代码的安全性(`final`)。
      2. 缺点：代码繁琐、如果构造参数过多，可能会导致构造函数臃肿
      3. 注意：如果当前类中只存在一个构造函数，`@Autowired`可以省略
   3.  setter注入
      1. 优点：保持了类的封装性依赖关系更清晰
      2. 缺点：需需要额外编写setter方法，增增加了代码量

   ```java
   @RestController
   public class UserController {
   	private UserService userService;
   	@Autowired
   	public void setUserService(UserService userService）{
   		this.userService = userService;
       }
   }
   ```

   `final`：该对象被初始化后就`不能再修改`(如c++的`const`)

   `@Autowired`注解，默认是按照类型进行注入的。

   如果存在多个相同类型的bean，将会报出如下错误：
   ![image-20250426173636272](C:\Users\30703\AppData\Roaming\Typora\typora-user-images\image-20250426173636272.png)

   解决方案

   1. `@Primary`

      ```java
      @Primary
      @Service
      public class UserServiceImpl implements UserService {
      	@Override
      	public List<User> list(){
      		//省略..
      	}
      }
      ```

   2. `@Qualifier`

      ```java
      @RestController
      public class UserController{
      	@Autowired
      	@Qualifier("userServiceImpl")
      	private UserService userService;
      }
      ```

   3. `@Resource`

      ```java
      @RestController
      	public class UserController {
      	@Resource(name = "userServiceImpl")
      	private UserService userService;
      }
      ```

   `@Resource`与`@Autowired`区别
   1. `@Autowired`是`Spring`框架提供的注解，而`@Resource`是`JavaEE`规范提供的
   2. `@Autowired`默认是按照类型注入，而`@Resource`默认是按照名称注入
### 配置文件格式

	SpringBoot项目提供了多种属性配置方式(properties、yaml、yml)。
#### yaml配置文件

1. 格式：
	- 数值前边必须有空格，作为分隔符
	- 使用缩进表示层级关系，缩进时，不允许使用tab键，只能用空格
	- 缩进的空格数目不重要，只要相同层级的元素左侧对齐即可
	- `#`表示注释
2. 定义对象/map集合
```yaml
user:
  name: 张三
  age: 18
  password: 123456
```

​	3.定义数组/List/Set集合

```yaml
hobby:
  - java
  - game
  - sport
```

> 在yml格式的配置文件中，如果配置项的值是以0开头的，值需要使用`''`引起来，因为以0开头在yml中表示8进制的数据。

### START

![image-20250506210745312](C:\Users\30703\AppData\Roaming\Typora\typora-user-images\image-20250506210745312.png)

![image-20250506211620628](C:\Users\30703\AppData\Roaming\Typora\typora-user-images\image-20250506211620628.png)

#### REST

- REST（REpresentationalState Transfer），表述性状态转换，它是一种软件架构风格。

![[image-20250506211739412.png]]

![[image-20250506211914365 1.png]]

> 1.REST是风格，是约定方式，约定不是规定，可以打破。
> 2．描述功能模块通常使用复数形式（加s），表示此类资源，而非单个资源。如：users、books.．

- rest四种请求方式
  1. GET：查询
  2. POST：新增
  3. PUT：修改
  4. DELETE：删除

##### Apifox

- 介绍：Apifox是一款集成了Api文档、Api调试、ApiMock、Api测试的一体化协作平台
-  作用：接口文档管理、接口请求测试、Mock服务。 
- 官网：https://apifox.com/

##### 数据封装

- 实体类属性名和数据库表查询`返回的字段名一致`，mybatis会自动封装。

- 如果实体类属性名和数据库表查询返回的`字段名不一致`，不能自动封装。

- 手动结果映射：通过`@Results`及`@Result`进行手动结果映射

  ```java
  @Results({
              @Result(column = "create_time", property = "createTime"),
              @Result(column = "update_time", property = "updateTime")
      })
  ```

- 起别名：在SQL语句中，对不一样的列名起别名，别名和实体类属性名一样。

  ```java
  @Select("select id, name, create_time createTime, update_time updateTime from dept order by update_time desc;")
  ```

- 开启驼峰命名：如果字段名与属性名符合驼峰命名规则，mybatis会自动通过驼峰命名规则映射，

  ```yaml
  mybatis:
    configuration:
      map-underscore-to-camel-case: true
  ```

### Controller接受参数

1. 通过原始的HttpServletRequest对象获取请求参数。

   ```java
   @DeleteMapping("depts")
   public Result delete(HttpServletRequest requests) {
       String idStr = request.getParameter("id");
       int id = Integer.parseInt(idStr);
       System.out.println("根据ID删除部门：" + id);
       return Result.success();
   }
   ```

2. 通过Spring提供的`@RequestParam`注解，将请求参数绑定给方法形参

   ```java
   @DeleteMapping("depts")
   public Result delete(@RequestParam(value = "id", required = false) Integer deptId) {
   	System.out.println("根据ID删除部门：" + deptId);
   	return Result.success();
   }
   ```

   > @RequestParam注解required属性默认为true，代表该参数必须传递，如果不传递将报错。如果参数可选，可以将属性设置为false

3. 如果请求参数名与形参变量名相同，直接定义方法形参即可接收。（省略RequestParam）

   ```java
   @DeleteMapping("depts")
   public Result delete(Integer id) {
       System.out.println("根据ID删除部门：" + id);
       return Result.success();
   }
   ```


### json参数接收

- JSON格式的参数，通常会使用一个实体对象进行接收 。
- 规则：JSON数据的键名与方法形参对象的属性名相同，并需要使用`@RequestBody`注解标识。

> 一个完整的请求路径，应该是类上的 `@RequestMapping` 的value属性 + 方法上的 @RequestMapping的value属性。

1. 在插入数据之后，如何获取到主键值
   `@Options(useGeneratedKeysS = true，keyProperty="id")`

2. <foreach>动态SQL标签的作用？其中属性的含义？
   1. 作用：遍历集合/数组
      1. 属性：
         - collection：集合名称
         - item:集合遍历出来的元素/项
         - separator：每一次遍历使用的分隔符（可选）
         - open:遍历开始前拼接的片段（可选）
         - close：遍历结束后拼接的片段（可选）

### 事务管理

```java
@Transactional
```

两个常见的属性：

1. 异常回滚的属性：`rollbackFor`

   - **默认情况下，只有出现RuntimeException(运行时异常)才会回滚事务。**

   - 改为

     ```java
     //通过rollbackFor这个属性可以指定出现何种异常类型回滚事务
     @Transactional(rollbackFor = Exception.class)
     ```

2. 事务传播行为：`propagation`

   - 配置事务的传播行为的：就是当一个事务方法被另一个事务方法调用时，这个事务方法应该如何进行事务控制

   - 事务传播行为

   - | 属性值        | 含义                                                         |
     | ------------- | ------------------------------------------------------------ |
     | REQUIRED      | 【默认值】需要事务，有则加入，无则创建新事务                 |
     | REQUIRES_NEW  | 需要新事务，无论有无，总是创建新事务                         |
     | SUPPORTS      | 支持事务，有则加入，无则在无事务状态中运行                   |
     | NOT_SUPPORTED | 不支持事务，在无事务状态下运行,如果当前存在已有事务,则挂起当前事务 |
     | MANDATORY     | 必须有事务，否则抛异常                                       |
     | NEVER         | 必须没事务，否则抛异常                                       |
     | …             |                                                              |

   - 对于这些事务传播行为，我们只需要关注以下两个就可以了：

     1. REQUIRED（默认值）
     2. REQUIRES_NEW

   - ```java
     @Transactional(propagation = Propagation.REQUIRES_NEW)
     ```

   - **REQUIRED：**大部分情况下都是用该传播行为即可。

   - **REQUIRES_NEW：**当我们不希望事务之间相互影响时，可以使用该传播行为。比如：下订单前需要记录日志，不论订单保存成功与否，都需要保证日志记录能够记录成功。

### 服务器端获取文件上传

> 在新增员工的时候，要上传员工的头像，此时就会涉及到文件上传的功能。在进行文件上传时，我们点击加号或者是点击图片，就可以选择手机或者是电脑本地的图片文件了。当我们选择了某一个图片文件之后，这个文件就会上传到服务器，从而完成文件上传的操作。

#### 前端页面

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>上传文件</title>
</head>
<body>

    <form action="/upload" method="post" enctype="multipart/form-data">
        姓名: <input type="text" name="name"><br>
        年龄: <input type="text" name="age"><br>
        头像: <input type="file" name="file"><br>
        <input type="submit" value="提交">
    </form>

</body>
</html>
```

- 上传文件的原始form表单，要求表单必须具备以下三点（上传文件页面三要素）：
  1. 表单必须有file域，用于选择要上传的文件：如果想要选择本地电脑上的文件，必须要有文件上传的表单项，所以必须要有input标签并且type设置为file，表明这是一个文件上传的表单项，才能够选择要上传的文件
  2. 表单提交方式必须为POST：通常上传的文件会比较大，所以需要使用 POST 提交方式
  3. 表单的编码类型enctype必须要设置为：multipart/form-data：普通默认的编码格式是不适合传输大型的二进制数据的，所以在文件上传时，表单的编码格式必须设置为multipart/form-data

#### 后端实现

> Spring中提供了一个API：MultipartFile，使用这个API就可以来接收到上传的文件

1. **MultipartFile 常见方法：** 
   - `String  getOriginalFilename();`  //获取原始文件名
   - `void  transferTo(File dest); `   //将接收的文件转存到磁盘文件中
   - `long  getSize();`   //获取文件的大小，单位：字节
   - `byte[]  getBytes(); `   //获取文件内容的字节数组
   - `InputStream  getInputStream();`    //获取接收到的文件内容的输入流

#### 问题

如果直接存储在服务器的磁盘目录中，存在以下缺点：

- 不安全：磁盘如果损坏，所有的文件就会丢失
- 容量有限：如果存储大量的图片，磁盘空间有限(磁盘不可能无限制扩容)
- 无法直接访问

为了解决上述问题呢，通常有两种解决方案：

- 自己搭建存储服务器，如：fastDFS 、MinIO
- 使用现成的云服务，如：阿里云，腾讯云，华为云



## Exception

<img src="D:\refines\refines\image.png" alt="image" style="zoom:50%;" />

当我们没有做任何的异常处理时，我们三层架构处理异常的方案：

- Mapper接口在操作数据库的时候出错了，此时异常会往上抛(谁调用Mapper就抛给谁)，会抛给service。 
- service 中也存在异常了，会抛给controller。
- 而在controller当中，我们也没有做任何的异常处理，所以最终异常会再往上抛。最终抛给框架之后，框架就会返回一个JSON格式的数据，里面封装的就是错误的信息，但是框架返回的JSON格式的数据并不符合我们的开发规范。

### solutions

1. **方案一：在所有Controller的所有方法中进行try…catch处理**
   - 缺点：代码臃肿
2. **方案二：全局异常处理器**
   - 好处：简单、优雅（推荐)
   - <img src="D:\refines\refines\image2.png" alt="image2" style="zoom:50%;" />

#### 全局异常处理器

- 定义全局异常处理器非常简单，就是定义一个类，在类上加上一个注解@RestControllerAdvice，加上这个注解就代表我们定义了一个全局异常处理器。
- 在全局异常处理器当中，需要定义一个方法来捕获异常，在这个方法上需要加上注解@ExceptionHandler。通过@ExceptionHandler注解当中的value属性来指定我们要捕获的是哪一类型的异常。

```java
@RestControllerAdvice
public class GlobalExceptionHandler {
    
    //处理异常
    @ExceptionHandler
    public Result ex(Exception e){//方法形参中指定能够处理的异常类型
        e.printStackTrace();//打印堆栈中的异常信息
        //捕获到异常之后，响应一个标准的Result
        return Result.error("对不起,操作失败,请联系管理员");
    }
    
}
```

> `@RestControllerAdvice` = `@ControllerAdvice` + `@ResponseBody`
>
> 处理异常的方法返回值会转换为json后再响应给前端

> 以上就是全局异常处理器的使用，主要涉及到两个注解：
>
> - `@RestControllerAdvice`  //表示当前类为全局异常处理器
> - `@ExceptionHandler`  //指定可以捕获哪种类型的异常进行处理



> 如果查询的记录往Map中封装，可以通过@MapKey注解指定返回的map中的唯一标识是那个字段。【也可以不指定】

**case流程控制函数：**

- 语法一：case when cond1 then res1 [ when cond2 then res2 ] else res end ;
- 含义：如果 cond1 成立， 取 res1。  如果 cond2 成立，取 res2。 如果前面的条件都不成立，则取 res。

- 语法二（仅适用于等值匹配）：case expr when val1 then res1 [ when val2 then res2 ] else res end ;
- 含义：如果 expr 的值为 val1 ， 取 res1。  如果  expr 的值为 val2 ，取 res2。 如果前面的条件都不成立，则取 res。

## 登录校验

前面在讲解HTTP协议的时候，我们提到HTTP协议是无状态协议。什么又是无状态的协议？

​		所谓无状态，指的是`每一次请求都是独立`的，下一次请求并不会携带上一次请求的数据。而浏览器与服务器之间进行交互，基于HTTP协议也就意味着现在我们通过浏览器来访问了登陆这个接口，实现了登陆的操作，接下来我们在执行其他业务操作时，服务器也并不知道这个员工到底登陆了没有。因为HTTP协议是无状态的，两次请求之间是独立的，所以是无法判断这个员工到底登陆了没有。

![dd737974-52c9-4a6d-84e5-4ea6075d4a97](D:\refines\refines\dd737974-52c9-4a6d-84e5-4ea6075d4a97.png)

### 如何实现

1. 在员工登录成功后，需要将用户`登录成功的信息存起来`，记录用户已经登录成功的标记。
2. 在浏览器发起请求时，需要`在服务端进行统一拦截`，拦截后进行登录校验。
3. 为了简化这块操作，我们可以使用一种技术：`统一拦截技术`。
   1. 通过统一拦截的技术，我们可以来`拦截浏览器发送过来的所有的请求`，拦截到这个请求之后，就可以通过请求来`获取之前所存入的登录标记`，在获取到登录标记且标记为登录成功，就说明员工已经登录了。如果已经登录，我们就直接放行(意思就是可以访问正常的业务接口了)。

会涉及到web开发中的两个技术：

1. 会话技术：用户登录成功之后，在后续的每一次请求中，都可以获取到该标记。
2. 统一拦截技术：过滤器`Filter`、拦截器`Interceptor`

### 会话技术

- 在web开发当中，会话指的就是浏览器与服务器之间的一次连接，我们就称为一次会话。
- 在用户打开浏览器第一次访问服务器的时候，这个会话就建立了，直到有任何一方断开连接，此时会话就结束了。在一次会话当中，是可以包含多次请求和响应的。

> 需要注意的是：会话是和浏览器关联的，当有三个浏览器客户端和服务器建立了连接时，就会有三个会话。`同一个浏览器在未关闭之前`请求了多次服务器，这多次请求是`属于同一个会话`。比如：1、2、3这三个请求都是属于同一个会话。当我们`关闭浏览器之后`，这次`会话就结束`了。而如果我们是直接把web服务器关了，那么所有的会话就都结束了。

![85941777-60c7-4562-909d-73061f3a44fb](D:\refines\refines\85941777-60c7-4562-909d-73061f3a44fb.png)

#### 会话跟踪

- 一种`维护浏览器状态`的方法，服务器需要`识别多次请求是否来自于同一浏览器`，以便在`同一次会话的多次请求`间`共享数据`。
- 由于HTTP是无状态协议，在后面请求中怎么拿到前一次请求生成的数据呢？此时就需要在一次会话的多次请求之间进行数据共享
- 会话跟踪技术有两种：
  - Cookie（客户端会话跟踪技术）：数据存储在客户端浏览器当中
  - Session（服务端会话跟踪技术）：数据存储在储在服务端
  - 令牌技术

##### Cookie

- cookie 是`客户端会话跟踪技术`，它是`存储在客户端浏览器`的，我们使用 cookie 来跟踪会话，我们就可以在浏览器第一次发起请求来请求服务器的时候，我们在服务器端来设置一个cookie。
- 比如第一次请求了登录接口，登录接口执行完成之后，我们就可以设置一个cookie，在 cookie 当中我们就可以来存储用户相关的一些数据信息。比如我可以在 cookie 当中来存储当前登录用户的用户名，用户的ID。
- `服务器端`在`给客户端在响应数据`的时候，会**`自动`**的将 cookie 响应给浏览器，浏览器接收到响应回来的 cookie 之后，会**自动**的将 cookie 的值`存储在浏览器本地`。接下来在后续的每一次请求当中，都会将浏览器本地所存储的 cookie `**自动**地携带到服务端`。

![c2b69efe-7782-49cc-a658-b92c26ae0a54](D:\refines\refines\c2b69efe-7782-49cc-a658-b92c26ae0a54.png)

​		接下来在服务端我们就可以获取到 cookie 的值。我们可以去判断一下这个 cookie 的值是否存在，如果不存在这个cookie，就说明客户端之前是没有访问登录接口的；如果存在 cookie 的值，就说明客户端之前已经登录完成了。这样我们就可以基于 cookie 在同一次会话的不同请求之间来共享数据。

###### **为什么是自动化的**

​		是因为 cookie 它是 `HTTP `协议当中所支持的技术，而各大浏览器厂商都支持了这一标准。在 HTTP 协议官方给我们提供了一个响应头和请求头：

- 响应头 `Set-Cookie` ：设置Cookie数据的
- 请求头 `Cookie`：携带Cookie数据的

![a4ef8e51-6944-49f7-81c1-adb9587a9b97](D:\refines\refines\a4ef8e51-6944-49f7-81c1-adb9587a9b97.png)

###### 代码样例

```java
@Slf4j
@RestController
public class SessionController {

    //设置Cookie
    @GetMapping("/c1")
    public Result cookie1(HttpServletResponse response){
        response.addCookie(new Cookie("login_username","itheima")); //设置Cookie/响应Cookie
        return Result.success();
    }
        
    //获取Cookie
    @GetMapping("/c2")
    public Result cookie2(HttpServletRequest request){
        Cookie[] cookies = request.getCookies();
        for (Cookie cookie : cookies) {
            if(cookie.getName().equals("login_username")){
                System.out.println("login_username: "+cookie.getValue()); //输出name为login_username的cookie
            }
        }
        return Result.success();
    }
}    
```

###### **优缺点：**

- 优点：HTTP协议中支持的技术（像Set-Cookie 响应头的解析以及 Cookie 请求头数据的携带，都是浏览器`自动进行`的，是无需我们手动操作的）
- 缺点：
  - 移动端APP(Android、IOS)中`无法使用Cookie`
  - 不安全，用户可以自己`禁用Cookie`
  - Cookie`不能跨域`
    - 跨域：
      - ![4bfb108e-d80f-43a7-8fb3-8a0718825dbc](D:\refines\refines\4bfb108e-d80f-43a7-8fb3-8a0718825dbc.png)
      - 现在的项目，大部分都是`前后端分离`的，前后端最终也会`分开部署`，前端部署在服务器 192.168.150.200 上，端口 80，后端部署在 192.168.150.100上，端口 8080。`端口号不同`
      - 区分跨域的维度（三个维度有任何一个维度不同，那就是跨域操作）：
        - 协议
        - IP/协议
        - 端口
      - 举例：
        - http://192.168.150.200/login.html ----------> https://192.168.150.200/login                    [协议不同，跨域]
        - http://192.168.150.200/login.html ----------> http://192.168.150.100/login                     [IP不同，跨域]
        - http://192.168.150.200/login.html ----------> http://192.168.150.200:8080/login             [端口不同，跨域]
        - http://192.168.150.200/login.html ----------> http://192.168.150.200/login                     [不跨域]  

##### Session

1. 获取Session
   - ![842ea416-59af-47ad-bee1-d17d85741ca3](D:\refines\refines\842ea416-59af-47ad-bee1-d17d85741ca3.png)
   - 如果我们现在要`基于 Session `来进行`会话跟踪`，浏览器在`第一次请求服务器`的时候，我们就可以直接在服务器当中来`获取到会话对象Session`。如果是第一次请求Session ，会话对象是不存在的，这个时候服务器会`自动的创建一个会话对象Session` 。而每一个会话对象Session ，它都有一个`ID`（示意图中Session后面括号中的1，就表示ID），我们称之为 `Session 的ID`。
2. 响应cookie
   - ![0cd81912-3881-4998-9e43-bff4f04c204e](D:\refines\refines\0cd81912-3881-4998-9e43-bff4f04c204e.png)
   - 接下来，服务器端在`给浏览器响应数据`的时候，它会将 `Session 的 ID` `通过 Cookie 响应`给浏览器。其实在响应头当中增加了一个 Set-Cookie 响应头。这个  Set-Cookie  响应头对应的值是不是cookie？ cookie 的名字是固定的 `JSESSIONID` 代表的服务器端会话对象 `Session 的 ID`。浏览器会自动识别这个响应头，然后自动将Cookie存储在浏览器本地。
3. 查找Session
   - ![611f8b64-0207-43a2-a309-4466450c4f3e](D:\refines\refines\611f8b64-0207-43a2-a309-4466450c4f3e.png)
   - 接下来，在后续的`每一次请求`当中，都会`将 Cookie 的数据获取`出来，并且`携带到服务端`。接下来服务器拿到JSESSIONID这个 Cookie 的值，也就是 Session 的ID。拿到 ID 之后，就会从众多的 Session 当中来找到当前请求对应的会话对象Session。

###### 代码样例

```java
@Slf4j
@RestController
public class SessionController {

    @GetMapping("/s1")
    public Result session1(HttpSession session){
        log.info("HttpSession-s1: {}", session.hashCode());

        session.setAttribute("loginUser", "tom"); //往session中存储数据
        return Result.success();
    }

    @GetMapping("/s2")
    public Result session2(HttpServletRequest request){
        HttpSession session = request.getSession();
        log.info("HttpSession-s2: {}", session.hashCode());

        Object loginUser = session.getAttribute("loginUser"); //从session中获取数据
        log.info("loginUser: {}", loginUser);
        return Result.success(loginUser);
    }
}
```

###### **优缺点**

- 优点：Session是存储在服务端的，安全
- 缺点：
  - `服务器集群环境`下`无法直接使用`Session
  - `移动端`APP(Android、IOS)中无法使用Cookie
  - 用户可以自己`禁用Cookie`
  - Cookie`不能跨域`

> `PS：Session 底层是基于Cookie实现的会话跟踪，如果Cookie不可用，则该方案，也就失效了。`

###### 服务器集群

- 在现在的企业项目开发当中，最终部署的时候都是以`集群的形式`来进行部署，也就是同一个项目它会部署多份。比如这个项目我们现在就部署了 3 份。
- 而用户在访问的时候，到底访问这三台其中的哪一台？其实用户在访问的时候，他会`访问一台前置的服务器`，我们叫`负载均衡服务器`，我们在后面项目当中会详细讲解。目前大家先有一个印象负载均衡服务器，它的作用就是`将前端发起的请求均匀的分发给后面的这三台服务器`。
- ![4895a698-6478-4849-bb37-0de621ec5184](D:\refines\refines\4895a698-6478-4849-bb37-0de621ec5184.png)
- 此时假如我们通过 session 来进行会话跟踪，可能就会存在这样一个问题。用户打开浏览器要进行登录操作，此时会发起登录请求。登录请求到达负载均衡服务器，将这个请求转给了第一台 Tomcat 服务器。
- Tomcat 服务器接收到请求之后，要获取到会话对象session。获取到会话对象 session 之后，要给浏览器响应数据，最终在给浏览器响应数据的时候，就会携带这么一个 cookie 的名字，就是 JSESSIONID ，下一次再请求的时候，是不是又会将 Cookie 携带到服务端？
- 好。此时假如又执行了一次查询操作，要查询部门的数据。这次请求到达负载均衡服务器之后，负载均衡服务器将这次请求转给了第二台 Tomcat 服务器，此时他就要到第二台 Tomcat 服务器当中。根据JSESSIONID 也就是对应的 session 的 ID 值，要找对应的 session 会话对象。
- 我想请问在第二台服务器当中有没有这个ID的会话对象 Session， 是没有的。此时是不是就出现问题了？我同一个浏览器发起了 2 次请求，结果获取到的不是同一个会话对象，这就是Session这种会话跟踪方案它的缺点，在服务器集群环境下无法直接使用Session。

#####  令牌技术

- 就是一个用户身份的标识，看似很高大上，很神秘，其实本质就是一个字符串。
- 如果通过令牌技术来`跟踪会话`，我们就可以在浏览器发起请求。在`请求登录接口的时候`，如果登录成功，我就可以`生成一个令牌`，令牌就是用户的`合法身份凭证`。接下来我在响应数据的时候，我就可以`直接将令牌响应给前端`。
- 接下来我们在前端程序当中`接收到令牌`之后，就需要将这个`令牌存储起来`。这个存储可以`存储在 cookie` 当中，也可以存储在其他的存储空间(比如：localStorage)当中。
- 接下来，在后续的`每一次请求`当中，都需要`将令牌携带到服务端`。携带到服务端之后，接下来我们就需要来`校验令牌的有效性`。如果令牌是有效的，就说明用户已经执行了登录操作，如果令牌是无效的，就说明用户之前并未执行登录操作。
- 此时，如果是在同一次会话的多次请求之间，我们想共享数据，我们就可以将共享的数据存储在令牌当中就可以了。

###### **优缺点**

- 优点：
  - `支持PC端、移动端`
  - `解决集群`环境下的认证问题
  - `减轻`服务器的`存储压力`（无需在服务器端存储）
- 缺点：`需要自己实现`（包括令牌的生成、令牌的传递、令牌的校验）

> **针对于这三种方案，现在企业开发当中使用的`最多的`就是第三种`令牌技术`进行会话跟踪。而前面的这两种传统的方案，现在企业项目开发当中已经很少使用了。所以在我们的课程当中，我们也将会采用令牌技术来解决案例项目当中的会话跟踪问题。**

##### JWT令牌

###### 介绍

- JWT全称 JSON Web Token  （官网：https://jwt.io/），定义了一种简洁的、自包含的格式，用于在通信双方以`json数据格式`安全的传输信息。由于数字签名的存在，这些信息是可靠的。
  - 简洁：是指jwt就是一个简单的字符串。可以在请求参数或者是请求头当中直接传递。
  - 自包含：指的是jwt令牌，看似是一个随机的字符串，但是我们是可以根据自身的需求在jwt令牌中存储自定义的数据内容。如：可以直接在jwt令牌中存储用户的相关信息。
  - 简单来讲，jwt就是将原始的json数据格式进行了安全的封装，这样就可以直接基于jwt在通信双方安全的进行信息传输了。

###### 组成

- JWT令牌由三个部分组成，三个部分之间使用英文的点来分割
  1. `Header`(头）， 记录令牌类型、签名算法等。 例如：{"alg":"HS256","type":"JWT"}
  2. `Payload`(有效载荷），携带一些自定义信息、默认信息等。 例如：{"id":"1","username":"Tom"}
  3. `Signature`(签名），防止Token被篡改、确保安全性。将header、payload，并加入指定秘钥，通过指定签名算法计算而来。

> `签名`的目的就是为了`防jwt令牌被篡改`，而正是因为jwt令牌最后一个部分数字签名的存在，所以整个jwt 令牌是非常`安全可靠`的。一旦jwt令牌当中任何一个部分、任何一个字符被篡改了，整个令牌在校验的时候都会失败，所以它是非常安全可靠的。

![JWT](D:\refines\refines\JWT.png)

###### 格式转换

- 其实在生成JWT令牌时，会对JSON格式的数据进行一次编码：进行`base64编码`
- Base64：是一种基于`64`个`可打印的字符`来表示`二进制数据`的`编码方式`。既然能编码，那也就意味着也能解码。所使用的64个字符分别是A到Z、a到z、 0- 9，一个加号，一个斜杠，加起来就是64个字符。任何数据经过base64编码之后，最终就会通过这64个字符来表示。当然还有一个符号，那就是等号。等号它是一个补位的符号
- 需要注意的是Base64是`编码方式`，而`不是加密方式`。

###### 生成和校验

1. 引入JWT的依赖：

   ```xml
   <!-- JWT依赖-->
   <dependency>
       <groupId>io.jsonwebtoken</groupId>
       <artifactId>jjwt</artifactId>
       <version>0.9.1</version>
   </dependency>
   ```

   在引入完JWT来赖后，就可以调用工具包中提供的API来完成JWT令牌的生成和校验。工具类：`Jwts`

2. 生成JWT的实现

   ```java
   @Test
   public void testGenJwt() {
       Map<String, Object> claims = new HashMap<>();
       claims.put("id", 10);
       claims.put("username", "itheima");
   
       String jwt = Jwts.builder().signWith(SignatureAlgorithm.HS256, "aXRjYXN0")
           .addClaims(claims)
           .setExpiration(new Date(System.currentTimeMillis() + 12 * 3600 * 1000))
           .compact();
   
       System.out.println(jwt);
       // 输出的结果就是生成的JWT令牌,，通过英文的点分割对三个部分进行分割
   }
   ```

   - 第一部分解析出来，看到JSON格式的原始数据，所使用的签名算法为HS256。
   - 第二个部分是我们自定义的数据，之前我们自定义的数据就是id，还有一个exp代表的是我们所设置的过期时间。
   - 第三部分：由于前两个部分是base64编码，所以是可以直接解码出来。但最后一个部分并不是base64编码，是经过签名算法计算出来的，所以最后一个部分是不会解析的。

###### 登录时下发令牌

1. 生成令牌
   - 在登录成功之后来生成一个JWT令牌，并且把这个令牌直接返回给前端
2. 校验令牌
   - 拦截前端请求，从请求中获取到令牌，对令牌进行解析校验
3. 实现
   1. static通常用于工具类方法，比如专门处理 JWT 的 `JwtUtils` 类，里面的方法常常是 `static` 的，方便全局调用。
   2. `compact()` 是用于**生成最终的 JWT 字符串**，也就是编码签名并将所有部分（头部、载荷、签名）组合成一个字符串。
   3. `.parseClaimsJws(jwt)` 会解析传入的 JWT 字符串，并验证签名。
   4. `.getBody()` 表示获取 JWT 的**载荷部分（payload）**，也就是你真正存储的数据内容，如用户名、角色、过期时间等。



##### 过滤器filter

- Filter表示过滤器，是 JavaWeb三大组件(Servlet、Filter、Listener)之一。
- 过滤器可以把`对资源的请求拦截`下来，从而实现一些特殊的功能
  - 使用了过滤器之后，要想访问web服务器上的资源，必须`先经过滤器`，过滤器`处理完毕`之后，`才可以访问`对应的资源。
- 过滤器一般完成一些通用的操作，比如：登录校验、统一编码处理、敏感字符处理等。

![filter1](D:\refines\refines\filter1.png)

基本操作

- 第1步，定义过滤器 ：1.定义一个类，实现 Filter 接口，并重写其所有方法。

   - ```java
     public class DemoFilter implements Filter {
         //初始化方法, web服务器启动, 创建Filter实例时调用, 只调用一次
         public void init(FilterConfig filterConfig) throws ServletException {
             System.out.println("init ...");
         }
     
         //拦截到请求时,调用该方法,可以调用多次
         public void doFilter(ServletRequest servletRequest, ServletResponse servletResponse, FilterChain chain) throws IOException, ServletException {
             System.out.println("拦截到了请求...");
         }
     
         //销毁方法, web服务器关闭时调用, 只调用一次
         public void destroy() {
             System.out.println("destroy ... ");
         }
     }
     ```

   - > - init方法：过滤器的初始化方法。在web服务器启动的时候会自动的创建Filter过滤器对象，在创建过滤器对象的时候会自动调用init初始化方法，这个方法只会被调用一次。
     > - doFilter方法：这个方法是在每一次拦截到请求之后都会被调用，所以这个方法是会被调用多次的，每拦截到一次请求就会调用一次doFilter()方法。
     > - destroy方法： 是销毁的方法。当我们关闭服务器的时候，它会自动的调用销毁方法destroy，而这个销毁方法也只会被调用一次。

- 第2步，配置过滤器：Filter类上加 `@WebFilter` 注解，配置拦截资源的路径。引导类上加 `@ServletComponentScan` 开启Servlet组件支持。

   - 在定义完Filter之后，Filter其实并不会生效，还需要完成Filter的配置，Filter的配置非常简单，只需要在Filter类上添加一个注解：`@WebFilter`，并指定属性`urlPatterns`，通过这个属性指定过滤器要拦截哪些请求

   - ```java
     @WebFilter(urlPatterns = "/*") //配置过滤器要拦截的请求路径（ /* 表示拦截浏览器的所有请求 ）
     public class DemoFilter implements Filter {
         //初始化方法, web服务器启动, 创建Filter实例时调用, 只调用一次
         public void init(FilterConfig filterConfig) throws ServletException {
             System.out.println("init ...");
         }
     
         //拦截到请求时,调用该方法,可以调用多次
         public void doFilter(ServletRequest servletRequest, ServletResponse servletResponse, FilterChain chain) throws IOException, ServletException {
             System.out.println("拦截到了请求...");
         }
     
         //销毁方法, web服务器关闭时调用, 只调用一次
         public void destroy() {
             System.out.println("destroy ... ");
         }
     }
     ```

   - 当我们在Filter类上面加了@WebFilter注解之后，接下来我们还需要在启动类上面加上一个注解`@ServletComponentScan`，通过这个`@ServletComponentScan`注解来开启SpringBoot项目对于Servlet组件的支持。

   - ```java
     @ServletComponentScan //开启对Servlet组件的支持
     @SpringBootApplication
     public class TliasManagementApplication {
         public static void main(String[] args) {
             SpringApplication.run(TliasManagementApplication.class, args);
         }
     }
     ```

   - > **注意事项：**在过滤器Filter中，如果不执行放行操作，将无法访问后面的资源。 放行操作：`chain.doFilter(request, response);`

   <img src="D:\refines\refines\filter2.png" alt="filter2" style="zoom: 67%;" />



1. 获取请求url
2. 判断请求url中是否包含login，如果包含，说明是登录操作，放行
3. 获取请求头中的令牌（token）
4. 判断令牌是否存在，如果不存在，响应 401
5. 解析token，如果解析失败，响应 401
6. 放行

1. `FilterChain`class:  
   1. `FilterChain` 对象内部保存的是 **一组已注册的 Filter 列表**，以及一个指针（索引）来指示当前应该调用哪个过滤器。
   2. 调用 `chain.doFilter()` 时，**实际上是由 `FilterChain` 自己调用下一个 Filter 的 `doFilter()` 方法**，从而形成“链式传递”。

###### 执行流程

![filter3](D:\refines\refines\filter3.png)

​		过滤器当中我们`拦截到了请求之后`，如果`希望继续访问`后面的web资源，就要执行放行操作，`放行就是调用 FilterChain对象`当中的`doFilter()`方法，在调用doFilter()这个方法之前所编写的代码`属于放行之前的逻辑`。

​		在`放行后`访问完 web 资源之后还会`回到过滤器`当中，回到过滤器之后如有需求还可以执行放行之后的逻辑，放行之后的逻辑我们`写在doFilter()这行代码之后`。

###### 拦截路径

| 拦截路径     | urlPatterns值 | 含义                               |
| ------------ | ------------- | ---------------------------------- |
| 拦截具体路径 | /login        | 只有访问 /login 路径时，才会被拦截 |
| 目录拦截     | /emps/*       | 访问/emps下的所有资源，都会被拦截  |
| 拦截所有     | /*            | 访问所有资源，都会被拦截           |

###### 过滤器链

![filter4](D:\refines\refines\filter4.png)

- 比如：在我们web服务器当中，定义了两个过滤器，这两个过滤器就形成了一个过滤器链。
- 而这个链上的过滤器在执行的时候会`一个一个的执行`，会先执行第一个Filter，放行之后再来执行第二个Filter，如果执行到了`最后一个过滤器放行`之后，`才会访问对应的web资源`。
- 访问完web资源之后，按照我们刚才所介绍的过滤器的执行流程，还会回到过滤器当中来执行过滤器放行后的逻辑，而在`执行放行后的逻辑`的时候，`顺序是反着`的。`先要执行过滤器2`放行之后的逻辑，`再来执行过滤器1`放行之后的逻辑，最后在给浏览器响应数据。

> 过滤器链上过滤器的执行顺序：注解配置的Filter，优先级是按照过滤器类名（字符串）的自然排序。 比如：
>
> - AbcFilter
> - DemoFilter
>
> 这两个过滤器来说，AbcFilter 会先执行，DemoFilter会后执行。

##### 拦截器(用的比过滤器多)

- 是一种`动态拦截`方法调用的机制，类似于过滤器。
- 拦截器是`Spring框架中提供`的，用来动态拦截控制器方法的执行，`需要交给IOC容器管理`。
- 拦截器的作用：拦截请求，在`指定方法调用前后`，根据业务需要执行预先设定的代码。

![Interceptor1](D:\refines\refines\Interceptor1.png)

- 在拦截器当中，我们通常也是做一些`通用性`的操作，比如：我们可以通过拦截器来`拦截前端发起的请求`，将`登录校验的逻辑`全部编写在拦截器当中。在校验的过程当中，如发现用户登录了(携带JWT令牌且是合法令牌)，就可以直接放行，去访问spring当中的资源。如果校验时发现并没有登录或是非法令牌，就可以直接给前端响应未登录的错误信息。

###### 基本使用

1. 定义拦截器

   ```java
   //自定义拦截器
   @Component
   public class DemoInterceptor implements HandlerInterceptor {
       //目标资源方法执行前执行。 返回true：放行    返回false：不放行
       @Override
       public boolean preHandle(HttpServletRequest request, HttpServletResponse response, Object handler) throws Exception {
           System.out.println("preHandle .... ");
           
           return true; //true表示放行
       }
   
       //目标资源方法执行后执行
       @Override
       public void postHandle(HttpServletRequest request, HttpServletResponse response, Object handler, ModelAndView modelAndView) throws Exception {
           System.out.println("postHandle ... ");
       }
   
       //视图渲染完毕后执行，最后执行
       @Override
       public void afterCompletion(HttpServletRequest request, HttpServletResponse response, Object handler, Exception ex) throws Exception {
           System.out.println("afterCompletion .... ");
       }
   }
   ```

   - `preHandle`方法：目标资源方法执行前执行。 返回true：放行    返回false：不放行
   - `postHandle`方法：目标资源方法执行后执行
   - `afterCompletion`方法：视图渲染完毕后执行，最后执行

2. 注册配置拦截器

   在 `org.example`下创建一个包，然后创建一个配置类 `WebConfig`， 实现 `WebMvcConfigurer` 接口，并重写 `addInterceptors` 方法

   ```java
   @Configuration  
   public class WebConfig implements WebMvcConfigurer {
   
       //自定义的拦截器对象
       @Autowired
       private DemoInterceptor demoInterceptor;
   
       
       @Override
       public void addInterceptors(InterceptorRegistry registry) {
          //注册自定义拦截器对象
           registry.addInterceptor(demoInterceptor).addPathPatterns("/**");//设置拦截器拦截的请求路径（ /** 表示拦截所有请求）
       }
   }
   ```

###### 详解

1. 拦截器的拦截路径配置

   1. 在注册配置拦截器的时候，我们要指定拦截器的拦截路径，通过`addPathPatterns("要拦截路径")`方法，就可以指定要拦截哪些资源。

   2. 在入门程序中我们配置的是`/**`，表示拦截所有资源，而在配置拦截器时，不仅可以指定要拦截哪些资源，还可以指定不拦截哪些资源，只需要调用`excludePathPatterns("不拦截路径")`方法，指定哪些资源不需要拦截。

   3. | 拦截路径  | 含义                 | 举例                                                |
      | --------- | -------------------- | --------------------------------------------------- |
      | /*        | 一级路径             | 能匹配/depts，/emps，/login，不能匹配 /depts/1      |
      | /**       | 任意级路径           | 能匹配/depts，/depts/1，/depts/1/2                  |
      | /depts/*  | /depts下的一级路径   | 能匹配/depts/1，不能匹配/depts/1/2，/depts          |
      | /depts/** | /depts下的任意级路径 | 能匹配/depts，/depts/1，/depts/1/2，不能匹配/emps/1 |

2. 拦截器的执行流程

   - ![Interceptor2](D:\refines\refines\Interceptor2.png)
   - 当我们打开浏览器来访问部署在web服务器当中的web应用时，此时我们所定义的`过滤器会拦截到这次请求`。拦截到这次请求之后，它会`先执行放行前的逻辑`，然后`再执行放行操作`。而由于我们当前是基于`springboot`开发的，所以放行之后是进入到了spring的环境当中，也就是要来访问我们所定义的controller当中的接口方法。
   - `Tomcat`并`不识别`所编写的`Controller`程序，但是它`识别Servlet`程序，所以在Spring的Web环境中提供了一个非常`核心的Servlet`：`DispatcherServlet`（前端控制器），`所有请求都会先进行`到`DispatcherServlet`，`再`将请求`转给Controller`。
   - 当我们定义了`拦截器`后，会在`执行Controller的方法之前`，请求被拦截器`拦截住`。执行`preHandle()`方法，这个方法执行完成后需要`返回一个布尔`类型的值，如果返回`true`，就表示`放行`本次操作，才会`继续访问controller`中的方法；如果返回`false`，则`不会放行`（controller中的方法也不会执行）。
   - 在`controller`当中的方法执行完毕之后，再回过来执行`postHandle()`这个方法以及`afterCompletion()` 方法，然后再返回给`DispatcherServlet`，最终再来执行过滤器当中`放行后`的这一部分逻辑的逻辑。执行完毕之后，最终给浏览器响应数据。

##### filter 和 interceptor 的区别

- **`接口规范`不同：过滤器需要实现`Filter`接口，而拦截器需要实现`HandlerInterceptor`接口。**
- **`拦截范围`不同：过滤器Filter会`拦截所有`的资源，而Interceptor`只会拦截Spring环境中`的资源。**

## AOP

- AOP：`Aspect Oriented Programming`（`面向切面`编程、面向方面编程），其实说白了，面向切面编程就是面向特定方法编程。 

### 优势

1. 减少重复代码：不需要在业务方法中定义大量的重复性的代码，只需要将`重复性的代码抽取`到AOP程序中即可。
2. 代码无侵入：在基于AOP实现这些业务功能时，对原有的业务代码是`没有任何侵入`的，不需要修改任何的业务代码。
3. 提高开发效率
4. 维护方便

> AOP是一种思想，而在Spring框架中，对这种思想进行了实现，那我们要学习的就是Spring AOP。

### 常用场景

- 记录系统的操作日志
- 权限控制
- 事务管理：我们前面所讲解的Spring`事务管理`，`底层`其实也是`通过AOP`来实现的，只要添加`@Transactional`注解之后，AOP程序自动会在原始方法运行前先来开启事务，在原始方法运行完毕之后提交或回滚事务

### 核心概念

1. **连接点：`JoinPoint`**，可以被AOP控制的方法（暗含方法执行时的相关信息）
   - 连接点指的是`可以被aop控制的方法`。例如：入门程序当中所有的业务方法都是可以被aop控制的方法。
   - 在SpringAOP提供的`JoinPoint当中`，封装了连接点方法在`执行时的相关信息`。（后面会有具体的讲解）
2. **通知：`Advice`**，指哪些重复的逻辑，也就是`共性功能`（最终体现为一个方法）
   - 在入门程序中是需要统计各个业务方法的执行耗时的，此时我们就需要在这些业务方法运行开始之前，先记录这个方法运行的开始时间，在每一个业务方法运行结束的时候，再来记录这个方法运行的结束时间。
   - 是在AOP面向切面编程当中，我们只需要将这部分重复的代码逻辑`抽取出来单独定义`。抽取出来的这一部分重复的逻辑，也就是共性的功能。
3. **切入点：`PointCut`**，`匹配连接点`的`条件`，通知仅会在切入点方法执行时被应用。
   - 在通知当中，我们所定义的共性功能到底要应用在哪些方法上？此时就涉及到了切入点pointcut概念。切入点指的是匹配连接点的条件。`通知`仅会在`切入点方法运行`时才会被应用。
   - 在aop的开发当中，我们通常会通过`一个切入点表达式`来`描述切入点`(后面会有详解)。
4. **切面：`Aspect`**，描述通知与切入点的`对应关系`（通知+切入点）
   - 当`通知和切入点结合`在一起，就形成了`一个切面`。通过切面就能够描述当前aop程序需要针对于哪个原始方法，在什么时候执行什么样的操作。
   - 而切面所在的类，称之为切面类（被`@Aspect`注解标识的类）。
5. **目标对象：`Target`**，通知所应用的对象
   - 目标对象指的就是`通知所应用的对象`，我们就称之为`目标对象`。

> Spring的AOP`底层`是`基于动态代理`技术来实现的，也就是说在程序运行的时候，会自动的`基于动态代理`技术为目标对象`生成一个对应的代理对象`。在代理对象当中就会对目标对象当中的`原始方法`进行`功能的增强`。

> SpringAOP 旨在`管理bean对象`的过程中，主要通过`底层的动态代理`机制，对特定的方法进行编程 。

### 进阶

#### 通知类型

| **Spring AOP 通知类型** |                                                              |
| ----------------------- | ------------------------------------------------------------ |
| `@Around`               | 环绕通知，此注解标注的通知方法在目标方法`前、后`都被执行     |
| `@Before`               | 前置通知，此注解标注的通知方法在目标方法`前`被执行           |
| `@After`                | 后置通知，此注解标注的通知方法在目标方法`后`被执行，无论`是否有异常`都会执行 |
| `@AfterReturning`       | `返回后`通知，此注解标注的通知方法在目标方法`后`被执行，`有异常不会执行` |
| `@AfterThrowing`        | `异常后`通知，此注解标注的通知方法`发生异常后`执行           |

程序发生异常的情况下：

- `@AfterReturning`标识的通知方法`不会执行`，`@AfterThrowing`标识的通知方法执行了
- `@Around`环绕通知中原始方法调用时`有异常`，通知中的环绕后的代码逻辑也`不会在执行`了 （因为原始方法调用已经出异常了）

> 在使用通知时的`注意事项`：
>
> - `@Around`环绕通知需要`自己调用 ``ProceedingJoinPoint.proceed()` 来`让原始方法执行`，其他通知不需要考虑目标方法执行
> - `@Around`环绕通知方法的`返回值`，必须指定为`Object`，来接收原始方法的返回值，否则原始方法执行完毕，是获取不到返回值的。

##### `@PointCut`

- 作用是将公共的切入点表达式抽取出来，需要用到时引用该切入点表达式即可。

- ```java
  //切入点方法（公共的切入点表达式）
  @Pointcut("execution(* com.itheima.service.*.*(..))")
  ```

#### 通知顺序

1. 在不同切面类中，默认按照切面类的类名字母排序：
   - 目标方法`前`的通知方法：`字母`排名靠`前`的先执行
   - 目标方法`后`的通知方法：`字母`排名靠`前`的后执行
2. 如果我们想控制通知的执行顺序有两种方式：
   1. 修改切面类的类名（这种方式非常繁琐、而且不便管理）
   2. 使用Spring提供的`@Order`注解
      1. `@Order(2) `
      2. `@Order(3) `
      3. 前置通知：数字越小先执行; 后置通知：数字越小越后执行

#### 切入点表达式

切入点表达式：`描述切入点方法`的一种表达式

- 作用：主要用来`决定项目中`的哪些方法需要`加入通知`

- 常见形式：

  - `execution(……)`：根据方法的签名来匹配

    - ```java
      execution(访问修饰符?  返回值  包名.类名.?方法名(方法参数) throws 异常?)
      ```

    - 其中带`?`的表示可以省略的部分

      - 访问修饰符：可省略（比如: public、protected）
      - 包名.类名： 可省略
      - throws 异常：可省略（注意是方法上声明抛出的异常，不是实际抛出的异常）

    - 样例

      ```java
      @Before("execution(void com.itheima.service.impl.DeptServiceImpl.delete(java.lang.Integer))")
      ```

    - 可以使用`通配符`描述切入点

      - `*` ：单个独立的任意符号，可以通配任意返回值、包名、类名、方法名、任意类型的一个参数，也可以通配包、类、方法名的一部分
      - `..` ：多个连续的任意符号，可以通配任意层级的包，或任意类型、任意个数的参数

    - 切入点表达式的语法规则：

      1. 方法的访问修饰符可以省略
      2. 返回值可以使用`*`号代替（任意返回值类型）
      3. 包名可以使用`*`号代替，代表任意包（一层包使用一个`*`）
      4. 使用`..`配置包名，标识此包以及此包下的所有子包
      5. 类名可以使用`*`号代替，标识任意类
      6. 方法名可以使用`*`号代替，表示任意方法
      7. 可以使用 `*`  配置参数，一个任意类型的参数
      8. 可以使用`..` 配置参数，任意个任意类型的参数

    - **注意事项：**

      - 根据业务需要，可以使用 且（&&）、或（||）、非（!） 来组合比较复杂的切入点表达式。

    - **切入点表达式书写建议：**

      1. 所有业务方法名在命名时尽量规范，方便切入点表达式快速匹配。如：findXxx，updateXxx。
      2. 描述切入点方法通常基于接口描述，而不是直接描述实现类，增强拓展性。
      3. 在满足业务需要的前提下，尽量缩小切入点的匹配范围。如：包名尽量不使用..，使用 `*` 匹配单个包。

  - `@annotation(……)` ：根据注解匹配

    - 基于注解的方式来匹配切入点方法。这种方式虽然多一步操作，我们需要自定义一个注解，但是相对来比较灵活。我们需要匹配哪个方法，就在方法上加上对应的注解就可以了

### ThreadLocal

- ThreadLocal `并不是`一个`Thread`，而是Thread的`局部变量`。
- ThreadLocal为`每个线程`提供一份`单独`的`存储空间`，具有`线程隔离`的效果，不同的线程之间`不会相互干扰`。

![threadLocal1](D:\refines\refines\threadLocal1.png)

- 常见方法：
  - `public void set(T value)`` `  设置当前线程的线程局部变量的值
  - `public T get()`` `                    返回当前线程所对应的线程局部变量的值
  - `public void remove()`` `         移除当前线程的线程局部变量

![threadLocal2](D:\refines\refines\threadLocal2.png)
