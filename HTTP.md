
-  GET：获得数据
- POST：创建数据

#  请求

![image-20240427160419595](C:\Users\30703\AppData\Roaming\Typora\typora-user-images\image-20240427160419595.png)

- user-agent：何种客户端发送请求
- accept：要响应的数据是什么类型，`*/*`表示接受任意信号

![image-20240427160706532](C:\Users\30703\AppData\Roaming\Typora\typora-user-images\image-20240427160706532.png)

- 请求体中放客户端要传给服务器的其他任意数据，但GET请求的请求体一般是空的
- GET请求一般是请求参数

# 响应

![image-20240427160829515](C:\Users\30703\AppData\Roaming\Typora\typora-user-images\image-20240427160829515.png)

- 状态行：协议版本，状态码，状态消息（常见的状态码如下）

- ![image-20240427160947314](C:\Users\30703\AppData\Roaming\Typora\typora-user-images\image-20240427160947314.png)

- 响应头：生成响应的时间和日期，返回内容的类型及编码格式![image-20240427161245135](C:\Users\30703\AppData\Roaming\Typora\typora-user-images\image-20240427161245135.png)

- 状态码418：回应爬虫


![image-20240822083641813](C:\Users\30703\AppData\Roaming\Typora\typora-user-images\image-20240822083641813.png)

## 2025年4月24日

- 概念：`Hyper Text Transfer Protocol`，超文本传输协议，规定了浏览器和服务器之间数据传输的规则。

- 特点：
  1. 基于TCP协议：面向连接，安全
  2. 基于请求-响应模型的：一次请求对应一次响应
  3. HTTP协议是`无状态`的协议：对于事务处理没有记忆能力。每次请求-响应都是独立的。
     - 缺点：多次请求间`不能共享数据`。
     - 优点：速度快

### http请求协议

#### 请求数据格式

1. 请求行

   1. 请求方式
   2. 资源路径
   3. 协议

2. 请求头

   1. 格式key:value
      ![image-20250424202221031](C:\Users\30703\AppData\Roaming\Typora\typora-user-images\image-20250424202221031.png)

3. 请求体

   1. 与请求头有一行空行
   2. 只有POST有请求体

   > 请求方式-GET：请求参数在请求行中，没有请求体，如：/brand/findALL?name=OPPO&status=1。GET请求大小在浏览器中是有限制的。
   > 请求方式-POST：请求参数在请求体中，POST请求大小是没有限制的。

#### 请求数据获取

- Web服务器（Tomcat)对HTTP协议的请求数据进行解析，并进行了封装(`HttpServletRequest`），在调用Controlle方法的时候传递给了该方法。这样，就使得程序员不必直接对协议进行操作，让Web开发更加便捷。

### http响应协议

#### 响应数据格式

1. 响应行
   1. 协议
   2. 状态码
   3. 描述
2. 响应头
   1. key，value
3. 响应体
   1. 存放响应数据

![image-20250424204107396](C:\Users\30703\AppData\Roaming\Typora\typora-user-images\image-20250424204107396.png)

![image-20250424204114752](C:\Users\30703\AppData\Roaming\Typora\typora-user-images\image-20250424204114752.png)

![image-20250424204451608](C:\Users\30703\AppData\Roaming\Typora\typora-user-images\image-20250424204451608.png)

#### 响应数据设置

